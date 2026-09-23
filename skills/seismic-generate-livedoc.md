---
name: seismic-generate-livedoc
description: Generate a Seismic LiveDoc from a template and retrieve the finished document, handling the asynchronous job path correctly.
api: Seismic LiveDocs API
base_url: https://api.seismic.com/integration/v2
operations:
  - listLiveDocTemplates
  - getLiveDocTemplate
  - getLiveDocTemplateInputs
  - previewLiveDocTemplate
  - generateLiveDoc
  - getGenerationJob
  - listGenerationJobs
scopes:
  - seismic.library.view
  - seismic.library.manage
---

# Generate a Seismic LiveDoc

## Before you start

- Get a bearer token from `https://auth.seismic.com/connect/token`. Scope is necessary but not
  sufficient — a tenant administrator must also have granted the permission, so a 403 on a
  correctly-scoped token means "ask the admin", not "get a different token".
- **There is no idempotency key on this API.** `POST /livedocs/generate` is the most expensive
  write in this skill. If the call times out, do NOT blindly retry — poll `listGenerationJobs`
  first and check whether a job for this template already exists.

## Steps

1. **Find the template.** `listLiveDocTemplates` (`GET /livedocs/templates`) returns templates with
   `id`, `outputFormats`, `dataSourceId` and `inputCount`. Use `offset`/`limit` to page.
2. **Read what it needs.** `getLiveDocTemplateInputs`
   (`GET /livedocs/templates/{templateId}/inputs`) returns `TemplateInput` records: `name`, `type`,
   `required`, `defaultValue`, `options`, `dataSourceField`. Every input with `required: true` must
   be supplied. If `dataSourceField` is set, the value comes from the template's data source — call
   `getDataSource` (`GET /livedocs/datasources/{dataSourceId}`) and check `status` and `lastSyncAt`
   before assuming the data is current.
3. **Rehearse.** `previewLiveDocTemplate` (`POST /livedocs/templates/{templateId}/preview`) is the
   only dry-run on this surface. Use it to validate inputs before committing.
4. **Generate.** `generateLiveDoc` (`POST /livedocs/generate`). This returns **either** `200` with a
   `LiveDocResult` **or** `202` with a `GenerationJob`. Branch on the status code — do not assume
   one shape.
5. **Poll if asynchronous.** On `202`, poll `getGenerationJob` (`GET /livedocs/jobs/{jobId}`) and
   read `status` and `progress`. When complete, `result` carries the `LiveDocResult` with
   `downloadUrl`, `contentId` and `folderId`. On failure, `error` carries the reason.
   Alternatively subscribe to the `LiveDocCompletedV2` webhook and stop polling entirely.

## Rate limits

`POST /livedocs/generate` is Seismic's **Tier 1** endpoint: **10 calls per 60 seconds per tenant** —
the tightest limit on the platform. Every other operation in this skill is Tier 3 (600/min).
On `429`, read `X-Seismic-Remaining-Calls` and back off by the number of seconds named in the
message body; there is no `Retry-After` header.

## Reversal

A generation in flight can be cancelled on the LiveDocs Express surface
(`seismiclivedocsexpressbatchcanceljob`). A completed LiveDoc is a content item and can be deleted
with `deleteContentItem`, but Seismic publishes **no restore path and no retention window** for a
deleted content item — treat the delete as permanent.

## Errors

`400` almost always means a missing or mistyped template input. `404` on `getGenerationJob` can mean
the job expired, not only that the id is wrong. See `errors/seismic-problem-types.yml`.
