# Trends API — Daily Traffic

**Cost:** 1 API unit per request  
**Billing note:** Empty responses are not charged.

Provides a day-by-day breakdown of traffic for a selected domain. Useful for monitoring daily fluctuations, identifying trends, and responding to changes in user behavior.

---

## Endpoint

```
GET https://api.semrush.com/analytics/ta/api/v3/summary_by_day
```

---

## Request Parameters

| Parameter | Required | Description |
|-----------|----------|-------------|
| `key` | Yes | Your API key (from Subscription info → API Units) |
| `target` | Yes | Root domain. Use `target_type` for subdomains or subfolders. |
| `display_date` | No | Month in `YYYY-MM-01` format. Defaults to previous month. Min: `2017-01-01`. Max: start of current month (e.g. `2024-06-01` if today is June 19, 2024). |
| `target_type` | No | `domain` (default), `subdomain`, or `subfolder` |
| `device_type` | No | `desktop` or `mobile`. Defaults to all devices. |
| `country` | No | ISO 3166-1 Alpha-2 country code. Defaults to global data. |
| `include_forecasted_items` | No | `true` or `false` (default). When `true`, includes forecasted data for the next 4 weeks. Requires `display_date` set to the current month. |
| `export_columns` | No | Comma-separated columns to return. Defaults to all columns. |

---

## Export Columns

| Column | Description |
|--------|-------------|
| `display_date` | Date of the data point |
| `country` | Country filter used |
| `device_type` | Device type filter used |
| `target` | The queried domain/subdomain/subfolder |
| `rank` | Traffic rank |
| `visits` | Total visits |
| `users` | Unique visitors |
| `hits` | Total hits |
| `direct` | Direct traffic |
| `search_organic` | Organic search traffic |
| `search_paid` | Paid search traffic |
| `social_organic` | Organic social traffic |
| `social_paid` | Paid social traffic |
| `referral` | Referral traffic |
| `mail` | Email traffic |
| `display_ad` | Display advertising traffic |
| `ai_assistants` | Traffic from AI assistants (e.g. ChatGPT, Copilot) |
| `ai_search` | Traffic from AI search engines (e.g. Gemini) |
| `time_on_site` | Average visit duration |
| `pages_per_visit` | Pages per visit |
| `bounce_rate` | Bounce rate |
| `desktop_share` | Share of desktop traffic |
| `mobile_share` | Share of mobile traffic |
| `is_forecasted` | Whether the row is a forecasted value (`true`/`false`) |

---

## Request Example

```
https://api.semrush.com/analytics/ta/api/v3/summary_by_day?key=YOUR_API_KEY&target=amazon.com
```

## Response Example (CSV)

```
display_date;country;device_type;target;rank;visits;users;hits;direct;search_organic;search_paid;social_organic;social_paid;referral;mail;display_ad;ai_assistants;ai_search;time_on_site;pages_per_visit;bounce_rate;desktop_share;mobile_share;is_forecasted
2025-08-31;GLOBAL;all;amazon.com;0;81503642;55980389;531755802;60439536;12542552;98247;1616270;20466;6151430;517794;33213;80826;3308;678;6.5243;0.4349;0.38861737;0.61138263;false
2025-08-30;GLOBAL;all;amazon.com;0;83479974;56721688;578403597;62383146;12662038;52476;1556629;25431;6278725;413136;25319;82365;709;687;6.9287;0.424;0.39057638;0.60942362;false
2025-08-29;GLOBAL;all;amazon.com;0;89151759;59685027;613598166;67227562;12724719;82402;1503120;25512;6907341;575260;4171;99601;2071;712;6.8826;0.4149;0.44174532;0.55825468;false
```

*Response includes one row per day for the requested month.*
