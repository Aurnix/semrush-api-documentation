# Site Audit — Enable Site Audit Tool

**Price:** 100 API units per request

Enables the Site Audit tool for a project. Lets you schedule audits, include or exclude pages from the crawl, and set the number of pages to crawl.

## Endpoint

```
POST https://api.semrush.com/management/v1/projects/{ID}/siteaudit/enable?key=YOUR_API_KEY
```

## Parameters

Path / query:

| Parameter | Required | Type | Description |
|---|---|---|---|
| `key` | Yes | string | API key for your Semrush account. |
| `ID` | Yes | string | Project ID. |

Request body (JSON):

| Field | Required | Type | Description |
|---|---|---|---|
| `domain` | Yes | string | Project URL. |
| `pageLimit` | Yes | integer | Number of pages to crawl. |
| `scheduleDay` | No | integer | Day of the week (`1`–`7`) for periodic execution. Use `0` for manual start. |
| `notify` | No | boolean | Send email notification on audit completion. |
| `allow` | No | array[string] | Masks for the `Allow` directive. |
| `disallow` | No | array[string] | Masks for the `Disallow` directive. |
| `userAgentType` | No | integer | User agent. `2` GoogleBot Desktop, `3` GoogleBot Mobile, `7` SiteAuditBot Desktop, `8` SiteAuditBot Mobile, `9` OpenAI-Search. See [User agent types](projects_siteaudit_overview.md#user-agent-types). |
| `removedParameters` | No | array[string] | URL parameters to exclude from the audit scope. |
| `crawlSubdomains` | No | boolean | `true`: crawl the domain and its subdomains. `false`: crawl only the selected domain. |
| `respectCrawlDelay` | No | boolean | `true`: follow the `Crawl-delay` directive in `robots.txt`. `false`: crawl with a one-second interval. |

## Example Request

```
POST https://api.semrush.com/management/v1/projects/{ID}/siteaudit/enable?key=YOUR_API_KEY
```

```json
{
  "domain": "www.mysite.com",
  "scheduleDay": 1,
  "notify": false,
  "allow": ["", "", ""],
  "disallow": ["", "", ""],
  "pageLimit": 1000,
  "userAgentType": 2,
  "removedParameters": ["", "", ""],
  "crawlSubdomains": true,
  "respectCrawlDelay": false
}
```

## See Also

- [Edit campaign](projects_siteaudit_edit.md)
- [Run audit](projects_siteaudit_launch.md)
- [Site Audit Overview](projects_siteaudit_overview.md)
