# Seismic (seismic)

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Seismic is the global leader in enablement, helping organizations engage customers, enable teams, and ignite revenue growth. The Seismic platform provides content management, learning and coaching, dynamic document generation, and buyer engagement capabilities through a comprehensive suite of APIs.

**APIs.json:** [https://seismic.com](https://seismic.com)

## Timestamps

- **Created:** 2025-02-10
- **Modified:** 2026-05-19

## APIs

### Seismic Content API

API for managing and accessing content within the Seismic platform, including documents, presentations, folders, and other sales materials. Supports uploading, organizing, searching, delivering, and managing content items.

- **Human URL:** [https://seismic.com/products/content-management/](https://seismic.com/products/content-management/)
- **Base URL:** `https://api.seismic.com/integration/v2`

#### Tags

- Content
- Content Management
- Documents
- Sales Enablement

#### Properties

- [Documentation](https://developer.seismic.com/seismicsoftware/reference/content-api)
- [OpenAPI](openapi/seismic-content-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/seismic-content.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/seismic-content.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [Authentication](https://developer.seismic.com/seismicsoftware/docs/authentication)
- [JSON Schema](json-schema/seismic-content-item-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Schema](json-schema/seismic-folder-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Structure](json-structure/seismic-content-item-structure.json)

### Seismic LiveDocs API

API for creating and managing LiveDocs, Seismic's dynamic document generation solution. Enables automated creation of personalized proposals, presentations, and sales materials by merging CRM and other data into templates.

- **Human URL:** [https://seismic.com/products/livedocs/](https://seismic.com/products/livedocs/)
- **Base URL:** `https://api.seismic.com/integration/v2`

#### Tags

- Document Generation
- Dynamic Content
- LiveDocs
- Sales Enablement

#### Properties

- [Documentation](https://developer.seismic.com/seismicsoftware/reference/livedocs-api)
- [OpenAPI](openapi/seismic-livedocs-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/seismic-livedocs.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/seismic-livedocs.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [JSON Schema](json-schema/seismic-livedoc-template-schema.json) — [JSON Schema](https://json-schema.org/specification)

### Seismic Analytics API

API for accessing analytics and reporting data on content usage, user engagement, and sales effectiveness. Provides insights into content performance, user adoption, buyer engagement, and exportable reports.

- **Human URL:** [https://seismic.com/products/analytics/](https://seismic.com/products/analytics/)
- **Base URL:** `https://api.seismic.com/integration/v2`

#### Tags

- Analytics
- Insights
- Metrics
- Reporting

#### Properties

- [Documentation](https://developer.seismic.com/seismicsoftware/reference/analytics-api)
- [OpenAPI](openapi/seismic-analytics-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/seismic-analytics.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/seismic-analytics.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Seismic User Management API

API for managing users, groups, roles, teams, and permissions within the Seismic platform. Supports creating and organizing users, managing group hierarchies, assigning roles, and team structures for access control.

- **Human URL:** [https://seismic.com](https://seismic.com)
- **Base URL:** `https://api.seismic.com/integration/v2`

#### Tags

- Administration
- Groups
- Permissions
- Users

#### Properties

- [Documentation](https://developer.seismic.com/seismicsoftware/reference/user-management-api)
- [OpenAPI](openapi/seismic-user-management-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/seismic-user-management.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/seismic-user-management.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [JSON Schema](json-schema/seismic-user-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Schema](json-schema/seismic-group-schema.json) — [JSON Schema](https://json-schema.org/specification)

## Common Properties

- [Arazzo Workflows](arazzo/) — [Arazzo Specification](https://spec.openapis.org/arazzo/latest.html)
- [LinkedIn](https://www.linkedin.com/company/seismic)
- [Portal](https://developer.seismic.com/)
- [Getting Started](https://developer.seismic.com/seismicsoftware/docs/getting-started)
- [Authentication](https://developer.seismic.com/seismicsoftware/docs/authentication)
- [Rate Limits](https://developer.seismic.com/seismicsoftware/docs/rate-limits)
- [Webhooks](https://developer.seismic.com/seismicsoftware/docs/webhooks)
- [Support](https://seismic.com/support/)
- [Privacy Policy](https://seismic.com/privacy-policy/)
- [Terms of Service](https://seismic.com/terms-of-service/)
- [Status Page](https://status.seismic.com/)
- [Documentation](https://developer.seismic.com/seismicsoftware/docs)
- [Changelog](https://developer.seismic.com/seismicsoftware/changelog)
- [Website](https://seismic.com)
- [Blog](https://seismic.com/resources/blog/)
- [Login](https://login.seismic.com/)
- [Spectral Rules](rules/seismic-rules.yml)
- [J S O N L D Context](json-ld/seismic-context.jsonld)
- [Vocabulary](vocabulary/seismic-vocabulary.yml)
- [Integrations](https://www.seismic.com/platform/integrations/)
- [L L Ms Txt](https://developer.seismic.com/llms.txt)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
**URL:** https://apievangelist.com
