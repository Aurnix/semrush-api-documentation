# Position Tracking — Disable Email Notifications

**Price:** 100 API units per request

Disables the delivery of weekly emails containing tracking campaign statistics.

## Endpoint

```
DELETE https://api.semrush.com/management/v1/projects/{campaignID}/tracking/notifications?key=YOUR_API_KEY
```

## Parameters

| Parameter | Required | Type | Description |
|---|---|---|---|
| `key` | Yes | string | API key from Subscription info > API units. |
| `campaignID` | Yes | string | Campaign ID (path parameter). See [how to get your campaign ID](projects_api_overview.md#get-your-campaign-id). |

## See Also

- [Enable email notifications](projects_tracking_notifications_enable.md)
- [Position Tracking Overview](projects_tracking_overview.md)
