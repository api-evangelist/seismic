---
name: seismic-pull-analytics
description: Pull Seismic content, delivery and user engagement analytics, and export a report without tripping the rate limiter.
api: Seismic Analytics and Reports APIs
base_url: https://api.seismic.com/integration/v2
operations:
  - getContentAnalytics
  - getContentItemAnalytics
  - getTopContent
  - getDeliveryAnalytics
  - getUserAnalytics
  - getUserActivityAnalytics
  - listReports
  - getReport
  - exportReport
scopes:
  - seismic.reporting
---

# Pull Seismic analytics

## Before you start

This skill is read-only apart from `exportReport`, which starts a job. Analytics entities key on the
id of the object they describe (`contentId`, `userId`, `deliveryId`), not on an id of their own —
you cannot address an analytics record independently.

## Steps

1. **Start broad.** `getTopContent` (`GET /analytics/content/top`) or `getContentAnalytics`
   (`GET /analytics/content`) for the period. `ContentAnalytics` carries `views`, `uniqueViews`,
   `downloads`, `shares`, `engagementScore`, `averageViewDuration`, `completionRate`.
2. **Drill in.** `getContentItemAnalytics` (`GET /analytics/content/{contentId}`) returns
   `ContentAnalyticsDetail` with a `summary`, a `timeSeries` and a `viewerBreakdown`. Resolve
   `contentId` against `getContentItem` when you need the item's name and folder.
3. **Buyer side.** `getDeliveryAnalytics` (`GET /analytics/deliveries`) joins content to recipients:
   `senderUserId`, `recipientEmail`, `opened`, `viewCount`, `completionRate`.
4. **Adoption side.** `getUserAnalytics` (`GET /analytics/users`) and `getUserActivityAnalytics`
   (`GET /analytics/users/{userId}`) for `loginCount`, `contentViewed`, `adoptionScore`.
5. **Export.** `listReports` (`GET /analytics/reports`), then `getReport`
   (`GET /analytics/reports/{reportId}`) for `ReportData` (`columns`, `rows`, `totalRows`), or
   `exportReport` (`POST /analytics/reports/{reportId}/export`), which returns `202` — an
   asynchronous job, not a file.

## Handling PII

`getDeliveryAnalytics` returns `recipientEmail` and `getUserAnalytics` returns user emails. Treat
both as personal data: do not write them into logs, summaries or downstream prompts that leave the
tenant boundary.

## Rate limits

All Tier 3 (600 calls per 60 seconds per tenant). A per-content-item drill-down loop across a large
library is what exhausts this; page with `offset`/`limit` and prefer the aggregate endpoints over
N+1 detail calls. On `429`, the seconds to wait are in the message body, not in a `Retry-After`
header.
