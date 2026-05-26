# Site Audit — Get Page ID by URL

**Price:** 100 API units per request

Returns the page ID for crawled pages matching the URL substring. Use the returned `page_id` with [Get information about page](projects_siteaudit_page.md).

## Endpoint

```
GET https://api.semrush.com/reports/v1/projects/{ID}/siteaudit/page/list?url={url}&limit={limit}&key=YOUR_API_KEY
```

## Parameters

| Parameter | Required | Type | Description |
|---|---|---|---|
| `key` | Yes | string | API key for your Semrush account. |
| `ID` | Yes | string | Project ID. |
| `url` | Yes | string | URL substring to match. |
| `limit` | No | integer | Result row limit. Default `10`. |

## Response Fields

| Field | Type | Description |
|---|---|---|
| `data` | array | Matched pages. |
| `data[].url` | string | Crawled page URL. |
| `data[].page_id` | string | Page ID. |
| `total` | integer | Total number of results. |

## Example Response

```json
{
  "data": [
    {
      "url": "http://semrush.com",
      "page_id": "54102d9e0cf2e0c100696c88"
    }
  ],
  "total": 178
}
```

## See Also

- [Get information about page](projects_siteaudit_page.md)
- [Detailed report for issue](projects_siteaudit_issue_detail.md)
- [Site Audit Overview](projects_siteaudit_overview.md)
