# Map Rank Tracker — GetUserLimits

Returns the current usage and available limits for Map Rank Tracker campaigns and credits on the user's account.

Map Rank Tracker credits power data collection and reset to the plan maximum on the first day of each month. Unused credits do not roll over.

Does not consume API units. Requires a Bearer Token.

## Endpoint

```
GET https://api.semrush.com/apis/v4/map-rank-tracker/v0/limits
```

## Response Fields

| Field | Type | Description |
|---|---|---|
| `campaigns` | object | Campaign slot usage. |
| `campaigns.total` | integer | Maximum campaign slots on the account. |
| `campaigns.inUse` | integer | Campaigns currently created. |
| `campaigns.available` | integer | Remaining campaign slots. |
| `credits` | object | Map Rank Tracker credit usage. |
| `credits.total` | integer | Monthly credit allowance. |
| `credits.spentThisMonth` | integer | Credits spent this month. |
| `credits.available` | integer | Remaining credits this month. |

## Example Request

```
curl --request GET \
  --url https://api.semrush.com/apis/v4/map-rank-tracker/v0/limits \
  --header 'Authorization: Bearer ${YOUR_TOKEN}'
```

## Example Response

```json
{
  "meta": {
    "success": true,
    "status_code": 200,
    "request_id": "aed59894cb5631f3889bdcdfd54833ff"
  },
  "data": {
    "campaigns": {
      "available": 10007,
      "inUse": 3,
      "total": 10010
    },
    "credits": {
      "available": 23908,
      "spentThisMonth": 417,
      "total": 24325
    }
  }
}
```

## See Also

- [CollectCampaign](local_map_rank_collect.md)
- [CreateCampaign](local_map_rank_campaign_create.md)
- [Map Rank Tracker Overview](local_map_rank_overview.md)
