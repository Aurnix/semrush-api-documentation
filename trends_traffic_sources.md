# Trends API — Traffic Sources

**Cost:** 1 API unit per request  
**Billing note:** Units are charged even if the response is empty.

Analyzes traffic sources by channel for a domain, subdomain, or subfolder. Covers direct, referral, search, social, email, paid, display ad, and AI-driven traffic channels.

---

## Endpoint

```
GET https://api.semrush.com/analytics/ta/api/v3/sources
```

---

## Request Parameters

| Parameter | Required | Description |
|-----------|----------|-------------|
| `key` | Yes | Your API key (from Subscription info → API Units) |
| `target` | Yes | Root domain, subdomain, or subfolder (e.g. `example.com`, `sub.example.com`, `example.com/subfolder/`) |
| `display_date` | No | Month in `YYYY-MM-01` format. Defaults to previous month. Min: `2017-01-01`. Max: start of previous month. |
| `device_type` | No | `desktop` or `mobile`. Defaults to all devices. |
| `display_limit` | No | Results per request. Default: `1000`. Max: `5000`. |
| `display_offset` | No | Results to skip for pagination. Default: `0`. Max: `10000`. |
| `traffic_channel` | No | Filter by channel: `direct`, `referral`, `search`, `social`, `mail`, `display_ad`, `ai_assistants`, `ai_search`. Defaults to all channels. |
| `traffic_type` | No | `organic` or `paid`. Defaults to all types. |
| `sort_order` | No | Sort field + direction. Append `_desc` (default) or `_asc`. Options: `traffic`, `traffic_diff`, `traffic_share`. |
| `country` | No | ISO 3166-1 Alpha-2 country code. Defaults to global data. |
| `export_columns` | No | Comma-separated columns to return. Defaults to all columns. |

---

## Export Columns

| Column | Description |
|--------|-------------|
| `target` | The analyzed domain/subdomain/subfolder |
| `from_target` | The referring domain or source |
| `display_date` | Month of the data |
| `country` | Country filter used |
| `device_type` | Device type filter used |
| `channel` | Traffic channel (direct, referral, search, etc.) |
| `traffic_type` | organic or paid |
| `traffic` | Estimated visits from this source |
| `traffic_share` | Share of total traffic from this source (decimal) |
| `traffic_diff` | Change in traffic vs. prior period |
| `prev_traffic` | Traffic in the prior period |
| `search_engine` | Search engine (for search channel rows) |
| `categories` | Industry categories of the referring domain |

---

## Request Example

```
https://api.semrush.com/analytics/ta/api/v3/sources?target=medium.com&device_type=mobile&display_limit=5&display_offset=0&country=us&sort_order=traffic_diff&traffic_channel=referral&traffic_type=organic&display_date=2020-06-01&export_columns=target,from_target,display_date,country,traffic_share,traffic,channel&key=YOUR_API_KEY
```

## Response Example (CSV)

```
target;from_target;display_date;country;traffic_share;traffic;channel
medium.com;phlap.net;2020-06-01;US;0.00019134;7025;referral
medium.com;blackhatworld.com;2020-06-01;US;0.00006379;2342;referral
medium.com;crunchyroll.com;2020-06-01;US;0.00005102;1873;referral
medium.com;outline.com;2020-06-01;US;0.00005102;1873;referral
medium.com;uber.com;2020-06-01;US;0.00005102;1873;referral
```
