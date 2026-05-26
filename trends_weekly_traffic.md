# Trends API — Weekly Traffic

**Cost:** 1 API unit per request  
**Billing note:** Empty responses are not charged.

Provides a week-by-week breakdown of traffic for a selected domain. Useful for comparing week-over-week performance and identifying broader trends.

---

## Endpoint

```
GET https://api.semrush.com/analytics/ta/api/v3/summary_by_week
```

---

## Request Parameters

| Parameter | Required | Description |
|-----------|----------|-------------|
| `key` | Yes | Your API key (from Subscription info → API Units) |
| `target` | Yes | Root domain. Use `target_type` for subdomains or subfolders. |
| `display_date` | No | Month in `YYYY-MM-01` format. Defaults to previous month. Min: `2017-01-01`. Max: start of current month. |
| `target_type` | No | `domain` (default), `subdomain`, or `subfolder` |
| `device_type` | No | `desktop` or `mobile`. Defaults to all devices. |
| `country` | No | ISO 3166-1 Alpha-2 country code. Defaults to global data. |
| `include_forecasted_items` | No | `true` or `false` (default). When `true`, includes forecasted data for the next 4 weeks. Requires `display_date` set to the current month. |
| `export_columns` | No | Comma-separated columns to return. Defaults to all columns. |

---

## Export Columns

| Column | Description |
|--------|-------------|
| `display_date` | Start date of the week |
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
https://api.semrush.com/analytics/ta/api/v3/summary_by_week?key=YOUR_API_KEY&target=amazon.com
```

## Response Example (CSV)

```
display_date;country;device_type;target;rank;visits;users;hits;direct;search_organic;search_paid;social_organic;social_paid;referral;mail;display_ad;ai_assistants;ai_search;time_on_site;pages_per_visit;bounce_rate;desktop_share;mobile_share;is_forecasted
2025-08-25;GLOBAL;all;amazon.com;0;620227136;235565992;4220426790;464959224;91541309;546726;11802993;235502;46480533;3839504;159020;651043;11282;698;6.8046;0.416;0.43777211;0.56222789;false
2025-08-18;GLOBAL;all;amazon.com;0;615692483;231541315;4277798665;458712363;91473395;733284;11689206;194778;47810011;4252092;179953;638025;9376;709;6.9479;0.4084;0.45154267;0.54845733;false
2025-08-11;GLOBAL;all;amazon.com;0;603448377;225920810;4237659278;449648534;90470820;641958;11620293;200268;45880514;4077303;280660;614766;13261;723;7.0224;0.4128;0.45383129;0.54616871;false
2025-08-04;GLOBAL;all;amazon.com;0;631590511;240102236;4258167362;470748382;95874454;631379;11841015;193475;47390538;4043741;220060;632018;15449;718;6.742;0.4193;0.44188288;0.55811712;false
2025-07-28;GLOBAL;all;amazon.com;0;616725385;233061869;4165117586;460257172;92896328;597006;11644068;188534;46298996;4080618;81847;668804;12012;713;6.7536;0.417;0.44343993;0.55656007;false
```

*Response includes one row per week. `display_date` reflects the Monday (start) of each week.*
