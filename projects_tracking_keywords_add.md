# Position Tracking — Add Keywords To A Tracking Campaign

**Price:** 100 API units per keyword added

Adds keywords to track to an existing tracking campaign and optionally groups them with tags.

## Endpoint

```
PUT https://api.semrush.com/management/v1/projects/{campaignID}/keywords?key=YOUR_API_KEY
```

## Parameters

| Parameter | Required | Type | Description |
|---|---|---|---|
| `key` | Yes | string | API key from Subscription info > API units. |
| `campaignID` | Yes | string | Campaign ID (path parameter). See [how to get your campaign ID](projects_api_overview.md#get-your-campaign-id). |
| `keywords` | No | array | Keywords (each with optional `tags`). |
| `tags` | No | array | Tags for a keyword. |

## Response Fields

| Field | Type | Description |
|---|---|---|
| `url` | string | Domain of the tracking campaign. |
| `tools` | array | List of project tools activated by the user. |
| `project_id` | string | Project ID. |
| `project_name` | string | Project name. |
| `campaign_id` | string | Campaign ID. |
| `competitors` | array | Competitors. |
| `keywords` | array | Keywords. Each keyword object includes `keyword`, `tags`, and `timestamp`. |

## Example Request Body

```json
{"keywords":[{"keyword":"seo", "tags":["seo"]},{"keyword":"seotool", "tags":["seo"]}]}
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
  "project_name": "my old project",
  "campaign_id": "643526670283248_17238",
  "competitors": [
    "google.com",
    "ebay.com",
    "bing.com"
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
    },
    {
      "keyword": "seo",
      "tags": [
        "seo"
      ],
      "timestamp": 1491517755
    },
    {
      "keyword": "seotool",
      "tags": [
        "seo"
      ],
      "timestamp": 1491517755
    }
  ]
}
```

## See Also

- [Remove keywords](projects_tracking_keywords_remove.md)
- [Add tags to keywords](projects_tracking_tags_add.md)
- [Position Tracking Overview](projects_tracking_overview.md)
