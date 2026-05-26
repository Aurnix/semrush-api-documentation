# Map Rank Tracker — GetKeywordStatuses

Returns keyword-related status information for a specific Map Rank Tracker campaign.

Does not consume API units. Requires a Bearer Token.

## Endpoint

```
GET https://api.semrush.com/apis/v4/map-rank-tracker/v0/campaigns/:campaignId/keywords
```

## Path Parameters

| Parameter | Required | Type | Description |
|---|---|---|---|
| `campaignId` | Yes | string | Campaign UUID. |

## Query Parameters

| Parameter | Required | Type | Description |
|---|---|---|---|
| `reportDate` | No | string | ISO-8601 timestamp. Date for which the heatmap report was generated. Defaults to the latest report date. |

## Response Fields

| Field | Type | Description |
|---|---|---|
| `keywords` | array | List of keyword entries. |
| `keywords[].keyword` | object | `{ id, name }`. |
| `keywords[].status` | string | E.g. `"COLLECTED"`. |

## Example Request

```
curl --request GET \
  --url https://api.semrush.com/apis/v4/map-rank-tracker/v0/campaigns/382738af-b6ae-4002-b6f6-c4c907b2b024/keywords \
  --header 'Authorization: Bearer ${YOUR_TOKEN}'
```

## Example Response

```json
{
  "meta": {
    "success": true,
    "status_code": 200,
    "request_id": "api-flb-15461ce898e002da1d75017f591d2bd3"
  },
  "data": {
    "keywords": [
      {
        "keyword": {
          "id": "95ed-b433-4395-82cb-4146211",
          "name": "cold beer"
        },
        "status": "COLLECTED"
      }
    ]
  }
}
```

## See Also

- [GetCampaign](local_map_rank_campaign_get.md)
- [GetHeatmap](local_map_rank_heatmap.md)
- [Map Rank Tracker Overview](local_map_rank_overview.md)
