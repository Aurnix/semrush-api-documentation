# Position Tracking — Campaign Dates

**Price:** 100 API units per request

Returns a list of dates when campaign data was harvested.

## Endpoint

```
GET https://api.semrush.com/reports/v1/projects/{campaignID}/tracking/
```

## Parameters

| Parameter | Required | Type | Description |
|---|---|---|---|
| `key` | Yes | string | API key from Subscription info > API units. |
| `action` | Yes | string | Type of action. Value: `report`. |
| `type` | Yes | string | Request type. Value: `tracking_campaign_dates`. |

## Response Fields

| Field | Type | Description |
|---|---|---|
| `total` | integer | Number of results. |
| `last_crawl` | integer | Hours elapsed since the last crawl. |
| `data` | object | Map of index → `{Dt: <date in YYYYMMDD>}`. |

## Example Request

```
GET /?key=YOUR_API_KEY&action=report&type=tracking_campaign_dates
```

## Example Response

```json
{
  "total": "9",
  "last_crawl": "2",
  "data": {
    "0": { "Dt": "20140401" },
    "1": { "Dt": "20140402" },
    "2": { "Dt": "20140403" },
    "3": { "Dt": "20140404" }
  }
}
```

## See Also

- [Position Tracking Overview](projects_tracking_overview.md)
