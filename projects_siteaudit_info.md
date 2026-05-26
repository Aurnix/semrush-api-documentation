# Site Audit — Get Information About Campaign

**Price:** 100 API units per request

Returns a summary of the most recent audit: counts of errors, warnings, and notices; checks passed/failed; pages crawled and pending; and the date of the last audit.

## Endpoint

```
GET https://api.semrush.com/reports/v1/projects/{ID}/siteaudit/info?key=YOUR_API_KEY
```

## Parameters

| Parameter | Required | Type | Description |
|---|---|---|---|
| `key` | Yes | string | API key for your Semrush account. |
| `ID` | Yes | string | Project ID. |

## Response Fields

| Field | Type | Description |
|---|---|---|
| `id` | integer | Project ID. |
| `url` | string | Project URL. |
| `name` | string | Project name. |
| `status` | string | Audit status: `RUNNING`, `FINISHED`, `CHECKING`, or `SAVING`. |
| `errors` | integer | Errors found during the last audit. |
| `warnings` | integer | Warnings found during the last audit. |
| `notices` | integer | Notices found during the last audit. |
| `broken` | integer | Number of broken pages. |
| `blocked` | integer | Number of pages blocked from crawling. |
| `redirected` | integer | Number of redirecting pages. |
| `healthy` | integer | Number of healthy pages. |
| `haveIssues` | integer | Pages with issues. |
| `haveIssuesDelta` | integer | Difference in issues found vs. the previous audit. |
| `defects` | object | Map of [issue ID](projects_siteaudit_overview.md#issue-ids) → number of detections. |
| `markups` | object | Counts for `twitterCard`, `openGraph`, `schemaOrg`, `microfomats`. |
| `depths` | object | Click depth → number of pages at that depth from the homepage. |
| `crawlSubdomains` | boolean | Whether subdomains were crawled. |
| `respectCrawlDelay` | boolean | Whether `Crawl-delay` in `robots.txt` was respected. |
| `user_agent_type` | integer | User agent. See [User agent types](projects_siteaudit_overview.md#user-agent-types). |
| `last_audit` | integer | Unix timestamp (ms) of the last audit. |
| `last_failed_audit` | integer | Unix timestamp (ms) of the last failed audit. |
| `next_audit` | integer | Unix timestamp (ms) of the next scheduled audit. `-1` if none scheduled. |
| `running_pages_crawled` | integer | Pages crawled during a running audit. |
| `running_pages_limit` | integer | Crawl page limit for the running audit. |
| `pages_crawled` | integer | Pages crawled in the last completed audit. |
| `pages_limit` | integer | Crawl page limit. |
| `total_checks` | integer | Number of checks performed in the last audit. |
| `errors_delta` | integer | Difference in errors vs. the previous audit. |
| `warnings_delta` | integer | Difference in warnings vs. the previous audit. |
| `notices_delta` | integer | Difference in notices vs. the previous audit. |
| `mask_allow` | array[string] | Masks for the `Allow` directive. |
| `mask_disallow` | array[string] | Masks for the `Disallow` directive. |
| `removedParameters` | array[string] | URL parameters excluded from the audit scope. |
| `excluded_checks` | array[integer] / null | IDs of issues excluded from the audit scope. |

## Example Response

```json
{
  "id": 4594705336925861,
  "name": "test",
  "url": "semrush.com",
  "status": "FINISHED",
  "errors": 228,
  "warnings": 391,
  "notices": 9,
  "broken": 0,
  "blocked": 0,
  "redirected": 2,
  "healthy": 1,
  "haveIssues": 2,
  "haveIssuesDelta": 0,
  "defects": { "109": 2 },
  "markups": {
    "twitterCard": 0,
    "openGraph": 0,
    "schemaOrg": 0,
    "microfomats": 0
  },
  "depths": { "0": 3 },
  "crawlSubdomains": true,
  "respectCrawlDelay": false,
  "user_agent_type": 2,
  "last_audit": 1410346398040,
  "last_failed_audit": 0,
  "next_audit": -1,
  "running_pages_crawled": 178,
  "running_pages_limit": 500,
  "pages_crawled": 178,
  "pages_limit": 500,
  "total_checks": 22725,
  "errors_delta": 0,
  "warnings_delta": 0,
  "notices_delta": 0,
  "mask_allow": [],
  "mask_disallow": [],
  "removedParameters": ["rr", "r", "p"],
  "excluded_checks": null
}
```

## See Also

- [Get information about snapshot](projects_siteaudit_snapshot.md)
- [Get snapshots history](projects_siteaudit_history.md)
- [Site Audit Overview](projects_siteaudit_overview.md) — Issue IDs, user agent types
