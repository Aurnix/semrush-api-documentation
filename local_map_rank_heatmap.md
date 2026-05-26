# Map Rank Tracker — GetHeatmap

Returns the heatmap report for a Map Rank Tracker campaign and keyword on a specific date — the position at each tracking point and the diff vs. the previous report.

Does not consume API units. Requires a Bearer Token.

## Endpoint

```
GET https://api.semrush.com/apis/v4/map-rank-tracker/v0/campaigns/:campaignId/heatmap
```

## Path Parameters

| Parameter | Required | Type | Description |
|---|---|---|---|
| `campaignId` | Yes | string | Campaign UUID. |

## Query Parameters

| Parameter | Required | Type | Description |
|---|---|---|---|
| `keywordId` | Yes | string | Keyword UUID. |
| `cid` | Conditional | string | Business ID. Either `cid` or `placeIds` must be specified. |
| `placeIds` | Conditional | string | Comma-separated Google Place IDs. Either `cid` or `placeIds` must be specified. |
| `reportDate` | Yes | string | ISO-8601 timestamp. Date for which the heatmap report was generated. |

## Response Fields

| Field | Type | Description |
|---|---|---|
| `keyword` | object | `{ id, name }`. |
| `date` | string | Report timestamp. |
| `positions` | array | Per-point rankings. |
| `positions[].point` | object | `{ id, coordinates: { lat, lng } }`. |
| `positions[].position` | integer | Ranking at this point. |
| `positions[].diff` | integer | Position change vs. the previous report. |

## Example Request

```
curl --request GET \
  --url 'https://api.semrush.com/apis/v4/map-rank-tracker/v0/campaigns/382738af-b6ae-4002-b6f6-c4c907b2b024/heatmap?keywordId=319565ed-b433-4195-82cb-4146253d3311&reportDate=2024-07-05T12%3A39%3A22.611Z&cid=7947215078713107333&placeIds=ChIJD61nCjmD4BQRhaNSCAIuSm4' \
  --header 'Authorization: Bearer ${YOUR_TOKEN}'
```

## Example Response

```json
{
  "meta": {
    "success": true,
    "status_code": 200,
    "request_id": "api-flb-b26b3089b265a968f0158aaaacd16"
  },
  "data": {
    "keyword": {
      "id": "319565ed-b433-4195-82cb-4146253d3311",
      "name": "travel agency"
    },
    "date": "2024-07-05T12:39:22.611Z",
    "positions": [
      {
        "point": {
          "id": "95782b87-d0bc-4ea4-a61b-4355a48b6ba2",
          "coordinates": { "lat": 34.901978091462624, "lng": 33.64292406980698 }
        },
        "position": 1,
        "diff": 1
      },
      {
        "point": {
          "id": "186af327-0b8a-4eea-ba57-62779e510a21",
          "coordinates": { "lat": 34.89748197591122, "lng": 33.631958499999996 }
        },
        "position": 1,
        "diff": 0
      }
    ]
  }
}
```

## See Also

- [GetMetrics](local_map_rank_metrics.md)
- [GetTopCompetitors](local_map_rank_top_competitors.md)
- [GetKeywordStatuses](local_map_rank_keyword_statuses.md)
- [Map Rank Tracker Overview](local_map_rank_overview.md)
