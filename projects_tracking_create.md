# Position Tracking — Create a Campaign

**Price:** 100 API units per request

Creates a Position Tracking campaign in a project. The newly created campaign has no keywords — add them with [Add keywords to an existing tracking campaign](projects_tracking_keywords_add.md).

When creating a campaign in a project with one or more existing tracking campaigns, the combination of `location_id` and `device` must differ from those in the existing campaigns.

The `campaign_id` value from the response is used as `{campaignID}` in other Position Tracking requests.

## Endpoint

```
POST https://api.semrush.com/management/v1/projects/{projectID}/tracking/enable?key=YOUR_API_KEY
```

## Parameters

| Parameter | Required | Type | Description |
|---|---|---|---|
| `key` | Yes | string | API key from Subscription info > API units. |
| `tracking_url_type` | Yes | enum | Type of the tracked URL. Values: `rootdomain`, `subdomain`, `subfolder`, `url`. |
| `tracking_url` | Yes | string | Tracked URL. |
| `location_id` | Yes | integer | Location ID. Use [Universal location search](projects_tracking_locations.md) to look this up. |
| `weekly_notification` | No | boolean | `true` (default): enable weekly emails. `false`: disable. |
| `timezone` | No | integer | Time zone. Crawling starts at 05:00 in the specified time zone. |
| `device` | No | enum | Target device. Values: `desktop`, `phone`, `tablet`. |
| `business_name` | No | string | Business name. |

## Example Request Body

```json
{
  "tracking_url": "example.com",
  "tracking_url_type": "rootdomain",
  "location_id": 2840,
  "weekly_notification": true,
  "device": "desktop",
  "business_name": "example.com"
}
```

## Example Response

```json
{
  "status": "SUCCESS",
  "action": "tracking_enable",
  "result": {
    "campaign_id": "103345921_15710"
  }
}
```

## See Also

- [Position Tracking Overview](projects_tracking_overview.md)
- [Add keywords](projects_tracking_keywords_add.md)
- [Universal location search](projects_tracking_locations.md)
