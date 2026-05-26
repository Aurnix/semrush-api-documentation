# SEO API — Referring Domains

**Price:** 40 API units per line

Lists domains pointing to the queried domain, root domain, or URL.

## Endpoint

```
GET https://api.semrush.com/analytics/v1/
```

## Parameters

| Parameter | Required | Description |
|---|---|---|
| `type` | Yes | Report type. Value: `backlinks_refdomains` |
| `key` | Yes | API key from Subscription info > API units. |
| `target` | Yes | Root domain, subdomain, or URL to investigate. Example: `example.com`, `www.example.com`, or `http://www.example.com` |
| `target_type` | Yes | Type of target. Values: `root_domain`, `domain` (use for subdomains), `url` |
| `export_columns` | Yes | Comma-separated columns to return. Defaults to: `domain,backlinks_num,domain_score,domain_trust_score,first_seen,last_seen,ip,country`. Note: `domain_score` is an alias for `domain_ascore`; use `domain_ascore` to request it explicitly. |
| `display_sort` | No | Column to sort by. Default: `backlinks_num_desc`. Values: `domain_ascore_asc`, `domain_ascore_desc`, `backlinks_num_asc`, `backlinks_num_desc`, `last_seen_asc`, `last_seen_desc`, `first_seen_asc`, `first_seen_desc` |
| `display_limit` | No | Number of results to return. Default and value of `0`: 10,000. |
| `display_offset` | No | Number of results to skip before returning data. If used, increase `display_limit` by the offset value. |
| `display_filter` | No | Filters to apply. Available filter fields: `zone`, `country`, `ip`, `newdomain`, `lostdomain`, `category` |

## Export Columns

| Column | Description |
|---|---|
| `domain_ascore` | Domain Authority Score — overall quality metric based on backlinks, referring domains, organic traffic. (`domain_score` is an alias.) |
| `domain` | Referring domain name. |
| `backlinks_num` | Number of backlinks from this domain to the target. |
| `domain_trust_score` | Domain trustworthiness metric. |
| `ip` | IP address associated with the referring domain. |
| `country` | Country the referring domain is associated with (ISO 3166-1 Alpha-2). |
| `first_seen` | Unix timestamp when Semrush first noticed a backlink from this domain. |
| `last_seen` | Unix timestamp when Semrush last noticed a backlink from this domain. |

## Example Request

```
https://api.semrush.com/analytics/v1/?key=YOUR_API_KEY&type=backlinks_refdomains&target=searchenginejournal.com&target_type=root_domain&export_columns=domain_ascore,domain,backlinks_num,ip,country,first_seen,last_seen&display_limit=5
```

## Example Response

```
domain_ascore;domain;backlinks_num;ip;country;first_seen;last_seen
86;libsyn.com;1850868;204.16.246.222;us;1495338484;1580410670
38;customerguru.in;503992;37.60.254.149;us;1532739198;1578767338
58;obs.co.kr;386005;59.25.202.101;kr;1565621989;1580411659
22;recip-links.com;354282;52.95.147.26;ca;1524707034;1580411673
38;goldenarticles.net;348079;89.190.202.12;bg;1544015188;1580411732
```
