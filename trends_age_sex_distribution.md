# Trends API — Age and Sex Distribution

**Cost:** 1 API unit per request  
**Billing note:** Units are charged even if the response is empty.

Returns age and sex distribution data for a domain's audience. Useful for understanding market demographics and improving targeting and segmentation.

---

## Endpoint

```
GET https://api.semrush.com/analytics/ta/api/v3/age_and_sex_distribution
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

> **Note:** Historical data for this endpoint starts at `2020-04-01` (later than most other Trends API endpoints which start at `2017-01-01`).

---

## Export Columns

| Column | Description |
|--------|-------------|
| `target` | The analyzed domain |
| `display_date` | Month of the data |
| `country` | Country filter used |
| `device_type` | Device type filter used |
| `age` | Age band (e.g. `18-24`, `25-34`, `35-44`, `45-54`, `55-64`, `65+`) |
| `female_users` | Estimated number of female visitors in this age band |
| `male_users` | Estimated number of male visitors in this age band |
| `female_share` | Female visitors as a share of total audience (decimal) |
| `male_share` | Male visitors as a share of total audience (decimal) |

---

## Request Example

```
https://api.semrush.com/analytics/ta/api/v3/age_and_sex_distribution?target=amazon.com&export_columns=age,female_users,male_users,female_share,male_share&key=YOUR_API_KEY
```

## Response Example (CSV)

```
age;female_users;male_users;female_share;male_share
18-24;44327990;97168741;0.04749;0.1041
25-34;122735052;269057548;0.13149;0.28825
35-44;73095910;160239759;0.07831;0.17167
45-54;36337936;79667169;0.03893;0.08535
55-64;12013080;26341037;0.01287;0.02822
65+;3892350;8531434;0.00417;0.00914
```
