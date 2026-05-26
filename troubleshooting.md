# Troubleshooting

> For unresolved issues, contact Semrush Tech Support. Include: the specific endpoint, the full API request, any error messages, and your account type.

---

## Why API Data May Differ from the Semrush UI

API results don't always match the Semrush UI. Most discrepancies are caused by differing settings, filters, or data scope.

---

### Filters Applied Differently

The UI may have filters active (keyword type, SERP features, backlink type, etc.) while the API call fetches unfiltered data — or vice versa. Misconfigured API filters can also produce different results.

**Solution:** Verify that the same filters are applied in both the UI and the API request.

---

### Different Data Scope (Domain vs. Subdomain vs. Subfolder)

The UI allows drilling into subdomains or subfolders, but some API endpoints only support root domain level. For example, the Backlinks overview endpoint does not support subfolder scope, while the UI does. Comparing a subfolder in the UI against a root domain in the API will produce mismatches.

**Solution:** Confirm you are comparing the same scope. If the API doesn't support the required level, results will not align.

---

### Other Common Differences

| Cause | Detail |
|-------|--------|
| **Date ranges and update cycles** | The API may pull fresher data while the UI shows cached data, or updates run on slightly different schedules. |
| **Metric definitions and aggregation** | Some metrics are rounded or aggregated differently. For example, UI traffic is shown as a monthly total; the API provides daily data that must be summed. |
| **Limits and pagination** | Endpoints returning top-N results only return part of the dataset unless `display_limit` and `display_offset` are used for pagination. |
| **Naming differences** | API endpoint names and UI tool names don't always match. For example, the UI's "Domain Overview" report maps to the `domain_organic` API endpoint. |
