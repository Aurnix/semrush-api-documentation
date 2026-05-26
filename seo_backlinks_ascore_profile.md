# SEO API — Authority Score Profile

**Price:** 100 API units per request

Returns the distribution of referring domains by Authority Score. For each Authority Score value from 0 to 100, returns the number of referring domains with at least one link pointing to the queried target.

## Endpoint

```
GET https://api.semrush.com/analytics/v1/
```

## Parameters

| Parameter | Required | Description |
|---|---|---|
| `type` | Yes | Report type. Value: `backlinks_ascore_profile` |
| `key` | Yes | API key from Subscription info > API units. |
| `target` | Yes | Root domain, subdomain, or URL to investigate. Example: `example.com`, `www.example.com`, or `http://www.example.com` |
| `target_type` | Yes | Type of target. Values: `root_domain`, `domain` (use for subdomains), `url` |

## Response Format

No `export_columns` parameter — response always returns two columns:

| Column | Description |
|---|---|
| `ascore` | Authority Score value. Range: `0–100`. |
| `domains_num` | Number of referring domains at this Authority Score that have at least one link to the target. |

Always returns 101 rows (one per score value 0–100).

## Example Request

```
https://api.semrush.com/analytics/v1/?key=YOUR_API_KEY&type=backlinks_ascore_profile&target=searchenginejournal.com&target_type=root_domain
```

## Example Response

```
ascore;domains_num
0;941
1;60
2;114
3;227
4;433
5;810
...
95;2
96;0
97;1
98;1
99;0
100;0
```
