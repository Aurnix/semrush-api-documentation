# Map Rank Tracker — UpdateCampaign

Partial update of an existing Map Rank Tracker campaign. Only fields explicitly included in the request body are modified; all others remain unchanged.

Does not consume API units. Requires a Bearer Token.

## Tracking Area Configuration

`gridSettings` and `points` are mutually exclusive — providing both returns an error.

- **Custom grid** — provide `gridSettings` to recalculate the tracking grid.
- **Custom points** — provide `points` to override the tracked coordinates.
- **Unchanged** — provide neither.

## Endpoint

```
PATCH https://api.semrush.com/apis/v4/map-rank-tracker/v0/campaigns/:campaignId
```

## Headers

```
Authorization: Bearer YOUR_TOKEN
Content-Type: application/json
```

## Path Parameters

| Parameter | Required | Type | Description |
|---|---|---|---|
| `campaignId` | Yes | string | Campaign UUID. |

## Request Body

| Field | Required | Type | Description |
|---|---|---|---|
| `name` | No | string | Custom campaign name. |
| `keywords` | No | array[string] | Replaces the existing keyword list. Max 100; max 255 chars each. |
| `gridSettings` | No | object | New grid configuration. Cannot be combined with `points`. See [`gridSettings`](local_map_rank_overview.md#gridsettings). |
| `points` | No | array[object] | New point list. Cannot be combined with `gridSettings`. See [`points`](local_map_rank_overview.md#points). |
| `collectingFrequency` | No | object | Updated collection schedule. See [`collectingFrequency`](local_map_rank_overview.md#collectingfrequency). |

## Response

Returns the full updated [Campaign object](local_map_rank_overview.md#campaign-schema-response).

## Example Request

```
curl --location --request PATCH 'https://api.semrush.com/apis/v4/map-rank-tracker/v0/campaigns/94896106-e6bd-471b-960b-8d3f2a29b17c' \
  --header 'Authorization: Bearer ${YOUR_TOKEN}' \
  --header 'Content-Type: application/json' \
  --data '{
    "name": "Updated Demo Campaign",
    "collectingFrequency": {
      "frequency": "WEEKLY",
      "interval": 1,
      "positions": [3],
      "time": "12:00",
      "enable": true
    }
  }'
```

## Example Response

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
      "frequency": "WEEKLY",
      "positions": [3],
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
      }
    ],
    "countryCode": "US",
    "business": {
      "cid": "1773036218039458676",
      "placeIds": ["ChIJ0WHHXq8H9YgRdNsk3gsXmxg"],
      "name": "Updated Demo Campaign",
      "address": "155 Sycamore St, Decatur, GA 30030",
      "rating": 4.4,
      "reviewNumber": 484,
      "coordinates": { "lat": 33.7744675, "lng": -84.29508709999999 }
    },
    "createdAt": "2026-03-02T14:12:59.058330774Z",
    "status": "CREATED",
    "statusUpdatedAt": "2026-03-02T14:12:59.058337674Z",
    "projectMetrics": {},
    "name": "Updated Demo Campaign"
  }
}
```

## See Also

- [CreateCampaign](local_map_rank_campaign_create.md)
- [GetCampaign](local_map_rank_campaign_get.md)
- [DeleteCampaign](local_map_rank_campaign_delete.md)
- [Map Rank Tracker Overview](local_map_rank_overview.md)
