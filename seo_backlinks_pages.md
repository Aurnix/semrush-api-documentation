# SEO API — Indexed Pages

**Price:** 40 API units per line

Shows indexed pages of the queried domain with backlink and link counts.

## Endpoint

```
GET https://api.semrush.com/analytics/v1/
```

## Parameters

| Parameter | Required | Description |
|---|---|---|
| `type` | Yes | Report type. Value: `backlinks_pages` |
| `key` | Yes | API key from Subscription info > API units. |
| `target` | Yes | Root domain, subdomain, or URL to investigate. Example: `example.com`, `www.example.com`, or `http://www.example.com` |
| `target_type` | Yes | Type of target. Values: `root_domain`, `domain` (use for subdomains), `url` |
| `export_columns` | Yes | Comma-separated columns to return. Defaults to all columns. Values: `source_url`, `source_title`, `response_code`, `backlinks_num`, `domains_num`, `last_seen`, `external_num`, `internal_num` |
| `display_sort` | No | Column to sort by. Default: `backlinks_num_desc`. Values: `backlinks_num_asc`, `backlinks_num_desc`, `domains_num_asc`, `domains_num_desc`, `last_seen_asc`, `last_seen_desc` |
| `display_limit` | No | Number of results to return. Default and value of `0`: 10,000. |
| `display_offset` | No | Number of results to skip before returning data. If used, increase `display_limit` by the offset value. |

## Export Columns

| Column | Description |
|---|---|
| `source_url` | URL of the indexed page. |
| `source_title` | Title of the indexed page. |
| `response_code` | Server response code (e.g., `200`, `301`). |
| `backlinks_num` | Number of backlinks pointing to this page. |
| `domains_num` | Number of referring domains pointing to this page. |
| `last_seen` | Unix timestamp when Semrush last crawled this page. |
| `external_num` | Number of external links on this page. |
| `internal_num` | Number of internal links on this page. |

## Example Request

```
https://api.semrush.com/analytics/v1/?key=YOUR_API_KEY&type=backlinks_pages&target=searchenginejournal.com&target_type=root_domain&export_columns=source_url,source_title,response_code,backlinks_num,domains_num,last_seen,external_num,internal_num&display_sort=domains_num_desc&display_limit=5
```

## Example Response

```
source_url;source_title;response_code;backlinks_num;domains_num;last_seen;external_num;internal_num
https://www.searchenginejournal.com/;Search Engine Journal - SEO, Search Marketing News and Tutorials;200;129873;3602;1580113263;16;405
http://www.searchenginejournal.com/;;301;213841;3543;1580400186;0;0
https://www.searchenginejournal.com/seo-101/seo-statistics/;60+ Mind-Blowing Search Engine Optimization Stats;200;11746;1675;1580367611;88;156
https://www.searchenginejournal.com/24-eye-popping-seo-statistics/42665/;;301;3127;822;1579709305;0;0
https://www.searchenginejournal.com/seo-guide/;A Complete Guide to SEO | Search Engine Journal;200;12856;743;1580411596;19;130
```
