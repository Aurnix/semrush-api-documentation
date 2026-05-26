# SEO API — Referring IPs

**Price:** 40 API units per line

Lists IP addresses where backlinks to a domain, root domain, or URL are coming from.

## Endpoint

```
GET https://api.semrush.com/analytics/v1/
```

## Parameters

| Parameter | Required | Description |
|---|---|---|
| `type` | Yes | Report type. Value: `backlinks_refips` |
| `key` | Yes | API key from Subscription info > API units. |
| `target` | Yes | Root domain, subdomain, or URL to investigate. Example: `example.com`, `www.example.com`, or `http://www.example.com` |
| `target_type` | Yes | Type of target. Values: `root_domain`, `domain` (use for subdomains), `url` |
| `export_columns` | Yes | Comma-separated columns to return. Defaults to all columns. Values: `ip`, `country`, `domains_num`, `backlinks_num`, `first_seen`, `last_seen` |
| `display_sort` | No | Column to sort by. Default: `domains_num_desc`. Values: `domains_num_asc`, `domains_num_desc`, `backlinks_num_asc`, `backlinks_num_desc`, `first_seen_asc`, `first_seen_desc`, `last_seen_asc`, `last_seen_desc` |
| `display_limit` | No | Number of results to return. Default and value of `0`: 10,000. |
| `display_offset` | No | Number of results to skip before returning data. If used, increase `display_limit` by the offset value. |

## Export Columns

| Column | Description |
|---|---|
| `ip` | IP address hosting referring domains. |
| `country` | Country associated with the IP address (ISO 3166-1 Alpha-2). |
| `domains_num` | Number of unique domains hosted at this IP that link to the target. |
| `backlinks_num` | Total backlinks from this IP to the target. |
| `first_seen` | Unix timestamp when Semrush first noticed a backlink from this IP. |
| `last_seen` | Unix timestamp when Semrush last noticed a backlink from this IP. |

## Example Request

```
https://api.semrush.com/analytics/v1/?key=YOUR_API_KEY&type=backlinks_refips&target=searchenginejournal.com&target_type=root_domain&export_columns=ip,country,domains_num,backlinks_num,first_seen,last_seen&display_limit=5
```

## Example Response

```
ip;country;domains_num;backlinks_num;first_seen;last_seen
78.69.18.135;se;664;1195;1371696859;1580409277
192.0.78.12;us;357;3675;1534413883;1580408412
192.0.78.13;us;356;4012;1533338180;1580408397
172.217.15.65;us;306;617;1473348232;1580411014
172.217.164.161;us;300;581;1473018187;1580396737
```
