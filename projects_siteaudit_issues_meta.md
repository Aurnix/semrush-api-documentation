# Site Audit — Get Text Descriptions About Issues

**Price:** 100 API units per request

Returns a detailed explanation of each issue and its cause, helping you understand why an issue could be harmful and how to fix it.

## Endpoint

```
GET https://api.semrush.com/reports/v1/projects/{ID}/siteaudit/meta/issues?key=YOUR_API_KEY
```

## Parameters

| Parameter | Required | Type | Description |
|---|---|---|---|
| `key` | Yes | string | API key for your Semrush account. |
| `ID` | Yes | string | Project ID. |

## Response Fields

| Field | Type | Description |
|---|---|---|
| `issues` | array | Issue descriptions. |
| `id` | integer | Issue ID. See [Issue IDs](projects_siteaudit_overview.md#issue-ids). |
| `title` | string | Issue title. |
| `title_page` | string | Page title (template; `##count##` is replaced with the count). |
| `url_column` | string | Label of the URL column. |
| `info_column` | string | Label of the info column. |

## Example Response

```json
{
  "issues": [
    {
      "id": 14,
      "title": "Broken external images",
      "title_page": "##count## external images are broken",
      "url_column": "Image URL",
      "info_column": "HTTP Code"
    }
  ]
}
```

## See Also

- [Detailed report for issue](projects_siteaudit_issue_detail.md)
- [Get information about snapshot](projects_siteaudit_snapshot.md)
- [Site Audit Overview](projects_siteaudit_overview.md) — full list of Issue IDs
