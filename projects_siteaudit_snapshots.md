# Site Audit — Get List of Campaign Snapshots

**Price:** 100 API units per request

Returns a list of previous audit IDs along with their completion dates.

## Endpoint

```
GET https://api.semrush.com/reports/v1/projects/{ID}/siteaudit/snapshots?key=YOUR_API_KEY
```

## Parameters

| Parameter | Required | Type | Description |
|---|---|---|---|
| `key` | Yes | string | API key for your Semrush account. |
| `ID` | Yes | string | Project ID. |

## Response Fields

| Field | Type | Description |
|---|---|---|
| `snapshots` | array | Snapshots for the project. |
| `snapshot_id` | string | Snapshot ID. |
| `finish_date` | integer | Unix timestamp (ms) when the audit completed, e.g. `1410178856809`. |

## Example Response

```json
{
  "snapshots": [
    {
      "snapshot_id": "540d9e420cf2e0c1006966e3",
      "finish_date": 1410178856809
    },
    {
      "snapshot_id": "54102bd20cf2e0c100696a10",
      "finish_date": 1410345954754
    }
  ]
}
```

## See Also

- [Get information about snapshot](projects_siteaudit_snapshot.md)
- [Get snapshots history](projects_siteaudit_history.md)
- [Run audit](projects_siteaudit_launch.md)
- [Site Audit Overview](projects_siteaudit_overview.md)
