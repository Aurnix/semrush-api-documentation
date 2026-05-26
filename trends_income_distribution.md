# Trends API — Income Distribution

**Cost:** 1 API unit per request  
**Billing note:** Units are charged even if the response is empty.

Returns audience distribution by income level for a domain. Useful for understanding socioeconomic diversity and tailoring messaging, promotions, and offers.

---

## Endpoint

```
GET https://api.semrush.com/analytics/ta/api/v3/income_distribution
```

---

## Request Parameters

| Parameter | Required | Description |
|-----------|----------|-------------|
| `key` | Yes | Your API key (from Subscription info → API Units) |
| `target` | Yes | Root domain or subdomain (e.g. `example.com`, `subdomain.example.com`) |
| `display_date` | No | Month in `YYYY-MM-01` format. Defaults to previous month. Min: `2020-04-01`. Max: start of previous month. |
| `device_type` | No | `desktop` or `mobile`. Defaults to all devices. |
| `country` | No | ISO 3166-1 Alpha-2 country code. Defaults to global data. |
| `export_columns` | No | Comma-separated columns to return. Defaults to all columns. |

> **Note:** Historical data starts at `2020-04-01`.

---

## Export Columns

| Column | Description |
|--------|-------------|
| `target` | The analyzed domain |
| `display_date` | Month of the data |
| `country` | Country filter used |
| `device_type` | Device type filter used |
| `income_type` | Income level: `high`, `middle`, or `low` |
| `users` | Estimated number of visitors in this income group |
| `users_share` | Share of total audience in this income group (decimal) |

---

## Request Example

```
https://api.semrush.com/analytics/ta/api/v3/income_distribution?target=amazon.com&export_columns=income_type,users,users_share&key=YOUR_API_KEY
```

## Response Example (CSV)

```
income_type;users;users_share
high;78982046;0.084616005
middle;236143146;0.25298774
low;618292149;0.66239625
```
