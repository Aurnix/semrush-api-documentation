# Trends API — Geo Distribution

**Cost:** 1 API unit per request  
**Billing note:** Units are charged even if the response is empty.

Returns a breakdown of traffic to a domain by country, subcontinent, or continent. Useful for understanding the geographic diversity of a market audience.

---

## Endpoint

```
GET https://api.semrush.com/analytics/ta/api/v3/geo
```

---

## Request Parameters

| Parameter | Required | Description |
|-----------|----------|-------------|
| `key` | Yes | Your API key (from Subscription info → API Units) |
| `target` | Yes | Root domain. Use `target_type` for subdomains or subfolders. |
| `target_type` | No | `domain` (default), `subdomain`, or `subfolder` |
| `display_date` | No | Month in `YYYY-MM-01` format. Defaults to previous month. Min: `2017-01-01`. Max: start of previous month. |
| `device_type` | No | `desktop` or `mobile`. Defaults to all devices. |
| `display_limit` | No | Results per request. Default: `1000`. Max: `5000`. |
| `display_offset` | No | Results to skip for pagination. Default: `0`. No maximum. |
| `geo_type` | No | Geographic granularity: `country` (default), `subcontinent`, or `continent`. When set to `continent` or `subcontinent`, the `geo` column contains region codes — see Geo Type Codes reference. |
| `sort_order` | No | Sort field + direction. Append `_desc` (default) or `_asc`. Options: `traffic`, `traffic_share`, `desktop_share`, `mobile_share`, `avg_visit_duration`, `pages_per_visit`, `bounce_rate`. |
| `export_columns` | No | Comma-separated columns to return. Defaults to all columns. |

---

## Export Columns

| Column | Description |
|--------|-------------|
| `target` | The analyzed domain/subdomain/subfolder |
| `display_date` | Month of the data |
| `device_type` | Device type filter used |
| `geo` | Country code (ISO 3166-1 Alpha-2), subcontinent code, or continent code depending on `geo_type` |
| `traffic` | Estimated visits from this geography |
| `global_traffic` | Total global traffic for the target |
| `traffic_share` | Share of total traffic from this geography (decimal) |
| `users` | Unique visitors from this geography |
| `avg_visit_duration` | Average visit duration in seconds |
| `bounce_rate` | Bounce rate |
| `pages_per_visit` | Pages per visit |
| `desktop_share` | Share of desktop traffic |
| `mobile_share` | Share of mobile traffic |

---

## Request Example

```
https://api.semrush.com/analytics/ta/api/v3/geo?display_date=2020-01-01&device_type=desktop&display_limit=7&display_offset=0&target=ebay.com&target_type=domain&geo_type=country&export_columns=target,display_date,device_type,geo,traffic,avg_visit_duration&key=YOUR_API_KEY
```

## Response Example (CSV)

```
target;display_date;device_type;geo;traffic;avg_visit_duration
ebay.com;2020-01-01;desktop;us;192581931;706
ebay.com;2020-01-01;desktop;ru;7305169;970
ebay.com;2020-01-01;desktop;ca;6392463;819
ebay.com;2020-01-01;desktop;il;5099407;1048
ebay.com;2020-01-01;desktop;mx;4277849;669
ebay.com;2020-01-01;desktop;br;3811888;711
ebay.com;2020-01-01;desktop;gb;3641529;384
```
