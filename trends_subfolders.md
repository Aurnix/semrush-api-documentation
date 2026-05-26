# Trends API — Subfolders

**Cost:** 1 API unit per request  
**Billing note:** Units are charged even if the response is empty.

Returns traffic data for the top subfolders of a domain or subdomain. Useful for understanding which site sections get the most traffic and how users navigate the site.

---

## Endpoint

```
GET https://api.semrush.com/analytics/ta/api/v3/subfolders
```

---

## Request Parameters

| Parameter | Required | Description |
|-----------|----------|-------------|
| `key` | Yes | Your API key (from Subscription info → API Units) |
| `target` | Yes | Root domain or subdomain (e.g. `example.com`, `subdomain.example.com`) |
| `target_type` | No | `domain` (default) or `subdomain` |
| `display_date` | No | Month in `YYYY-MM-01` format. Defaults to previous month. Min: `2017-01-01`. Max: start of previous month. |
| `device_type` | No | `desktop` only. |
| `display_limit` | No | Results per request. Default: `1000`. Max: `5000`. |
| `display_offset` | No | Results to skip for pagination. Default: `0`. No maximum. |
| `country` | No | ISO 3166-1 Alpha-2 country code. Defaults to global data. |
| `search_string` | No | Filter results to subfolders whose path contains this string. |
| `sort_order` | No | Sort field + direction. Append `_desc` (default) or `_asc`. See sortable columns below. |
| `export_columns` | No | Comma-separated columns to return. Defaults to all columns. |

### Sortable Columns

`traffic_share`, `unique_pageviews`, `users`, `entrances`, `exits`, `time_on_subfolder`, `pages_per_visit`, `bounce_rate`, `direct`, `referral`, `search_organic`, `search_paid`, `social_organic`, `social_paid`, `mail`, `display_ad`, `ai_assistants`, `ai_search`

---

## Export Columns

| Column | Description |
|--------|-------------|
| `display_date` | Month of the data |
| `subfolder` | The subfolder path |
| `subdomain` | The subdomain the subfolder belongs to |
| `traffic_share` | Share of total domain traffic going to this subfolder |
| `users` | Unique visitors |
| `unique_pageviews` | Unique pageviews |
| `entrances` | Sessions that started on this subfolder |
| `exits` | Sessions that ended on this subfolder |
| `time_on_subfolder` | Average time spent in this subfolder |
| `pages_per_visit` | Pages per visit |
| `bounce_rate` | Bounce rate |
| `direct` | Direct traffic |
| `referral` | Referral traffic |
| `search_organic` | Organic search traffic |
| `search_paid` | Paid search traffic |
| `social_organic` | Organic social traffic |
| `social_paid` | Paid social traffic |
| `mail` | Email traffic |
| `display_ad` | Display ad traffic |
| `ai_assistants` | Traffic from AI assistants |
| `ai_search` | Traffic from AI search engines |
| `search` | ⚠️ Deprecated |
| `social` | ⚠️ Deprecated |
| `paid` | ⚠️ Deprecated |

---

## Request Example

```
https://api.semrush.com/analytics/ta/api/v3/subfolders?target=amazon.com&target_type=domain&display_limit=5&sort_order=unique_pageviews_desc&export_columns=users,unique_pageviews,entrances,exits&key=YOUR_API_KEY
```

## Response Example (CSV)

```
users;unique_pageviews;entrances;exits
108034494;442718812;139391428;214631237
117317596;400357027;88809293;119252855
57876899;181880099;26825058;41811998
59238134;160586116;27531044;30810362
46792998;150398115;21906685;36809256
```
