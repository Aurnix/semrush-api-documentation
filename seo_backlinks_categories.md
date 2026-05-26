# SEO API — Categories

**Price:** 50 API units per request

Returns the categories that the queried domain itself belongs to, with a confidence rating per category. Results are sorted by rating descending.

## Endpoint

```
GET https://api.semrush.com/analytics/v1/
```

## Parameters

| Parameter | Required | Description |
|---|---|---|
| `type` | Yes | Report type. Value: `backlinks_categories` |
| `key` | Yes | API key from Subscription info > API units. |
| `target` | Yes | Root domain, subdomain, or URL to investigate. Example: `example.com`, `www.example.com`, or `http://www.example.com` |
| `target_type` | Yes | Type of target. Values: `root_domain`, `subdomain`, `url`. Note: use `subdomain` (not `domain`) for subdomains — differs from most other backlink endpoints. |
| `export_columns` | Yes | Comma-separated columns to return. Defaults to all columns. Values: `category_name`, `rating` |

## Export Columns

| Column | Description |
|---|---|
| `category_name` | Category name, 1–3 levels separated by `/`. Example: `/Internet & Telecom/Web Services/Search Engine Optimization & Marketing` |
| `rating` | Confidence that the queried domain belongs to this category. Values: `0–1` (closer to `1` = higher confidence). |

## Notes

- Unlike [Categories Profile](seo_backlinks_categories_profile.md), which counts referring domains per category, `rating` here is a true confidence score.
- No pagination parameters — returns all matching categories in a single request.
- `target_type` accepts `subdomain` instead of `domain` used by most other backlink endpoints.

## Example Request

```
https://api.semrush.com/analytics/v1/?key=YOUR_API_KEY&type=backlinks_categories&target=searchenginejournal.com&target_type=root_domain&export_columns=category_name,rating
```

## Example Response

```
category_name;rating
/Internet & Telecom/Web Services/Search Engine Optimization & Marketing;0.931905
/Internet & Telecom/Web Services/Affiliate Programs;0.880989
/Business & Industrial/Advertising & Marketing/Marketing;0.872495
/Internet & Telecom/Search Engines;0.821398
/Business & Industrial/Advertising & Marketing/Brand Management;0.813207
```
