# Map Rank Tracker — CreateCampaign

Creates a new Map Rank Tracker campaign to track a business's visibility across a specific geographic area.

Does not consume API units. Requires a Bearer Token.

## Tracking Area Configuration

`gridSettings` and `points` are mutually exclusive. See [Tracking Area Configuration](local_map_rank_overview.md#tracking-area-configuration) for the three create-time modes:

1. **Fully automatic (default)** — omit both. The system generates a `5x5` grid with a 1.5 km radius centered on the business.
2. **Custom grid** — provide `gridSettings`.
3. **Custom points** — provide `points`.

## Endpoint

```
POST https://api.semrush.com/apis/v4/map-rank-tracker/v0/campaigns
```

## Headers

```
Authorization: Bearer YOUR_TOKEN
Content-Type: application/json
```

## Request Body

| Field | Required | Type | Description |
|---|---|---|---|
| `placeId` | Yes | string | Google Place ID of the business to track. Find via [Google's Place ID Finder](https://developers.google.com/maps/documentation/places/web-service/place-id#find-id). |
| `keywords` | Yes | array[string] | 1–100 keywords. Max 255 chars per keyword. |
| `name` | No | string | Custom campaign name. Defaults to the business name. |
| `gridSettings` | No | object | Grid configuration. Cannot be combined with `points`. See [`gridSettings`](local_map_rank_overview.md#gridsettings). |
| `points` | No | array[object] | Custom point list. Cannot be combined with `gridSettings`. See [`points`](local_map_rank_overview.md#points). |
| `collectingFrequency` | No | object | Automatic collection schedule. Omit for manual-only collection. See [`collectingFrequency`](local_map_rank_overview.md#collectingfrequency). |

## Response

Returns the full [Campaign object](local_map_rank_overview.md#campaign-schema-response). Newly created campaigns start in `status="CREATED"`.

## Example Requests

**1. Fully automatic**

```
curl --location --request POST 'https://api.semrush.com/apis/v4/map-rank-tracker/v0/campaigns' \
  --header 'Authorization: Bearer ${YOUR_TOKEN}' \
  --header 'Content-Type: application/json' \
  --data '{
    "placeId": "ChIJ0WHHXq8H9YgRdNsk3gsXmxg",
    "keywords": ["restaurant"]
  }'
```

**2. Custom grid settings**

```
curl --location --request POST 'https://api.semrush.com/apis/v4/map-rank-tracker/v0/campaigns' \
  --header 'Authorization: Bearer ${YOUR_TOKEN}' \
  --header 'Content-Type: application/json' \
  --data '{
    "placeId": "ChIJ0WHHXq8H9YgRdNsk3gsXmxg",
    "collectingFrequency": {
      "frequency": "MONTHLY",
      "interval": 1,
      "positions": [1],
      "time": "10:00",
      "enable": true
    },
    "keywords": ["restaurant"],
    "gridSettings": {
      "template": "5x5",
      "unit": "KM",
      "distance": 1.5,
      "basePoint": { "lat": 33.7744675, "lng": -84.29508709999999 }
    },
    "name": "Demo Campaign"
  }'
```

**3. Custom points**

```
curl --location --request POST 'https://api.semrush.com/apis/v4/map-rank-tracker/v0/campaigns' \
  --header 'Authorization: Bearer ${YOUR_TOKEN}' \
  --header 'Content-Type: application/json' \
  --data '{
    "placeId": "ChIJ0WHHXq8H9YgRdNsk3gsXmxg",
    "collectingFrequency": {
      "frequency": "MONTHLY",
      "interval": 1,
      "positions": [1],
      "time": "10:00",
      "enable": true
    },
    "keywords": ["restaurant"],
    "points": [
      { "index": 0, "isEnabled": true, "coordinates": { "lat": 33.760976614131074, "lng": -84.31131325078074 } },
      { "index": 1, "isEnabled": true, "coordinates": { "lat": 33.760977410466175, "lng": -84.30320017544062 } }
    ],
    "name": "Demo Campaign"
  }'
```

## Example Response

> The `points` list in the original response covers all 25 grid points; truncated here to the first two for brevity.

```json
{
  "meta": {
    "success": true,
    "status_code": 200,
    "request_id": "c543235ce827f0369b0a91a9c20c543b"
  },
  "data": {
    "id": "94896106-e6bd-471b-960b-8d3f2a29b17c",
    "sharingStatus": {
      "accessType": "OWNER",
      "ownerEmail": "user@semrush.com",
      "sharesCount": 0
    },
    "collectingFrequency": {
      "frequency": "MONTHLY",
      "positions": [1],
      "enable": true
    },
    "keywords": [
      { "id": "0a5740f1-4b94-42e1-9c45-0097b8a0f50f", "name": "restaurant" }
    ],
    "gridSettings": {
      "template": "5x5",
      "unit": "KM",
      "distance": 1.5,
      "basePoint": { "lat": 33.7744675, "lng": -84.29508709999999 }
    },
    "nextReportDate": "2026-04-01T14:00:00Z",
    "points": [
      {
        "id": "4b966e5e-e3d9-4ccf-91de-ab3bb2c2804f",
        "index": 0,
        "isEnabled": true,
        "coordinates": { "lat": 33.760976614131074, "lng": -84.31131325078074 }
      },
      {
        "id": "4c4efb9e-f6f6-4ada-bc47-1bf7dd91ec42",
        "index": 1,
        "isEnabled": true,
        "coordinates": { "lat": 33.760977410466175, "lng": -84.30320017544062 }
      }
    ],
    "countryCode": "US",
    "business": {
      "cid": "1773036218039458676",
      "placeIds": ["ChIJ0WHHXq8H9YgRdNsk3gsXmxg"],
      "name": "The Deer and The Dove",
      "address": "155 Sycamore St, Decatur, GA 30030",
      "rating": 4.4,
      "reviewNumber": 484,
      "coordinates": { "lat": 33.7744675, "lng": -84.29508709999999 }
    },
    "createdAt": "2026-03-02T14:12:59.058330774Z",
    "status": "CREATED",
    "statusUpdatedAt": "2026-03-02T14:12:59.058337674Z",
    "projectMetrics": {},
    "name": "The Deer and The Dove"
  }
}
```

## See Also

- [UpdateCampaign](local_map_rank_campaign_update.md)
- [CollectCampaign](local_map_rank_collect.md)
- [DeleteCampaign](local_map_rank_campaign_delete.md)
- [GetUserLimits](local_map_rank_limits.md)
- [Map Rank Tracker Overview](local_map_rank_overview.md)
