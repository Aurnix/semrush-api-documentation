# Map Rank Tracker API — Overview

The Map Rank Tracker API exposes campaign, keyword, heatmap, metric, competitor, and limit data for Map Rank Tracker. For authorization, response envelope, status codes, and error formats see the [Local API overview](local_api_overview.md).

## Base URL

```
https://api.semrush.com/apis/v4/map-rank-tracker/v0/
```

All requests require a Bearer Token:

```
Authorization: Bearer YOUR_TOKEN
```

## Costs

Methods do not consume API units. `CollectCampaign` consumes **Map Rank Tracker credits** equal to *grid points × keywords* in the campaign. Credits reset to the plan limit on the first day of each month and do not roll over.

## Endpoints

**Read**
- [GetCampaign](local_map_rank_campaign_get.md) — `GET /campaigns/:campaignId`
- [GetCampaigns](local_map_rank_campaigns_list.md) — `GET /campaigns`
- [GetKeywordStatuses](local_map_rank_keyword_statuses.md) — `GET /campaigns/:campaignId/keywords`
- [GetHeatmap](local_map_rank_heatmap.md) — `GET /campaigns/:campaignId/heatmap`
- [GetMetrics](local_map_rank_metrics.md) — `GET /campaigns/:campaignId/metrics`
- [GetTopCompetitors](local_map_rank_top_competitors.md) — `GET /campaigns/:campaignId/top-competitors`
- [GetUserLimits](local_map_rank_limits.md) — `GET /limits`

**Write**
- [CreateCampaign](local_map_rank_campaign_create.md) — `POST /campaigns`
- [UpdateCampaign](local_map_rank_campaign_update.md) — `PATCH /campaigns/:campaignId`
- [DeleteCampaign](local_map_rank_campaign_delete.md) — `DELETE /campaigns/:campaignId`
- [CollectCampaign](local_map_rank_collect.md) — `PUT /campaigns/:campaignId/collect`

## Tracking Area Configuration

A campaign's tracking area is defined by either a grid (`gridSettings`) or an explicit list of points (`points`). The two fields are **mutually exclusive**.

On [CreateCampaign](local_map_rank_campaign_create.md):

1. **Fully automatic (default)** — omit both. The system generates a `5x5` grid with a 1.5 km radius centered on the business location.
2. **Custom grid** — provide `gridSettings`. The system generates tracking points from your center, distance, and template.
3. **Custom points** — provide `points`. The exact coordinates are used directly.

On [UpdateCampaign](local_map_rank_campaign_update.md):

- Provide a new `gridSettings` to recalculate the grid.
- Provide a new `points` list to override existing coordinates.
- Provide neither to leave the tracking area unchanged.

### `gridSettings`

| Field | Type | Description |
|---|---|---|
| `template` | string | Grid density, e.g. `"5x5"`, `"7x7"`. |
| `unit` | string | Distance unit, e.g. `"KM"`, `"MI"`. |
| `distance` | float | Radius from `basePoint` in `unit`. |
| `basePoint` | object | `{ lat, lng }` center coordinate. |

### `points`

Array of:

| Field | Type | Description |
|---|---|---|
| `id` | string | Server-assigned point ID (response only). |
| `index` | integer | Ordinal index in the grid. |
| `isEnabled` | boolean | Whether the point is tracked. |
| `coordinates` | object | `{ lat, lng }`. |

## Shared Objects

### `business`

| Field | Type | Description |
|---|---|---|
| `cid` | string | Business ID. |
| `placeIds` | array[string] | Google Place IDs associated with the business. |
| `name` | string | Business name. |
| `address` | string | Display address. |
| `rating` | float | Average rating. |
| `reviewNumber` | integer | Number of reviews. |
| `coordinates` | object | `{ lat, lng }`. |

### `collectingFrequency`

| Field | Type | Description |
|---|---|---|
| `frequency` | string | `WEEKLY`, `MONTHLY`, etc. |
| `interval` | integer | Number of `frequency` units between collections. |
| `positions` | array[integer] | Slot indices within the period (e.g. day-of-week for WEEKLY, day-of-month for MONTHLY). |
| `time` | string | `HH:mm` collection time. |
| `enable` | boolean | Whether automatic collection is active. Omit the whole object for manual-only collection. |

### `keywords`

Array of `{ id, name }`. Max 100 keywords per campaign; max 255 chars per keyword.

### `sharingStatus`

| Field | Type | Description |
|---|---|---|
| `accessType` | string | E.g. `"OWNER"`. |
| `ownerEmail` | string | Campaign owner. |
| `sharesCount` | integer | Number of users sharing access. |

## Campaign Schema (response)

| Field | Type | Description |
|---|---|---|
| `id` | string | Campaign UUID. |
| `userId` | string | Owner user ID. |
| `name` | string | Custom campaign name (defaults to business name). |
| `sharingStatus` | object | See above. |
| `collectingFrequency` | object | See above. Present when automatic collection is configured. |
| `keywords` | array | `[{ id, name }]`. |
| `gridSettings` | object | Grid configuration (if used). |
| `points` | array | Tracking points. |
| `countryCode` | string | ISO 3166-1 alpha-2. |
| `business` | object | See above. |
| `lastReportDate` | string | ISO-8601 timestamp of the most recent report. |
| `nextReportDate` | string | ISO-8601 timestamp of the next scheduled report. |
| `reportDates` | array[string] | All report timestamps. |
| `createdAt` | string | ISO-8601 creation timestamp. |
| `status` | string | E.g. `"CREATED"`, `"COLLECTED"`. |
| `statusUpdatedAt` | string | ISO-8601 timestamp when the status last changed. |
| `projectMetrics` | object | Aggregate metrics, e.g. `averagePosition`, `averagePositionDiff`, `averageShareOfVoice`, `averageShareOfVoiceDiff`. Present when reports have been collected. |
