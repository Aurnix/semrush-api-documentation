# Map Rank Tracker — GetMetrics

Returns time-series average position and Share of Voice metrics for a campaign and keyword.

Does not consume API units. Requires a Bearer Token.

## Endpoint

```
GET https://api.semrush.com/apis/v4/map-rank-tracker/v0/campaigns/:campaignId/metrics
```

## Path Parameters

| Parameter | Required | Type | Description |
|---|---|---|---|
| `campaignId` | Yes | string | Campaign UUID. |

## Query Parameters

| Parameter | Required | Type | Description |
|---|---|---|---|
| `keywordId` | Yes | string | Keyword UUID. An incorrect `keywordId` returns defaults: average position `21`, Share of Voice `0`. |
| `cid` | Conditional | string | Business ID. Either `cid` or `placeIds` must be specified. |
| `placeIds` | Conditional | string | Comma-separated Google Place IDs. Either `cid` or `placeIds` must be specified. |

## Response Fields

| Field | Type | Description |
|---|---|---|
| `average_positions` | map<string, double> | `datetime → average position`. Total of all business rankings divided by the number of data points. Rankings greater than 20 are counted as 21. |
| `share_of_voices` | map<string, double> | `datetime → Share of Voice`. Weighted-rank metric: higher rankings carry more weight (they are seen more often). Represents the business's share of the search market for the keyword. |

## Example Request

```
curl --request GET \
  --url 'https://api.semrush.com/apis/v4/map-rank-tracker/v0/campaigns/382738af-b6ae-4002-b6f6-c4c907b2b024/metrics?keywordId=319565ed-b433-4195-82cb-4146253d3311&cid=7947215078713107333&placeIds=ChIJD61nCjmD4BQRhaNSCAIuSm4' \
  --header 'Authorization: Bearer ${YOUR_TOKEN}'
```

## Example Response

```json
{
  "meta": {
    "success": true,
    "status_code": 200,
    "request_id": "api-flb-89a8f5c1b33de29399bd0d73dac91589"
  },
  "data": {
    "average_positions": {
      "2024-05-15T15:06:32.141Z": 1.5918367346938775,
      "2024-06-13T14:20:10.66Z":  1.7755102040816326,
      "2024-07-05T12:39:22.611Z": 1.3877551020408163
    },
    "share_of_voices": {
      "2024-05-15T15:06:32.141Z": 22.173065551020414,
      "2024-06-13T14:20:10.66Z":  20.35676273469386,
      "2024-07-05T12:39:22.611Z": 23.835469530612244
    }
  }
}
```

## See Also

- [GetHeatmap](local_map_rank_heatmap.md)
- [GetTopCompetitors](local_map_rank_top_competitors.md)
- [Map Rank Tracker Overview](local_map_rank_overview.md)
