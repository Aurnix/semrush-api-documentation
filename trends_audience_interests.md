# Trends API — Audience Interests

**Cost:** 1 API unit per request  
**Billing note:** Units are charged even if the response is empty.

Returns interest category data for a domain's audience. Useful for tailoring content and marketing strategies to match audience preferences.

---

## Endpoint

```
GET https://api.semrush.com/analytics/ta/api/v3/audience_interests
```

---

## Request Parameters

| Parameter | Required | Description |
|-----------|----------|-------------|
| `key` | Yes | Your API key (from Subscription info → API Units) |
| `target` | Yes | Root domain (e.g. `example.com`) |
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
| `category` | Interest category name (e.g. `online_services`, `retail`, `entertainment`) |
| `users` | Estimated number of visitors with this interest |
| `users_score` | Affinity score — share of the domain's audience with this interest (decimal, 0–1) |

---

## Request Example

```
https://api.semrush.com/analytics/ta/api/v3/audience_interests?target=amazon.com&export_columns=category,users,users_score&key=YOUR_API_KEY
```

## Response Example (CSV)

```
category;users;users_score
online_services;921033121;0.9867154258825707
mass_media;917265402;0.9826790167970272
publishing;887132366;0.9503970816831272
newspapers;814880850;0.8729930407695959
retail;772807972;0.8279197890185599
computer_software_and_development;698535570;0.7483507451917946
entertainment;658906903;0.7058960102376283
information_technology;653199899;0.6997820185103172
```
