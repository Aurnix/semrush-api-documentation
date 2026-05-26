# Trends API — Audience Insights

**Cost:** 1 API unit per request  
**Billing note:** Units are charged even if the response is empty.

Returns audience overlap data between selected domains. Shows which other domains the combined audience also visits. Useful for targeting, segmentation, and ad placement decisions.

Maps to the **Visited domains** section in the Audience Overlap dashboard.

---

## Endpoint

```
GET https://api.semrush.com/analytics/ta/api/v3/audience_insights
```

---

## Request Parameters

| Parameter | Required | Description |
|-----------|----------|-------------|
| `key` | Yes | Your API key (from Subscription info → API Units) |
| `targets` | Yes | Comma-separated list of domains to include in the analysis. Max 5 domains. |
| `selected_targets` | Yes | Comma-separated subset of `targets` domains to analyze. Max determined by `targets` count (up to 5). |
| `segment` | No | Defines how the audience is scoped (see Segment Values below). |
| `display_date` | No | Month in `YYYY-MM-01` format. Defaults to previous month. Min: `2017-01-01`. Max: start of previous month. |
| `device_type` | No | `desktop` or `mobile`. Defaults to all devices. |
| `display_limit` | No | Results per request. Default: `1000`. Max: `5000`. |
| `display_offset` | No | Results to skip for pagination. Default: `0`. No maximum. |
| `country` | No | ISO 3166-1 Alpha-2 country code. Defaults to global data. |
| `export_columns` | No | Comma-separated columns to return. Defaults to all columns. |

### Segment Values

| Value | Description |
|-------|-------------|
| `contains` | Unites the audience of all `selected_targets` (union) |
| `shares` | Audience who visited **all** of the `selected_targets` (intersection) |
| `excludes` | Audience who visited other `selected_targets` domains but **not** the excluded one |

---

## Export Columns

| Column | Description |
|--------|-------------|
| `target` | A domain that the audience segment also visits |
| `overlap_score` | Share of the segment's audience that also visits this domain (decimal) |
| `similarity_score` | Similarity index between the segment audience and this domain's audience (decimal) |
| `target_users` | Total unique visitors to this domain |
| `overlap_users` | Number of users in the segment who also visited this domain |
| `categories` | Industry categories of the domain |
| `is_adult` | Whether the domain is classified as adult content |

---

## Request Example

```
https://api.semrush.com/analytics/ta/api/v3/audience_insights?display_date=2020-02-01&device_type=desktop&country=us&segment=contains&targets=amazon.com,ebay.com,searchenginesland.com&selected_targets=amazon.com,ebay.com&export_columns=target,overlap_score,similarity_score,target_users,overlap_users&display_offset=5&display_limit=7&key=YOUR_API_KEY
```

## Response Example (CSV)

```
target;overlap_score;similarity_score;target_users;overlap_users
instagram.com;0.3688;0.4891;69429930;50399700
reddit.com;0.3467;0.4515;73201944;47379108
twitter.com;0.3467;0.4587;69915496;47372776
ebay.com;0.2448;0.3933;33448824;33448824
imdb.com;0.239;0.3621;43723270;32654776
apple.com;0.2326;0.3496;45222470;31789886
yahoo.com;0.2221;0.3242;50563124;30347980
```
