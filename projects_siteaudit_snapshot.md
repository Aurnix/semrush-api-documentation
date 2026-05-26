# Site Audit — Get Information About Snapshot

**Price:** 10,000 API units per request

Returns an overview of a single audit: the website's score, lists of errors / warnings / notices with counts and deltas, and the number of checks performed.

## Endpoint

```
GET https://api.semrush.com/reports/v1/projects/{ID}/siteaudit/snapshot?key=YOUR_API_KEY&snapshot_id={snapshot_id}
```

## Parameters

| Parameter | Required | Type | Description |
|---|---|---|---|
| `key` | Yes | string | API key for your Semrush account. |
| `ID` | Yes | string | Project ID. |
| `snapshot_id` | Yes | string | Snapshot ID. Obtain from [Run audit](projects_siteaudit_launch.md) or [Get list of campaign snapshots](projects_siteaudit_snapshots.md). |

## Response Fields

| Field | Type | Description |
|---|---|---|
| `quality.value` | integer | Website score. |
| `quality.delta` | integer | Difference in score vs. the previous audit. |
| `snapshot_id` | string | Snapshot ID. |
| `pages_crawled` | integer | Number of crawled pages. |
| `finish_date` | integer | Unix timestamp (ms) when the audit completed. |
| `errors` / `warnings` / `notices` | array | Per-issue breakdown. |
| `errors\|warnings\|notices.id` | integer | Issue ID. See [Issue IDs](projects_siteaudit_overview.md#issue-ids). |
| `errors\|warnings\|notices.count` | integer | Number of detections. |
| `errors\|warnings\|notices.delta` | integer | Difference vs. the previous audit. |
| `errors\|warnings\|notices.checks` | integer | Number of checks performed. |

## Example Response

```json
{
  "quality": { "value": 42, "delta": 0 },
  "errors": [
    { "id": 1, "count": 4, "delta": 0, "checks": 174 }
  ],
  "warnings": [
    { "id": 101, "count": 2, "delta": 0, "checks": 127 }
  ],
  "notices": [
    { "id": 201, "count": 1, "delta": 0, "checks": 127 }
  ],
  "snapshot_id": "54102d92e4b0f889a040c9c8",
  "pages_crawled": 178,
  "finish_date": 1410346398040
}
```

## See Also

- [Detailed report for issue](projects_siteaudit_issue_detail.md)
- [Get snapshots history](projects_siteaudit_history.md)
- [Get list of campaign snapshots](projects_siteaudit_snapshots.md)
- [Site Audit Overview](projects_siteaudit_overview.md) — Issue IDs
