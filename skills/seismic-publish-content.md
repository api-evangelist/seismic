---
name: seismic-publish-content
description: Upload a content item into the right Seismic folder and content profile, set its properties, and share it — including version handling.
api: Seismic Content API
base_url: https://api.seismic.com/integration/v2
operations:
  - listFolders
  - createFolder
  - getFolder
  - listContentProfiles
  - listContentProperties
  - createContentItem
  - getContentItem
  - updateContentItem
  - replaceContentFile
  - listContentVersions
  - downloadContentFile
  - getContentUrl
  - searchContent
  - deleteContentItem
scopes:
  - seismic.library.view
  - seismic.library.manage
  - seismic.delivery
---

# Publish content to Seismic

## Before you start

`createContentItem` has **no idempotency key**. A timed-out create can leave a duplicate that no
API call will detect for you — search by name in the target folder before retrying.

## Steps

1. **Locate or create the folder.** `listFolders` (`GET /folders`); `Folder` is a self-referencing
   tree via `parentId`, and `path` gives the resolved location. If it does not exist, `createFolder`
   (`POST /folders`) with `parentId`.
2. **Pick the content profile.** `listContentProfiles` (`GET /content-profiles`). The profile
   governs `allowedFileTypes` and which properties apply — creating an item with a file type the
   profile forbids is a `400`.
3. **Read the property schema.** `listContentProperties` (`GET /content-properties`).
   `ContentProperty` declares `type`, `required` and `options`; a value outside `options` is a `400`.
4. **Create.** `createContentItem` (`POST /content`) with `name`, `folderId`, `contentProfileId`,
   `tags` and `properties`. Expect `201` with a `ContentItem`.
5. **Update the file, not the item, on revisions.** `replaceContentFile`
   (`PUT /content/{contentId}/file`) creates a new version; `listContentVersions`
   (`GET /content/{contentId}/versions`) shows the history. Do NOT create a second content item for
   a new revision.
6. **Share.** `getContentUrl` (`GET /content/{contentId}/url`) returns the shareable URL;
   `downloadContentFile` (`GET /content/{contentId}/file`) returns the bytes.
7. **Confirm discoverability.** `searchContent` (`POST /search`) against the new item's name.

## Reversal

Replacing a file **is** reversible — prior versions are retained and listable, so re-upload a
retained version to roll back. `deleteContentItem` (`DELETE /content/{contentId}`) is **not**:
Seismic documents no recycle bin, no restore endpoint and no retention window. Delete only on an
explicit instruction, never as cleanup after a failed write.

## Rate limits

Folder and workspace listing operations are **Tier 2 — 60 calls per 60 seconds per tenant**, which
is the limit a crawl-then-upload loop hits first. Everything else here is Tier 3 (600/min).

## Events

`ContentManagerCreateFileV1`, `ContentManagerCreateFileVersionV1`,
`ContentManagerActiveVersionChangedV1`, `ContentManagerDeleteFileV1` and
`ContentManagerUpdateContentCustomPropertyV1` fire as webhooks.
