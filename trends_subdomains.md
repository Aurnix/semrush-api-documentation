# Trends API — Subdomains

**Cost:** 1 API unit per request  
**Billing note:** Units are charged even if the response is empty.

Returns traffic data for the top subdomains of a selected website. Useful for identifying the most popular sections of a domain.

---

## Endpoint

```
GET https://api.semrush.com/analytics/ta/api/v3/subdomains
```

---

## Request Parameters

| Parameter | Required | Description |
|-----------|----------|-------------|
| `key` | Yes | Your API key (from Subscription info → API Units) |
| `target` | Yes | Root domain or subdomain (e.g. `example.com`, `subdomain.example.com`) |
| `target_type` | No | `domain` (default) or `subdomain` |
| `display_date` | No | Month in `YYYY-MM-01` format. Defaults to previous month. Min: `2017-01-01`. Max: start of previous month. |
| `device_type` | No | `desktop` or `mobile`. Defaults to all devices. |
| `display_limit` | No | Results per request. Default: `1000`. Max: `5000`. |
| `display_offset` | No | Results to skip for pagination. Default: `0`. No maximum. |
| `country` | No | ISO 3166-1 Alpha-2 country code. Defaults to global data. |
| `sort_order` | No | Sort field + direction. Append `_desc` (default) or `_asc`. Options: `traffic`, `desktop_share`, `mobile_share`. |
| `export_columns` | No | Comma-separated columns to return. Defaults to all columns except `target_type`. |

---

## Export Columns

| Column | Description |
|--------|-------------|
| `domain` | The root domain analyzed |
| `subdomain` | The subdomain |
| `display_date` | Month of the data |
| `country` | Country filter used |
| `device_type` | Device type filter used |
| `target_type` | Type of target (`domain` or `subdomain`); excluded from default output |
| `traffic_share` | Share of total domain traffic going to this subdomain (decimal) |
| `desktop_share` | Share of desktop traffic |
| `mobile_share` | Share of mobile traffic |
| `total_visits` | Total visits to the subdomain |
| `desktop_visits` | Desktop visits |
| `mobile_visits` | Mobile visits |
| `total_users` | Unique visitors |
| `desktop_users` | Unique desktop visitors |
| `mobile_users` | Unique mobile visitors |
| `total_hits` | Total hits |
| `desktop_hits` | Desktop hits |
| `mobile_hits` | Mobile hits |

---

## Request Example

```
https://api.semrush.com/analytics/ta/api/v3/subdomains?target=amazon.com&export_columns=domain,display_date,subdomain&country=us&display_date=2019-07-01&device_type=desktop&display_limit=3&display_offset=3&key=YOUR_API_KEY
```

## Response Example (CSV)

```
domain;display_date;subdomain
amazon.com;2019-07-01;twitch.amazon.com
amazon.com;2019-07-01;sellercentral.amazon.com
amazon.com;2019-07-01;aws.amazon.com
```
