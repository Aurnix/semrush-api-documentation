# SEO API — TLD Distribution

**Price:** 40 API units per line

Shows referring domain distribution by top-level domain (TLD) type.

## Endpoint

```
GET https://api.semrush.com/analytics/v1/
```

## Parameters

| Parameter | Required | Description |
|---|---|---|
| `type` | Yes | Report type. Value: `backlinks_tld` |
| `key` | Yes | API key from Subscription info > API units. |
| `target` | Yes | Root domain, subdomain, or URL to investigate. Example: `example.com`, `www.example.com`, or `http://www.example.com` |
| `target_type` | Yes | Type of target. Values: `root_domain`, `domain` (use for subdomains), `url` |
| `export_columns` | Yes | Comma-separated columns to return. Defaults to all columns. Values: `zone`, `domains_num`, `backlinks_num` |
| `display_sort` | No | Column to sort by. Default: `domains_num_desc`. Values: `domains_num_asc`, `domains_num_desc`, `backlinks_num_asc`, `backlinks_num_desc` |
| `display_limit` | No | Number of results to return. Default and value of `0`: 10,000. |
| `display_offset` | No | Number of results to skip before returning data. If used, increase `display_limit` by the offset value. |

## Export Columns

| Column | Description |
|---|---|
| `zone` | TLD zone (e.g., `com`, `net`, `org`, `uk`). |
| `domains_num` | Number of referring domains with this TLD. |
| `backlinks_num` | Number of backlinks from domains with this TLD. |

## Example Request

```
https://api.semrush.com/analytics/v1/?key=YOUR_API_KEY&type=backlinks_tld&target=searchenginejournal.com&target_type=root_domain&export_columns=zone,domains_num,backlinks_num&display_limit=5
```

## Example Response

```
zone;domains_num;backlinks_num
com;27755;11645051
net;1894;1684571
org;1486;800180
uk;1267;22572
au;645;9531
```
