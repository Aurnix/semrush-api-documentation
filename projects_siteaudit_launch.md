# Site Audit — Run Audit

**Price:** 100 API units per request

Starts a new audit for the project. Returns the snapshot ID that identifies the audit.

## Endpoint

```
POST https://api.semrush.com/reports/v1/projects/{ID}/siteaudit/launch?key=YOUR_API_KEY
```

## Parameters

| Parameter | Required | Type | Description |
|---|---|---|---|
| `key` | Yes | string | API key for your Semrush account. |
| `ID` | Yes | string | Project ID. |

## Response Fields

| Field | Type | Description |
|---|---|---|
| `snapshot_id` | string | Snapshot ID for the new audit. Use it with [Get information about snapshot](projects_siteaudit_snapshot.md) and [Detailed report for issue](projects_siteaudit_issue_detail.md). |

## Example Response

```json
{
  "snapshot_id": "54102d92e4b0f889a040c9c8"
}
```

## See Also

- [Enable Site Audit tool](projects_siteaudit_enable.md)
- [Edit campaign](projects_siteaudit_edit.md)
- [Get list of campaign snapshots](projects_siteaudit_snapshots.md)
- [Get information about campaign](projects_siteaudit_info.md)
- [Site Audit Overview](projects_siteaudit_overview.md)
