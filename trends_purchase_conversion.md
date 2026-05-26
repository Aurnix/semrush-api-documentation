# Trends API — Purchase Conversion

**Cost:** 1 API unit per request  
**Billing note:** Units are charged even if the response is empty.

Provides monthly conversion metrics for a domain, showing the percentage of sessions that ended in a purchase. Useful for benchmarking purchase conversion rates across markets, prospects, or partners.

---

## Endpoint

```
GET https://api.semrush.com/analytics/ta/api/v3/purchase_conversion
```

---

## Request Parameters

| Parameter | Required | Description |
|-----------|----------|-------------|
| `key` | Yes | Your API key (from Subscription info → API Units) |
| `target` | Yes | Root domain (e.g. `example.com`) |
| `device_type` | Yes | Device type. Currently only `desktop` is supported. |
| `display_date` | No | Month in `YYYY-MM-01` format. Defaults to previous month. Min: `2017-01-01`. Max: start of current month. |
| `country` | No | ISO 3166-1 Alpha-2 country code. Defaults to global data. |
| `export_columns` | No | Comma-separated columns to return. Defaults to all columns. |

---

## Export Columns

| Column | Description |
|--------|-------------|
| `target` | The queried domain |
| `display_date` | Month of the data |
| `country` | Country filter used |
| `device_type` | Device type filter used |
| `conversion` | Share of sessions ending in a purchase (decimal, e.g. `0.043` = 4.3%) |

---

## Request Example

```
https://api.semrush.com/analytics/ta/api/v3/purchase_conversion?key=YOUR_API_KEY&target=amazon.com&device_type=desktop
```

## Response Example (CSV)

```
target;display_date;device_type;country;conversion
amazon.com;2024-06-01;desktop;GLOBAL;0.04269275
```
