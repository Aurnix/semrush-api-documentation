# Map Rank Tracker — GetCampaigns

Returns a paginated list of Map Rank Tracker campaigns, with optional name/address search.

Does not consume API units. Requires a Bearer Token.

## Endpoint

```
GET https://api.semrush.com/apis/v4/map-rank-tracker/v0/campaigns
```

## Query Parameters

| Parameter | Required | Type | Description |
|---|---|---|---|
| `page` | No | int32 | Page index. Default `0`. |
| `size` | No | int32 | Page size. Default `10`. |
| `sort` | No | string | `field,direction`. Fields: `createdAt`, `businessName`. Directions: `ASC`, `DESC`. Default `createdAt,DESC`. |
| `query` | No | string | Filter campaigns by name or business address. Max 255 chars. |
| `onlyMarkedForRemoval` | No | boolean | When `true`, return only campaigns marked for removal. |

## Response Fields

| Field | Type | Description |
|---|---|---|
| `content` | array | Campaigns on the current page. Each entry uses the same shape as a [Campaign object](local_map_rank_overview.md#campaign-schema-response) with summary fields like `keywordsNumber`, `pointsNumber`, and `projectMetrics`. |
| `pageable` | object | Pagination settings: `pageNumber`, `pageSize`, `sort`, `offset`, `paged`, `unpaged`. |
| `sort` | object | Applied sort: `empty`, `unsorted`, `sorted`. |
| `last` | boolean | Whether this is the last page. |
| `first` | boolean | Whether this is the first page. |
| `numberOfElements` | int32 | Number of items on the current page. |
| `empty` | boolean | Whether the current page is empty. |
| `totalElements` | int32 | Total campaigns available. |
| `totalPages` | int32 | Total pages available. |
| `size` | int32 | Page size. |
| `number` | int32 | Current page index. |

## Example Request

```
curl --request GET \
  --url https://api.semrush.com/apis/v4/map-rank-tracker/v0/campaigns \
  --header 'Authorization: Bearer ${YOUR_TOKEN}'
```

## Example Response

```json
{
  "meta": {
    "success": true,
    "status_code": 200,
    "request_id": "api-flb-c29dd331ef9c45fe6d0786b230109780"
  },
  "data": {
    "content": [
      {
        "id": "5d39173b-9701-4f81-a68f-562833ef089a",
        "userId": "84375",
        "keywordsNumber": 1,
        "pointsNumber": 49,
        "gridSettings": {
          "template": "7x7",
          "unit": "KM",
          "distance": 1.5,
          "basePoint": { "lat": 34.889669399999995, "lng": 33.6368593 }
        },
        "countryCode": "ES",
        "business": {
          "cid": "7376860126281215917",
          "placeIds": ["ChIJJQpxHt4C4BQRrfpTADjfX2Y"],
          "name": "Pablo's paella",
          "address": "Orange str, area 3028, Spain",
          "rating": 4.4,
          "reviewNumber": 790,
          "coordinates": { "lat": 34.889669399999995, "lng": 33.6368593 }
        },
        "projectMetrics": {
          "averagePosition": 16.2,
          "averagePositionDiff": -1.84,
          "averageShareOfVoice": 2.3,
          "averageShareOfVoiceDiff": 0.646
        },
        "name": "Pablo's paella",
        "lastReportDate": "2024-07-11T14:08:01.588Z",
        "status": "COLLECTED",
        "createdAt": "2024-07-11T14:08:01.594769Z"
      },
      {
        "id": "382738af-b6ae-4002-b6f6-c4c907b2b024",
        "userId": "20684375",
        "keywordsNumber": 1,
        "pointsNumber": 49,
        "gridSettings": {
          "template": "7x7",
          "unit": "KM",
          "distance": 1.5,
          "basePoint": { "lat": 34.9109718, "lng": 33.631958499999996 }
        },
        "countryCode": "DE",
        "business": {
          "cid": "7947215078713107333",
          "placeIds": ["ChIJD61nCjmD4BQRhaNSCAIuSm4"],
          "name": "Paul's shnitzel",
          "address": "Orangenstraße 20, Leipzig , Germany",
          "rating": 4.9,
          "reviewNumber": 233,
          "coordinates": { "lat": 34.9109718, "lng": 33.631958499999996 }
        },
        "name": "Paul's shnitzel",
        "lastReportDate": "2024-08-12T11:32:11.515Z",
        "nextReportDate": "2024-08-19T00:00:00Z",
        "status": "COLLECTED",
        "createdAt": "2024-05-15T15:06:32.148255Z"
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
    "last": true,
    "totalPages": 1,
    "totalElements": 2,
    "first": true,
    "size": 10,
    "number": 0,
    "sort": { "empty": false, "unsorted": false, "sorted": true },
    "numberOfElements": 2,
    "empty": false
  }
}
```

## See Also

- [GetCampaign](local_map_rank_campaign_get.md)
- [CreateCampaign](local_map_rank_campaign_create.md)
- [Map Rank Tracker Overview](local_map_rank_overview.md)
