# Trends API — Occupation Distribution

**Cost:** 1 API unit per request  
**Billing note:** Units are charged even if the response is empty.

Returns audience distribution by occupation for a domain. Useful for understanding the professional makeup of an audience and targeting specific professional groups.

---

## Endpoint

```
GET https://api.semrush.com/analytics/ta/api/v3/occupation_distribution
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
| `occupation` | Occupation category (see values below) |
| `users` | Estimated number of visitors in this occupation group |
| `users_share` | Share of total audience in this occupation group (decimal) |

### Occupation Values

| Value | Description |
|-------|-------------|
| `full_time_work` | Employed full-time |
| `part_time_work` | Employed part-time |
| `own_business` | Self-employed / business owner |
| `homemaker` | Homemaker |
| `studies` | Student |
| `unemployed` | Unemployed |
| `retired` | Retired |
| `leave_of_absence` | On leave of absence |
| `parental_leave` | On parental leave |

---

## Request Example

```
https://api.semrush.com/analytics/ta/api/v3/occupation_distribution?target=amazon.com&export_columns=occupation,users,users_share&key=YOUR_API_KEY
```

## Response Example (CSV)

```
occupation;users;users_share
unemployed;142362045;0.15251704
parental_leave;4634344;0.0049649226
leave_of_absence;12847917;0.013764387
studies;65785665;0.0704783
part_time_work;110365158;0.11823774
full_time_work;398638431;0.42707416
homemaker;99072807;0.10613988
own_business;46837581;0.050178606
retired;52873389;0.05664496
```
