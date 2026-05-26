# Trends API — Traffic Summary

**Cost:** 1 API unit per line  
**Billing note:** Empty responses are not charged. For multi-target requests, you are only charged for domains that return data.

Provides estimated traffic metrics for one or more domains, subdomains, or subfolders. Metrics include traffic rank, visits, unique visitors, pages per visit, average visit duration, and bounce rate.

---

## Endpoint

```
GET https://api.semrush.com/analytics/ta/api/v3/summary
```

---

## Request Parameters

| Parameter | Required | Description |
|-----------|----------|-------------|
| `key` | Yes | Your API key (from Subscription info → API Units) |
| `targets` | Yes | Comma-separated list of domains, subdomains, or subfolders. Max 200 targets. |
| `display_date` | No | Month in `YYYY-MM-01` format. Defaults to previous month. Min: `2017-01-01`. Max: start of previous month. |
| `device_type` | No | `desktop` or `mobile`. Defaults to all devices. |
| `country` | No | ISO 3166-1 Alpha-2 country code. Defaults to global data. |
| `export_columns` | No | Comma-separated list of columns to return. See columns table below. Defaults to: `target, rank, visits, desktop_visits, mobile_visits, users, desktop_users, mobile_users`. |

---

## Export Columns

| Column | Description |
|--------|-------------|
| `target` | The queried domain/subdomain/subfolder |
| `rank` | Traffic rank |
| `visits` | Total visits |
| `desktop_visits` | Desktop visits |
| `mobile_visits` | Mobile visits |
| `users` | Unique visitors |
| `desktop_users` | Unique desktop visitors |
| `mobile_users` | Unique mobile visitors |
| `categories` | Industry categories |
| `direct` | Direct traffic share |
| `referral` | Referral traffic share |
| `social` | Total social traffic share |
| `search` | Total search traffic share |
| `paid` | Total paid traffic share |
| `search_organic` | Organic search traffic share |
| `search_paid` | Paid search traffic share |
| `social_organic` | Organic social traffic share |
| `social_paid` | Paid social traffic share |
| `mail` | Email traffic share |
| `display_ad` | Display advertising traffic share |
| `ai_assistants` | Traffic from AI assistants (e.g. ChatGPT, Copilot) |
| `ai_search` | Traffic from AI search engines (e.g. Gemini) |
| `unknown_channel` | Traffic from unknown channels |
| `time_on_site` | Average visit duration (all devices) |
| `desktop_time_on_site` | Average visit duration (desktop) |
| `mobile_time_on_site` | Average visit duration (mobile) |
| `pages_per_visit` | Pages per visit (all devices) |
| `desktop_pages_per_visit` | Pages per visit (desktop) |
| `mobile_pages_per_visit` | Pages per visit (mobile) |
| `bounce_rate` | Bounce rate (all devices) |
| `desktop_bounce_rate` | Bounce rate (desktop) |
| `mobile_bounce_rate` | Bounce rate (mobile) |
| `desktop_share` | Share of desktop traffic |
| `mobile_share` | Share of mobile traffic |
| `accuracy` | Data accuracy indicator |
| `display_date` | Date of the data |
| `country` | Country filter used |
| `device_type` | Device type filter used |
| `desktop_hits` | Desktop hits |
| `mobile_hits` | Mobile hits |

---

## Request Example

```
https://api.semrush.com/analytics/ta/api/v3/summary?targets=golang.org,blog.golang.org,tour.golang.org/welcome/&export_columns=target,visits,users&key=YOUR_API_KEY
```

## Response Example (CSV)

```
target;visits;users
golang.org;4491179;1400453
blog.golang.org;402104;204891
tour.golang.org/welcome/;10131;11628
```
