# SEO API — Competitors (Backlinks)

**Price:** 40 API units per line

Lists domains that share a similar backlink profile with the analyzed domain.

## Endpoint

```
GET https://api.semrush.com/analytics/v1/
```

## Parameters

| Parameter | Required | Description |
|---|---|---|
| `type` | Yes | Report type. Value: `backlinks_competitors` |
| `key` | Yes | API key from Subscription info > API units. |
| `target` | Yes | Root domain, subdomain, or URL to investigate. Example: `example.com`, `www.example.com`, or `http://www.example.com` |
| `target_type` | Yes | Type of target. Values: `root_domain`, `domain` (use for subdomains), `url` |
| `export_columns` | Yes | Comma-separated columns to return. Defaults to all columns. Values: `ascore` (also listed as `score`), `neighbour`, `similarity`, `common_refdomains`, `domains_num`, `backlinks_num` |
| `display_limit` | No | Number of results to return. Default and value of `0`: 10,000. |
| `display_offset` | No | Number of results to skip before returning data. If used, increase `display_limit` by the offset value. |

## Export Columns

| Column | Description |
|---|---|
| `ascore` | Authority Score of the competitor domain. (`score` is an alias.) |
| `neighbour` | Competitor domain with a similar backlink profile. |
| `similarity` | Similarity score based on the number of common referring domains relative to total referring domains. Higher = more similar. |
| `common_refdomains` | Number of referring domains linking to both the analyzed domain and the competitor. |
| `domains_num` | Total referring domains for the competitor. |
| `backlinks_num` | Total backlinks for the competitor. |

## Example Request

```
https://api.semrush.com/analytics/v1/?key=YOUR_API_KEY&type=backlinks_competitors&target=searchenginejournal.com&target_type=root_domain&export_columns=ascore,neighbour,similarity,common_refdomains,domains_num,backlinks_num&display_limit=5
```

## Example Response

```
ascore;neighbour;similarity;common_refdomains;domains_num;backlinks_num
80;searchengineland.com;36;17584;79939;42840590
74;searchenginewatch.com;34;11537;47115;35855777
68;wordstream.com;32;9575;37065;1750926
77;moz.com;31;15732;103754;21136846
76;marketingland.com;30;9058;39986;9756098
```
