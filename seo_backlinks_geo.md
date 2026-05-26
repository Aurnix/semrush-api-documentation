# SEO API — Referring Domains by Country

**Price:** 40 API units per line

Shows referring domain distribution by country. Country is determined by the domain's IP address.

## Endpoint

```
GET https://api.semrush.com/analytics/v1/
```

## Parameters

| Parameter | Required | Description |
|---|---|---|
| `type` | Yes | Report type. Value: `backlinks_geo` |
| `key` | Yes | API key from Subscription info > API units. |
| `target` | Yes | Root domain, subdomain, or URL to investigate. Example: `example.com`, `www.example.com`, or `http://www.example.com` |
| `target_type` | Yes | Type of target. Values: `root_domain`, `domain` (use for subdomains), `url` |
| `export_columns` | Yes | Comma-separated columns to return. Defaults to all columns. Values: `country`, `domains_num`, `backlinks_num` |
| `display_sort` | No | Column to sort by. Default: `domains_num_desc`. Values: `domains_num_asc`, `domains_num_desc`, `backlinks_num_asc`, `backlinks_num_desc` |
| `display_limit` | No | Number of results to return. Default and value of `0`: 10,000. |
| `display_offset` | No | Number of results to skip before returning data. If used, increase `display_limit` by the offset value. |

## Export Columns

| Column | Description |
|---|---|
| `country` | Country name associated with the referring domain's IP address. |
| `domains_num` | Number of referring domains from this country. |
| `backlinks_num` | Number of backlinks from domains in this country. |

## Example Request

```
https://api.semrush.com/analytics/v1/?key=YOUR_API_KEY&type=backlinks_geo&target=searchenginejournal.com&target_type=root_domain&export_columns=country,domains_num,backlinks_num&display_limit=5
```

## Example Response

```
country;domains_num;backlinks_num
United States;36489;5463278
Germany;2594;149154
United Kingdom;1750;102385
France;917;99323
Canada;791;695950
```
