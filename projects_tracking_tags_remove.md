# Position Tracking — Remove Tags From Keywords

**Price:** 100 API units per request

Deletes up to **five tags** assigned to each tracked keyword.

## Endpoint

```
DELETE https://api.semrush.com/management/v1/projects/{campaignID}/tags?key=YOUR_API_KEY
```

## Parameters

| Parameter | Required | Type | Description |
|---|---|---|---|
| `key` | Yes | string | API key from Subscription info > API units. |
| `campaignID` | Yes | string | Campaign ID (path parameter). See [how to get your campaign ID](projects_api_overview.md#get-your-campaign-id). |
| `keywords` | No | array | Keywords to remove tags from. |
| `tags` | No | array | Tags to remove. |

## Response Fields

| Field | Type | Description |
|---|---|---|
| `url` | string | Domain of the tracking campaign. |
| `tools` | array | List of project tools activated by the user. |
| `project_id` | string | Project ID. |
| `project_name` | string | Project name. |
| `campaign_id` | string | Campaign ID. |
| `competitors` | array | Competitors. |
| `keywords` | array | Keywords with their updated tag arrays. |

## Example Request Body

```json
[{"tag":"seo", "keywords":["search tool", "search engine"]},{"tag":"seo tool", "keywords":["search tool", "search engine"]}]
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
    "ebay.com"
  ],
  "keywords": [
    {
      "keyword": "search tool",
      "tags": [
        "search"
      ],
      "timestamp": 1391517755
    },
    {
      "keyword": "search engine",
      "tags": [
        "search"
      ],
      "timestamp": 1391517755
    }
  ]
}
```

## See Also

- [Add tags to keywords](projects_tracking_tags_add.md)
- [Position Tracking Overview](projects_tracking_overview.md)
