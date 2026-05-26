# Trends API — Data Accuracy

**Cost:** 1 API unit per request  
**Billing note:** Units are charged even if the response is empty.

Returns a metric indicating the accuracy of traffic data for a domain. Useful for assessing reliability before building strategies on the data.

---

## Endpoint

```
GET https://api.semrush.com/analytics/ta/api/v3/accuracy
```

---

## Request Parameters

| Parameter | Required | Description |
|-----------|----------|-------------|
| `key` | Yes | Your API key (from Subscription info → API Units) |
| `target` | Yes | Root domain (e.g. `domain.com`) |
| `display_date` | No | Month in `YYYY-MM-01` format. Defaults to previous month. Min: `2017-01-01`. Max: start of previous month. |
| `device_type` | No | `desktop` or `mobile`. Defaults to all devices. |
| `country` | No | ISO 3166-1 Alpha-2 country code. Defaults to global data. |
| `export_columns` | No | Comma-separated columns to return. Defaults to all columns. |

---

## Export Columns

| Column | Description |
|--------|-------------|
| `target` | The analyzed domain |
| `display_date` | Month of the data |
| `country` | Country filter used |
| `device_type` | Device type filter used |
| `accuracy` | Numeric accuracy score for the data |

---

## Request Example

```
https://api.semrush.com/analytics/ta/api/v3/accuracy?display_date=2019-01-01&target=ebay.com&country=us&device_type=desktop&export_columns=target,display_date,country,device_type,accuracy&key=YOUR_API_KEY
```

## Response Example (CSV)

```
target;display_date;country;device_type;accuracy
ebay.com;2019-01-01;US;desktop;3
```
