# Position Tracking — Get A List Of Campaigns

**Price:** 100 API units per request

Returns a list of campaigns in the specified project and basic information about each.

To see all your tracking campaigns in the Semrush web UI, refer to the [Position Tracking main page](https://www.semrush.com/position-tracking/).

## Endpoint

```
GET https://api.semrush.com/management/v1/projects/{projectID}/tracking/campaigns?key=YOUR_API_KEY
```

## Parameters

| Parameter | Required | Type | Description |
|---|---|---|---|
| `key` | Yes | string | API key from Subscription info > API units. |
| `projectID` | Yes | string | Project ID (path parameter). See [how to get your project ID](projects_api_overview.md#get-your-project-id). |

## Response Fields

| Field | Type | Description |
|---|---|---|
| `project_id` | string | Project ID. |
| `campaigns` | array | List of campaigns. |
| `campaigns[].id` | string | Campaign ID. |
| `campaigns[].url` | string | Tracked URL. |
| `campaigns[].type` | string | Tracked URL type. |
| `campaigns[].engine` | string | Search engine. |
| `campaigns[].location.id` | integer | Location ID. |
| `campaigns[].location.name` | string | Location name. |
| `campaigns[].location.type` | string | Location type. |
| `campaigns[].location.code` | string | Location code. |
| `campaigns[].location.hl` | string | Language code. |
| `campaigns[].isGathering` | boolean | Whether the campaign is currently being harvested. |
| `campaigns[].language` | string | Language. |
| `campaigns[].device` | string | Type of SERPs the campaign tracks: `desktop`, `phone`, or `tablet`. |
| `campaigns[].keywords_count` | integer | Number of keywords in the campaign. |
| `limits.targets` | integer | Number of targets available under the user's subscription. |

## Example Response

```json
{
  "project_id": "103580023",
  "campaigns": [
    {
      "id": "103580023_16852",
      "url": "apple.com",
      "type": "rootdomain",
      "engine": "google",
      "location": {
        "id": 1014221,
        "name": "San Francisco, California, United States",
        "type": "city",
        "code": "us",
        "hl": "en"
      },
      "isGathering": false,
      "language": "English",
      "device": "desktop",
      "keywords_count": 81
    }
  ],
  "limits": {
    "targets": 5000
  }
}
```

## See Also

- [Create a Position Tracking campaign](projects_tracking_create.md)
- [Position Tracking Overview](projects_tracking_overview.md)
