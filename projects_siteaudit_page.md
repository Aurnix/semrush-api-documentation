# Site Audit — Get Information About Page

**Price:** 1,000 API units per request

Returns information about a single crawled page and the list of issues detected on it (errors, warnings, and notices).

## Endpoint

```
GET https://api.semrush.com/reports/v1/projects/{ID}/siteaudit/page/{pageId}?key=YOUR_API_KEY
```

## Parameters

| Parameter | Required | Type | Description |
|---|---|---|---|
| `key` | Yes | string | API key for your Semrush account. |
| `ID` | Yes | string | Project ID. |
| `pageId` | Yes | string | Page ID. Obtain via [Get page ID by URL](projects_siteaudit_page_list.md). |

## Response Fields

| Field | Type | Description |
|---|---|---|
| `title` | string | Page title. |
| `url` | string | Page URL. |
| `page_id` | string | Page ID. |
| `notices` / `warnings` / `errors` | array | Per-issue groups detected on the page. |
| `notices\|warnings\|errors[].id` | integer | Issue ID. See [Issue IDs](projects_siteaudit_overview.md#issue-ids). |
| `notices\|warnings\|errors[].total` | integer | Total occurrences of this issue. |
| `notices\|warnings\|errors[].data` | array | Detailed occurrences. |
| `notices\|warnings\|errors[].data[].discovered` | integer | Unix timestamp (ms) when the issue was discovered. |
| `notices\|warnings\|errors[].data[].info` | object / null | Issue description (e.g. HTTP status). |
| `notices\|warnings\|errors[].data[].target_url` | string | Target URL. For broken-link issues, the URL returning an error. |

## Example Response

```json
{
  "title": "Web Tutorials  •  Mike & Associates",
  "url": "http://semrush.com",
  "notices": [
    {
      "id": 202,
      "data": [
        {
          "discovered": 1410178856809,
          "info": null,
          "target_url": "http://%/test.com"
        }
      ],
      "total": 8
    }
  ],
  "warnings": [
    {
      "id": 110,
      "data": [
        {
          "discovered": 1410178856809,
          "info": null,
          "target_url": "http://semrush.com/index_files/html.jpg"
        }
      ],
      "total": 200
    }
  ],
  "errors": [
    {
      "id": 8,
      "data": [
        {
          "discovered": 1410178856809,
          "info": "503",
          "target_url": "http://semrush.com/errors/503.html"
        }
      ],
      "total": 101
    }
  ],
  "page_id": "54102d9e0cf2e0c100696c88"
}
```

## See Also

- [Get page ID by URL](projects_siteaudit_page_list.md)
- [Detailed report for issue](projects_siteaudit_issue_detail.md)
- [Site Audit Overview](projects_siteaudit_overview.md) — Issue IDs
