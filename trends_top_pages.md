# Trends API — Top Pages

**Cost:** 1 API unit per request  
**Billing note:** Units are charged even if the response is empty.

Returns the most popular pages for a domain, subdomain, or subfolder. Useful for understanding which content resonates most with an audience.

---

## Endpoint

```
GET https://api.semrush.com/analytics/ta/api/v3/toppages
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
| `country` | No | ISO 3166-1 Alpha-2 country code. Defaults to global data. |
| `sort_order` | No | Sort field + direction. Append `_desc` (default) or `_asc`. Options: `users_by_target`, `avg_visit_duration`, `exits`, `traffic`, `entrance_traffic`, `traffic_share`. |
| `export_columns` | No | Comma-separated columns to return. Defaults to all columns. |

---

## Export Columns

| Column | Description |
|--------|-------------|
| `target` | The analyzed domain/subdomain/subfolder |
| `page` | The specific page URL |
| `display_date` | Month of the data |
| `country` | Country filter used |
| `device_type` | Device type filter used |
| `traffic` | Estimated visits to the page |
| `traffic_share` | Share of domain traffic going to this page (decimal) |
| `desktop_share` | Share of desktop traffic |
| `mobile_share` | Share of mobile traffic |
| `users_by_target` | Unique visitors to the page |
| `avg_visit_duration` | Average time spent on the page |
| `exits` | Number of exits from this page |
| `entrance_traffic` | Traffic entering the site via this page |
| `direct` | Direct traffic to this page |
| `referral` | Referral traffic to this page |
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
| `unknown` | ⚠️ Deprecated |

---

## Request Example

```
https://api.semrush.com/analytics/ta/api/v3/toppages?device_type=desktop&display_date=2020-06-01&country=us&display_limit=5&display_offset=0&target=amazon.com&target_type=domain&export_columns=page,display_date,desktop_share,mobile_share&key=YOUR_API_KEY
```

## Response Example (CSV)

```
page;display_date;desktop_share;mobile_share
amazon.com/s;2020-06-01;1;0
amazon.com;2020-06-01;0.2545288066748602;0.7454711933251398
amazon.com/gp/css/order-history;2020-06-01;1;0
amazon.com/s/ref=nb_sb_noss_2;2020-06-01;1;0
amazon.com/gp/product/handle-buy-box/ref=dp_start-bbf_1_glance;2020-06-01;1;0
```
