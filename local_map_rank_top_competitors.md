# Map Rank Tracker — GetTopCompetitors

Returns the main business plus a paginated, sortable list of the top competitors for a campaign + keyword on a given date, including each competitor's average position and Share of Voice.

Does not consume API units. Requires a Bearer Token.

## Endpoint

```
GET https://api.semrush.com/apis/v4/map-rank-tracker/v0/campaigns/:campaignId/top-competitors
```

## Path Parameters

| Parameter | Required | Type | Description |
|---|---|---|---|
| `campaignId` | Yes | string | Campaign UUID. |

## Query Parameters

| Parameter | Required | Type | Description |
|---|---|---|---|
| `keywordId` | Yes | string | Keyword UUID. |
| `reportDate` | Yes | string | ISO-8601 timestamp. An incorrect value returns an empty competitor list. |
| `page` | No | int32 | Page index. Default `0`. |
| `size` | No | int32 | Page size. Default `10`. |
| `sort` | No | string | `field,direction`. Fields: `averagePosition`, `name`, `rating`, `reviewNumber`, `shareOfVoice`. Directions: `ASC`, `DESC`. Default `averagePosition,ASC`. |

## Response Fields

| Field | Type | Description |
|---|---|---|
| `business` | object | Main business block. |
| `business.business` | object | Business profile. See [`business`](local_map_rank_overview.md#business). |
| `business.averagePosition` | float | Average position of the main business for the keyword. |
| `business.shareOfVoice` | float | Share of Voice for the main business. |
| `competitors` | object | Paged competitor list. |
| `competitors.content[].business` | object | Competitor profile. |
| `competitors.content[].averagePosition` | float | Competitor average position. |
| `competitors.content[].shareOfVoice` | float | Competitor Share of Voice. |
| `competitors.pageable` / `last` / `first` / `totalPages` / `totalElements` / `size` / `number` / `numberOfElements` / `empty` / `sort` | mixed | Standard Spring-style pagination metadata. |

## Example Request

```
curl --request GET \
  --url 'https://api.semrush.com/apis/v4/map-rank-tracker/v0/campaigns/3218f353-87a9-495c-b5b8-3dcfd9213e20/top-competitors?keywordId=f43b514b-efc2-479b-8207-16707dea070f&reportDate=2024-08-13T15%3A20%3A19.686Z' \
  --header 'Authorization: Bearer ${YOUR_TOKEN}'
```

## Example Response

```json
{
  "meta": {
    "success": true,
    "status_code": 200,
    "request_id": "api-flb-ffd0a79a2b7f83e42c56247f20214e0a"
  },
  "data": {
    "business": {
      "business": {
        "cid": "7376860146281215917",
        "placeIds": ["ChIJJQpxHt2C4BQRrffTADjfX2Y"],
        "name": "Paolo's pizza",
        "address": "Strada arancione 62, Italy",
        "rating": 4.4,
        "reviewNumber": 802,
        "coordinates": { "lat": 34.889669399999995, "lng": 33.6368593 }
      },
      "averagePosition": 10.387755102040817,
      "shareOfVoice": 6.46734693877551
    },
    "competitors": {
      "content": [
        {
          "business": {
            "cid": "17188786011085295626",
            "placeIds": ["ChIJf2r8H92C4BQRClDxls7Viu4"],
            "name": "Paolo's pasta",
            "address": "Strada arancione 63, Italy",
            "rating": 4.3,
            "reviewNumber": 149,
            "coordinates": { "lat": 34.889787, "lng": 33.6371021 }
          },
          "averagePosition": 7.530612244897959,
          "shareOfVoice": 10.670408163265304
        },
        {
          "business": {
            "cid": "17986238257282860575",
            "placeIds": ["ChIJfVkrwBuD4BQRH8biWmb0m_k"],
            "name": "Paolo's calzone",
            "address": "Strada arancione 65, Italy",
            "rating": 4.3,
            "reviewNumber": 55,
            "coordinates": { "lat": 34.8964649, "lng": 33.638536 }
          },
          "averagePosition": 9.040816326530612,
          "shareOfVoice": 8.534693877551021
        }
      ],
      "pageable": {
        "pageNumber": 0,
        "pageSize": 10,
        "sort": { "empty": false, "unsorted": false, "sorted": true },
        "offset": 0,
        "paged": true,
        "unpaged": false
      },
      "last": false,
      "totalPages": 8,
      "totalElements": 76,
      "first": true,
      "size": 10,
      "number": 0,
      "sort": { "empty": false, "unsorted": false, "sorted": true },
      "numberOfElements": 10,
      "empty": false
    }
  }
}
```

## See Also

- [GetHeatmap](local_map_rank_heatmap.md)
- [GetMetrics](local_map_rank_metrics.md)
- [Map Rank Tracker Overview](local_map_rank_overview.md)
