# Position Tracking — Enable Email Notifications

**Price:** 100 API units per request

Enables the delivery of weekly emails containing tracking campaign statistics.

## Endpoint

```
PUT https://api.semrush.com/management/v1/projects/{campaignID}/tracking/notifications?key=YOUR_API_KEY
```

## Parameters

| Parameter | Required | Type | Description |
|---|---|---|---|
| `key` | Yes | string | API key from Subscription info > API units. |
| `campaignID` | Yes | string | Campaign ID (path parameter). See [how to get your campaign ID](projects_api_overview.md#get-your-campaign-id). |

## See Also

- [Disable email notifications](projects_tracking_notifications_disable.md)
- [Position Tracking Overview](projects_tracking_overview.md)
