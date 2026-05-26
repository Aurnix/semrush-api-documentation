# SEO API — Categories Profile

**Price:** 40 API units per line

Returns the categories that the queried domain's referring domains belong to, along with the count of referring domains per category. Results are sorted by referring domain count descending. Based on the first 10,000 referring domains for the queried domain.

## Endpoint

```
GET https://api.semrush.com/analytics/v1/
```

## Parameters

| Parameter | Required | Description |
|---|---|---|
| `type` | Yes | Report type. Value: `backlinks_categories_profile` |
| `key` | Yes | API key from Subscription info > API units. |
| `target` | Yes | Root domain, subdomain, or URL to investigate. Example: `example.com`, `www.example.com`, or `http://www.example.com` |
| `target_type` | Yes | Type of target. Values: `root_domain`, `domain` (use for subdomains), `url` |
| `export_columns` | Yes | Comma-separated columns to return. Defaults to all columns. Values: `category_name`, `rating` |
| `display_limit` | No | Number of results to return. Default and value of `0`: 10,000. |
| `display_offset` | No | Number of results to skip before returning data. If used, increase `display_limit` by the offset value. |

## Export Columns

| Column | Description |
|---|---|
| `category_name` | Category name, 1–3 levels separated by `/`. Example: `/Internet & Telecom/Web Services/Web Design & Development` |
| `rating` | Number of referring domains in this category that have at least one backlink to the queried domain. Note: despite the column name, this is a count, not a confidence rating. |

## Example Request

```
https://api.semrush.com/analytics/v1/?key=YOUR_API_KEY&type=backlinks_categories_profile&target=searchenginejournal.com&target_type=root_domain&export_columns=category_name,rating&display_limit=5
```

## Example Response

```
category_name;rating
/Business & Industrial/Advertising & Marketing/Marketing;2188
/Internet & Telecom/Web Services/Search Engine Optimization & Marketing;1975
/Business & Industrial/Advertising & Marketing/Brand Management;1725
/Business & Industrial/Advertising & Marketing/Sales;1116
/Internet & Telecom/Web Services/Web Design & Development;1001
```
