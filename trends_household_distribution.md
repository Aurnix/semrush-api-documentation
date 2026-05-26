# Trends API — Household Distribution

**Cost:** 1 API unit per request  
**Billing note:** Units are charged even if the response is empty.

Returns audience distribution by household size for a domain. Useful for understanding household demographics to improve segmentation and targeting.

---

## Endpoint

```
GET https://api.semrush.com/analytics/ta/api/v3/household_distribution
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
| `size` | Household size (values: `1`, `2`, `3`, `4`, `5`, `6`, `7`, `8`, `9`, `10+`) |
| `users` | Estimated number of visitors in this household size group |
| `users_share` | Share of total audience in this household size group (decimal) |

---

## Request Example

```
https://api.semrush.com/analytics/ta/api/v3/household_distribution?target=amazon.com&export_columns=size,users,users_share&key=YOUR_API_KEY
```

## Response Example (CSV)

```
size;users;users_share
1;119159479;0.12765938
2;216755165;0.23221678
3;196100018;0.21008825
4;188666644;0.20212464
5;111846800;0.11982507
6;55039594;0.058965687
7;23824865;0.025524344
8;11369735;0.012180763
9;5235293;0.0056087384
10+;5419740;0.005806342
```
