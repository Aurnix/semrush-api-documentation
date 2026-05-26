# Trends API — Education Distribution

**Cost:** 1 API unit per request  
**Billing note:** Units are charged even if the response is empty.

Returns audience distribution by education level for a domain. Useful for tailoring content and marketing strategies to match the educational background of an audience.

---

## Endpoint

```
GET https://api.semrush.com/analytics/ta/api/v3/education_distribution
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
| `education` | Education level: `none_completed`, `school`, `university`, or `postgraduate` |
| `users` | Estimated number of visitors at this education level |
| `users_share` | Share of total audience at this education level (decimal) |

---

## Request Example

```
https://api.semrush.com/analytics/ta/api/v3/education_distribution?target=amazon.com&export_columns=education,users,users_share&key=YOUR_API_KEY
```

## Response Example (CSV)

```
education;users;users_share
none_completed;31115401;0.03333493
school;467949632;0.5013295
university;383657211;0.4110243
postgraduate;50695096;0.054311287
```
