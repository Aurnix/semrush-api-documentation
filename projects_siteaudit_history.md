# Site Audit — Get Snapshots History

**Price:** 10,000 API units per request
**Alternative price:** 10,000 API units per snapshot returned

Returns audit results for a selected period. The total cost scales with the number of snapshots returned — e.g., five audits in one request cost 50,000 API units.

## Endpoint

```
GET https://api.semrush.com/reports/v1/projects/{ID}/siteaudit/history?limit={limit}&offset={offset}&key=YOUR_API_KEY
```

## Parameters

| Parameter | Required | Type | Description |
|---|---|---|---|
| `key` | Yes | string | API key for your Semrush account. |
| `ID` | Yes | string | Project ID. |
| `limit` | Yes | integer | Number of snapshots to return. Default `7`. |
| `offset` | Yes | integer | Number of snapshots to skip. Default `0`. |

## Response Fields

| Field | Type | Description |
|---|---|---|
| `data` | array | Snapshot entries. Each entry has the same shape as [Get information about snapshot](projects_siteaudit_snapshot.md). |
| `data[].quality.value` | integer | Website score. |
| `data[].quality.delta` | integer | Score difference vs. the previous audit. |
| `data[].snapshot_id` | string | Snapshot ID. |
| `data[].pages_crawled` | integer | Pages crawled. |
| `data[].finish_date` | integer | Unix timestamp (ms) when the audit completed. |
| `data[].errors` / `warnings` / `notices` | array | Per-issue breakdowns with `id`, `count`, `delta`, `checks`. See [Issue IDs](projects_siteaudit_overview.md#issue-ids). |
| `total` | integer | Total snapshots. |
| `limit` | integer | Number of returned results. |
| `offset` | integer | Number of lines skipped. |

## Example Response

```json
{
  "data": [
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
  ],
  "total": 0,
  "limit": 0,
  "offset": 0
}
```

## See Also

- [Get information about snapshot](projects_siteaudit_snapshot.md)
- [Get list of campaign snapshots](projects_siteaudit_snapshots.md)
- [Site Audit Overview](projects_siteaudit_overview.md) — Issue IDs
