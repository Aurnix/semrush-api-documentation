# SEO API — Comparison by Referring Domains

**Price:** 40 API units per line

Shows how many backlinks are sent to a target domain and its competitors from the same referring domains.

## Endpoint

```
GET https://api.semrush.com/analytics/v1/
```

## Parameters

| Parameter | Required | Description |
|---|---|---|
| `type` | Yes | Report type. Value: `backlinks_matrix` |
| `key` | Yes | API key from Subscription info > API units. |
| `targets[]` | Yes | Array of root domains, subdomains, or URLs to compare. Repeat for each target: `targets[]=example.com&targets[]=competitor.com` |
| `target_types[]` | Yes | Array of target types corresponding to each `targets[]` entry. Values: `root_domain`, `domain` (use for subdomains), `url`. Repeat in the same order as `targets[]`. |
| `export_columns` | Yes | Comma-separated columns to return. Defaults to all columns. Values: `domain`, `domain_ascore` (also `domain_score`), `matches_num`, `backlinks_num`. Note: the response also includes one dynamic column per target domain named after that domain. |
| `display_sort` | No | Column to sort by. Default: `domain_score_desc`. Values: `domain_score_desc`, `domain_score_asc`, `matchesnum_desc`, `matchesnum_asc`, `backlinksnum_0_desc/asc` through `backlinksnum_5_desc/asc` (positional index matching `targets[]` order). |
| `display_limit` | No | Number of results to return. Default and value of `0`: 10,000. |
| `display_offset` | No | Number of results to skip before returning data. If used, increase `display_limit` by the offset value. |
| `display_filter` | No | Filter by backlink count per target. Fields: `backlinksnum_0` through `backlinksnum_5` (positional index matching `targets[]` order). |

## Export Columns

| Column | Description |
|---|---|
| `domain` | Referring domain name. |
| `domain_ascore` | Domain Authority Score of the referring domain. (`domain_score` is an alias.) |
| `matches_num` | Number of analyzed targets that receive backlinks from this referring domain. |
| `backlinks_num` | Total backlinks from this referring domain across all targets. |
| *(target domain name)* | One dynamic column per target showing the backlink count from this referring domain to that specific target. Column name is the target domain itself. |

## Notes

- Up to 6 targets can be compared (`backlinksnum_0` through `backlinksnum_5`).
- Sort and filter fields use zero-based positional index matching the order of `targets[]` in the request.

## Example Request

Compare referring domains for two sites; filter to domains that link to `searchengineland.com` but not `searchenginejournal.com` (`backlinksnum_0=0`):

```
https://api.semrush.com/analytics/v1/?key=YOUR_API_KEY&type=backlinks_matrix&targets[]=searchenginejournal.com&targets[]=searchengineland.com&target_types[]=root_domain&target_types[]=root_domain&export_columns=domain,domain_ascore,matches_num,backlinks_num&display_limit=5&display_filter=%2B%7Cbacklinksnum_0%7CEq%7C0
```

## Example Response

Dynamic columns (`searchenginejournal.com`, `searchengineland.com`) are appended to the row, showing backlink count per target.

```
domain;domain_ascore;matches_num;searchenginejournal.com;searchengineland.com
squarespace.com;85;1;0;4
cloudflare.com;92;1;0;8
amazon.com;94;1;0;2
progresspond.com;65;1;0;2
slideshare.net;88;1;0;9
```
