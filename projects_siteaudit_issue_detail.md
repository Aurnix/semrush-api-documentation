# Site Audit — Detailed Report for Issue

**Price:** 100 API units per request

Returns a description of the issue, when it was detected, and the URLs of affected pages. Fetches data for the most recent snapshot of the project.

## Endpoint

```
GET https://api.semrush.com/reports/v1/projects/{ID}/siteaudit/snapshot/{snapshotId}/issue/{issueId}?key=YOUR_API_KEY
```

## Parameters

| Parameter | Required | Type | Description |
|---|---|---|---|
| `key` | Yes | string | API key for your Semrush account. |
| `ID` | Yes | string | Project ID. |
| `snapshotId` | Yes | string | Snapshot ID. Obtain from [Run audit](projects_siteaudit_launch.md) or [Get list of campaign snapshots](projects_siteaudit_snapshots.md). |
| `issueId` | Yes | integer | Issue ID. See [Issue IDs](projects_siteaudit_overview.md#issue-ids). |
| `sort` | No | string | Sort direction. Default `DESC`. |
| `page` | No | integer | Page number. Default `1`. |
| `limit` | No | integer | Results per page. Default `10`. |
| `filter` | No | string | One or more filters. Repeat the parameter for multiple filters. See [Filters](projects_siteaudit_overview.md#filters). |

## Response Fields

| Field | Type | Description |
|---|---|---|
| `limit` | integer | Results per page. |
| `page` | integer | Page number. |
| `total` | integer | Total number of results. |
| `issue_id` | integer | Issue ID. |
| `data` | array | Affected pages. |
| `target_url` | string | Target URL. For broken-link issues, this is the URL returning an error. |
| `page_id` | string | Page ID. |
| `source_url` | string | URL of the page where the error was detected. |

## Example Request

```
https://api.semrush.com/reports/v1/projects/{ID}/siteaudit/snapshot/{snapshotId}/issue/{issueId}?page={page}&filter={filter}&sort={sort}&limit={limit}&key=YOUR_API_KEY
```

## Example Response

```json
{
  "limit": 10,
  "page": 1,
  "total": 101,
  "data": [
    {
      "target_url": "http://semrush.com/errors/404.html",
      "page_id": "54102d9e0cf2e0c100696c88",
      "source_url": "http://semrush.com"
    }
  ],
  "issue_id": 8
}
```

## See Also

- [Get text descriptions about issues](projects_siteaudit_issues_meta.md)
- [Get information about snapshot](projects_siteaudit_snapshot.md)
- [Get information about page](projects_siteaudit_page.md)
- [Site Audit Overview](projects_siteaudit_overview.md) — Issue IDs, filters
