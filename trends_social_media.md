# Trends API — Social Media

**Cost:** 1 API unit per request  
**Billing note:** Units are charged even if the response is empty.

Returns social media platform preferences for a domain's audience. Shows which platforms the audience uses and how heavily, useful for optimizing social media strategy.

---

## Endpoint

```
GET https://api.semrush.com/analytics/ta/api/v3/social_media
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
| `social_name` | Social platform name (e.g. `YouTube`, `Facebook`) |
| `social_domain` | Domain of the social platform (e.g. `youtube.com`) |
| `users` | Estimated number of the domain's visitors who also use this platform |
| `users_score` | Affinity score — share of the domain's audience using this platform (decimal, 0–1) |

---

## Request Example

```
https://api.semrush.com/analytics/ta/api/v3/social_media?target=amazon.com&export_columns=social_name,social_domain,users_score,users&key=YOUR_API_KEY
```

## Response Example (CSV)

```
social_name;social_domain;users_score;users
YouTube;youtube.com;0.7474810387808435;697723757
Facebook;facebook.com;0.44912889370340137;419231904
Twitter;twitter.com;0.3635169623127236;339318869
Reddit;reddit.com;0.36153091057319436;337465022
Instagram;instagram.com;0.2945165976739555;274911625
TikTok;tiktok.com;0.20150881125651102;188095052
LinkedIn;linkedin.com;0.1261642745655982;117765946
Pinterest;pinterest.com;0.1086957264671911;101460220
```
