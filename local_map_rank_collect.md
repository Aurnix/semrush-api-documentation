# Map Rank Tracker — CollectCampaign

Triggers a data collection for a Map Rank Tracker campaign. Consumes Map Rank Tracker **credits** equal to `grid points × keywords` in the campaign. Does not consume API units. Requires a Bearer Token.

## Endpoint

```
PUT https://api.semrush.com/apis/v4/map-rank-tracker/v0/campaigns/:campaignId/collect
```

## Path Parameters

| Parameter | Required | Type | Description |
|---|---|---|---|
| `campaignId` | Yes | string | Campaign UUID. |

## Query Parameters

| Parameter | Required | Type | Description |
|---|---|---|---|
| `reportDate` | No | string | ISO-8601 timestamp to associate with this report. Defaults to current server time. |

## Response Fields

| Field | Type | Description |
|---|---|---|
| `collectingReportDate` | string | Scheduled timestamp for the data collection (ISO-8601). |

## Example Request

```
curl --request PUT \
  --url 'https://api.semrush.com/apis/v4/map-rank-tracker/v0/campaigns/0410f1d2-2bdb-4554-a761-0c15d636105b/collect' \
  --header 'Authorization: Bearer ${YOUR_TOKEN}'
```

## Example Response

```json
{
  "meta": {
    "success": true,
    "status_code": 200,
    "request_id": "a1b2c3d4e5f67890"
  },
  "data": {
    "collectingReportDate": "2026-02-25T17:30:00Z"
  }
}
```

## See Also

- [GetUserLimits](local_map_rank_limits.md) — check remaining credits before collecting
- [CreateCampaign](local_map_rank_campaign_create.md)
- [UpdateCampaign](local_map_rank_campaign_update.md)
- [Map Rank Tracker Overview](local_map_rank_overview.md)
