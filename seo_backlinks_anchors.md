# SEO API — Anchors

**Price:** 40 API units per line

Lists anchor texts used in backlinks to the queried domain, root domain, or URL, along with backlink and referring domain counts per anchor.

## Endpoint

```
GET https://api.semrush.com/analytics/v1/
```

## Parameters

| Parameter | Required | Description |
|---|---|---|
| `type` | Yes | Report type. Value: `backlinks_anchors` |
| `key` | Yes | API key from Subscription info > API units. |
| `target` | Yes | Root domain, subdomain, or URL to investigate. Example: `example.com`, `www.example.com`, or `http://www.example.com` |
| `target_type` | Yes | Type of target. Values: `root_domain`, `domain` (use for subdomains), `url` |
| `export_columns` | Yes | Comma-separated columns to return. Defaults to all columns. Values: `anchor`, `domains_num`, `backlinks_num`, `first_seen`, `last_seen` |
| `display_sort` | No | Column to sort by. Default: `backlinks_num_desc`. Values: `domains_num_asc`, `domains_num_desc`, `backlinks_num_asc`, `backlinks_num_desc`, `first_seen_asc`, `first_seen_desc`, `last_seen_asc`, `last_seen_desc` |
| `display_limit` | No | Number of results to return. Default and value of `0`: 10,000. |
| `display_offset` | No | Number of results to skip before returning data. If used, increase `display_limit` by the offset value. |

## Export Columns

| Column | Description |
|---|---|
| `anchor` | Anchor text used in the backlink. |
| `domains_num` | Number of referring domains using this anchor text. |
| `backlinks_num` | Number of backlinks using this anchor text. |
| `first_seen` | Unix timestamp when Semrush first noticed a backlink with this anchor. |
| `last_seen` | Unix timestamp when Semrush last noticed a backlink with this anchor. |

## Example Request

```
https://api.semrush.com/analytics/v1/?key=YOUR_API_KEY&type=backlinks_anchors&target=searchenginejournal.com&target_type=root_domain&export_columns=anchor,domains_num,backlinks_num,first_seen,last_seen&display_limit=5
```

## Example Response

```
anchor;domains_num;backlinks_num;first_seen;last_seen
search engine journal;8113;691263;1370650463;1580411804
93% of people;3;354284;1524707034;1580411673
the growth of social media v2.0 | search engine journal;1;251996;1532739198;1578767338
more;57;153884;1452198531;1580411620
read more >;2;114350;1545826610;1580411612
```
