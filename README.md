# Seismic

Seismic is the global leader in enablement, helping organizations engage customers, enable teams, and ignite revenue growth. The Seismic platform provides content management, learning and coaching, dynamic document generation, and buyer engagement capabilities through a comprehensive suite of APIs.

**URL:** [https://seismic.com](https://seismic.com)

## Timestamps

- **Created:** 2025-02-10
- **Modified:** 2026-05-02

## APIs

### Seismic Content API

API for managing and accessing content within the Seismic platform, including documents, presentations, folders, and other sales materials. Supports uploading, organizing, searching, delivering, and managing content items.

**Human URL:** [https://seismic.com/products/content-management/](https://seismic.com/products/content-management/)

#### Tags

- Content, Content Management, Documents, Sales Enablement

#### Properties

- [Documentation](https://developer.seismic.com/seismicsoftware/reference/content-api)
- [OpenAPI](openapi/seismic-content-openapi.yml)
- [Authentication](https://developer.seismic.com/seismicsoftware/docs/authentication)
- [JSONSchema - Content Item](json-schema/seismic-content-item-schema.json)
- [JSONSchema - Folder](json-schema/seismic-folder-schema.json)
- [JSONStructure - Content Item](json-structure/seismic-content-item-structure.json)

---

### Seismic LiveDocs API

API for creating and managing LiveDocs, Seismic's dynamic document generation solution. Enables automated creation of personalized proposals, presentations, and sales materials by merging CRM and other data into templates.

**Human URL:** [https://seismic.com/products/livedocs/](https://seismic.com/products/livedocs/)

#### Tags

- Document Generation, Dynamic Content, LiveDocs, Sales Enablement

#### Properties

- [Documentation](https://developer.seismic.com/seismicsoftware/reference/livedocs-api)
- [OpenAPI](openapi/seismic-livedocs-openapi.yml)
- [JSONSchema - LiveDoc Template](json-schema/seismic-livedoc-template-schema.json)

---

### Seismic Analytics API

API for accessing analytics and reporting data on content usage, user engagement, and sales effectiveness. Provides insights into content performance, user adoption, buyer engagement, and exportable reports.

**Human URL:** [https://seismic.com/products/analytics/](https://seismic.com/products/analytics/)

#### Tags

- Analytics, Insights, Metrics, Reporting

#### Properties

- [Documentation](https://developer.seismic.com/seismicsoftware/reference/analytics-api)
- [OpenAPI](openapi/seismic-analytics-openapi.yml)

---

### Seismic User Management API

API for managing users, groups, roles, teams, and permissions within the Seismic platform. Supports creating and organizing users, managing group hierarchies, assigning roles, and team structures for access control.

**Human URL:** [https://seismic.com](https://seismic.com)

#### Tags

- Administration, Groups, Permissions, Users

#### Properties

- [Documentation](https://developer.seismic.com/seismicsoftware/reference/user-management-api)
- [OpenAPI](openapi/seismic-user-management-openapi.yml)
- [JSONSchema - User](json-schema/seismic-user-schema.json)
- [JSONSchema - Group](json-schema/seismic-group-schema.json)

---

## Common Resources

| Resource | URL |
|---|---|
| Developer Portal | [https://developer.seismic.com/](https://developer.seismic.com/) |
| Getting Started | [https://developer.seismic.com/seismicsoftware/docs/getting-started](https://developer.seismic.com/seismicsoftware/docs/getting-started) |
| Authentication | [https://developer.seismic.com/seismicsoftware/docs/authentication](https://developer.seismic.com/seismicsoftware/docs/authentication) |
| Rate Limits | [https://developer.seismic.com/seismicsoftware/docs/rate-limits](https://developer.seismic.com/seismicsoftware/docs/rate-limits) |
| Webhooks | [https://developer.seismic.com/seismicsoftware/docs/webhooks](https://developer.seismic.com/seismicsoftware/docs/webhooks) |
| Status | [https://status.seismic.com/](https://status.seismic.com/) |
| Change Log | [https://developer.seismic.com/seismicsoftware/changelog](https://developer.seismic.com/seismicsoftware/changelog) |
| Blog | [https://seismic.com/resources/blog/](https://seismic.com/resources/blog/) |

## Artifacts

### OpenAPI Specifications

| API | File |
|---|---|
| Seismic Content API | [openapi/seismic-content-openapi.yml](openapi/seismic-content-openapi.yml) |
| Seismic LiveDocs API | [openapi/seismic-livedocs-openapi.yml](openapi/seismic-livedocs-openapi.yml) |
| Seismic Analytics API | [openapi/seismic-analytics-openapi.yml](openapi/seismic-analytics-openapi.yml) |
| Seismic User Management API | [openapi/seismic-user-management-openapi.yml](openapi/seismic-user-management-openapi.yml) |

### JSON Schemas

| Schema | File |
|---|---|
| Content Item | [json-schema/seismic-content-item-schema.json](json-schema/seismic-content-item-schema.json) |
| Folder | [json-schema/seismic-folder-schema.json](json-schema/seismic-folder-schema.json) |
| LiveDoc Template | [json-schema/seismic-livedoc-template-schema.json](json-schema/seismic-livedoc-template-schema.json) |
| User | [json-schema/seismic-user-schema.json](json-schema/seismic-user-schema.json) |
| Group | [json-schema/seismic-group-schema.json](json-schema/seismic-group-schema.json) |

### JSON Structures

| Structure | File |
|---|---|
| Content Item | [json-structure/seismic-content-item-structure.json](json-structure/seismic-content-item-structure.json) |

### Rules

| Ruleset | File |
|---|---|
| Seismic API Rules | [rules/seismic-rules.yml](rules/seismic-rules.yml) |

### Capabilities

#### Workflow Capabilities

| Workflow | Description | File |
|---|---|---|
| Content Management | Content management and analytics workflow for content teams | [capabilities/content-management.yaml](capabilities/content-management.yaml) |
| Sales Enablement | Full sales enablement workflow combining content, LiveDocs, analytics, and user management | [capabilities/sales-enablement.yaml](capabilities/sales-enablement.yaml) |

#### Shared Per-API Definitions

| API | File |
|---|---|
| Content API | [capabilities/shared/content-api.yaml](capabilities/shared/content-api.yaml) |
| Analytics API | [capabilities/shared/analytics-api.yaml](capabilities/shared/analytics-api.yaml) |
| LiveDocs API | [capabilities/shared/livedocs-api.yaml](capabilities/shared/livedocs-api.yaml) |
| User Management API | [capabilities/shared/user-management-api.yaml](capabilities/shared/user-management-api.yaml) |

### JSON-LD Context

- [json-ld/seismic-context.jsonld](json-ld/seismic-context.jsonld)

### Examples

| Example | File |
|---|---|
| List Content Items | [examples/seismic-list-content-items-example.json](examples/seismic-list-content-items-example.json) |
| Generate LiveDoc | [examples/seismic-generate-livedoc-example.json](examples/seismic-generate-livedoc-example.json) |

### Vocabulary

- [vocabulary/seismic-vocabulary.yml](vocabulary/seismic-vocabulary.yml)

## Maintainers

- **Kin Lane** — [kin@apievangelist.com](mailto:kin@apievangelist.com)
