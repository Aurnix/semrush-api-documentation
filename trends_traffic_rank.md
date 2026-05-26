# Trends API — Traffic Rank

**Cost:** 1 API unit per request  
**Billing note:** Units are charged even if the response is empty.

Returns a list of domains sorted by traffic in descending order. Useful for benchmarking your site against competitors and understanding relative market position.

---

## Endpoint

```
GET https://api.semrush.com/analytics/ta/api/v3/rank
```

---

## Request Parameters

| Parameter | Required | Description |
|-----------|----------|-------------|
| `key` | Yes | Your API key (from Subscription info → API Units) |
| `display_date` | No | Month in `YYYY-MM-01` format. Defaults to previous month. Min: `2017-01-01`. Max: start of previous month. |
| `device_type` | No | `desktop` or `mobile`. Defaults to all devices. |
| `display_limit` | No | Results per request. Default: `200`. Max: `200`. |
| `display_offset` | No | Results to skip for pagination. Default: `0`. No maximum. |
| `country` | No | ISO 3166-1 Alpha-2 country code. Defaults to global data. |
| `export_columns` | No | Comma-separated columns to return. Defaults to all columns. |

---

## Export Columns

| Column | Description |
|--------|-------------|
| `rank` | Traffic rank position |
| `domain` | Domain name |
| `display_date` | Month of the data |
| `country` | Country filter used |
| `device_type` | Device type filter used |
| `visits` | Total visits |
| `users` | Unique visitors |
| `desktop_visits` | Desktop visits |
| `mobile_visits` | Mobile visits |
| `desktop_share` | Share of desktop traffic |
| `mobile_share` | Share of mobile traffic |
| `time_on_site` | Average visit duration |
| `bounce_rate` | Bounce rate |
| `pages_per_visit` | Pages per visit |

---

## Request Example

```
https://api.semrush.com/analytics/ta/api/v3/rank?device_type=mobile&display_date=2020-05-01&country=us&display_limit=5&display_offset=0&export_columns=rank,domain&key=YOUR_API_KEY
```

## Response Example (CSV)

```
rank;domain
1;google.com
2;facebook.com
3;wikipedia.org
4;amazon.com
5;yahoo.com
```
