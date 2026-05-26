# Map Rank Tracker — GetCampaign

Returns detailed information about a specific Map Rank Tracker campaign.

Does not consume API units. Requires a Bearer Token.

## Endpoint

```
GET https://api.semrush.com/apis/v4/map-rank-tracker/v0/campaigns/:campaignId
```

## Path Parameters

| Parameter | Required | Type | Description |
|---|---|---|---|
| `campaignId` | Yes | string | Campaign UUID. |

## Response

Returns the full [Campaign object](local_map_rank_overview.md#campaign-schema-response).

## Example Request

```
curl --request GET \
  --url https://api.semrush.com/apis/v4/map-rank-tracker/v0/campaigns/382138af-b6ae-4002-b2f6-c4c907b2b024 \
  --header 'Authorization: Bearer ${YOUR_TOKEN}'
```

## Example Response

```json
{
  "meta": {
    "success": true,
    "status_code": 200,
    "request_id": "api-flb-1a921e710f506c746ad1c1339602b02c"
  },
  "data": {
    "id": "382238af-b6ae-4002-b6f6-c4c917b2b324",
    "userId": "20681378",
    "collectingFrequency": {
      "frequency": "WEEKLY",
      "positions": [1],
      "enable": true
    },
    "keywords": [
      { "id": "319563ed-b433-4135-82cb-4146253d2311", "name": "cold beer" }
    ],
    "gridSettings": {
      "template": "7x7",
      "unit": "KM",
      "distance": 1.5,
      "basePoint": { "lat": 34.9109718, "lng": 33.631958499999996 }
    },
    "lastReportDate": "2024-07-05T12:39:22.611Z",
    "nextReportDate": "2024-08-19T00:00:00Z",
    "reportDates": [
      "2024-07-05T12:39:22.611Z",
      "2024-06-13T14:20:10.660Z",
      "2024-05-15T15:06:32.141Z"
    ],
    "points": [
      {
        "id": "e344df69-03ef-43ed-993f-03d77eeb11db",
        "index": 1,
        "isEnabled": true,
        "coordinates": { "lat": 34.91546840802959, "lng": 33.631958499999996 }
      },
      {
        "id": "67a2253d-e9b0-4a9e-adaf-f2f35f1f7f94",
        "index": 2,
        "isEnabled": true,
        "coordinates": { "lat": 34.91996390757428, "lng": 33.64841045860617 }
      }
    ],
    "countryCode": "CY",
    "business": {
      "cid": "7942215073713207343",
      "placeIds": ["ChIJD61nCjmD4BQRhaNSCAIuSm4"],
      "name": "Pavlos souvlaki",
      "address": "Agias Faneromenis 135A, Larnaca 6025, Cyprus",
      "rating": 4.9,
      "reviewNumber": 220,
      "coordinates": { "lat": 34.9109718, "lng": 33.631958499999996 }
    },
    "createdAt": "2024-05-15T15:06:32.148255Z",
    "status": "COLLECTED",
    "statusUpdatedAt": "2024-08-12T11:32:13.130553Z",
    "name": "Pavlos souvlaki"
  }
}
```

## See Also

- [GetCampaigns](local_map_rank_campaigns_list.md)
- [GetKeywordStatuses](local_map_rank_keyword_statuses.md)
- [GetHeatmap](local_map_rank_heatmap.md)
- [Map Rank Tracker Overview](local_map_rank_overview.md)
