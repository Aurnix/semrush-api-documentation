# Position Tracking — Add Competitors To A Tracking Campaign

**Price:** 100 API units per request

Adds up to **20 competitor domains** to an existing tracking campaign.

## Endpoint

```
PUT https://api.semrush.com/management/v1/projects/{campaignID}/competitors?key=YOUR_API_KEY
```

## Parameters

| Parameter | Required | Type | Description |
|---|---|---|---|
| `key` | Yes | string | API key from Subscription info > API units. |
| `campaignID` | Yes | string | Campaign ID (path parameter). See [how to get your campaign ID](projects_api_overview.md#get-your-campaign-id). |
| `competitors` | No | array | List of competitor domains. Maximum 20. |

## Response Fields

| Field | Type | Description |
|---|---|---|
| `url` | string | Domain of the tracking campaign. |
| `tools` | array | List of project tools activated by the user. |
| `project_id` | string | Project ID. |
| `project_name` | string | Project name. |
| `campaign_id` | string | Campaign ID. |
| `competitors` | array | Updated competitor list. |
| `keywords` | array | Keywords. |

## Example Request Body

```json
{"competitors":["yahoo.com"]}
```

## Example Response

```json
{
  "url": "mysite.com",
  "tools": [
    {
      "tool": "tracking"
    }
  ],
  "project_id": 643526670283248,
  "project_name": "myproject",
  "campaign_id": 643526670283248_17238,
  "competitors": [
    "google.com",
    "ebay.com",
    "yahoo.com"
  ]
}
```

## See Also

- [Remove competitors](projects_tracking_competitors_remove.md)
- [Organic competitors discovery](projects_tracking_competitors_organic.md)
- [Position Tracking Overview](projects_tracking_overview.md)
