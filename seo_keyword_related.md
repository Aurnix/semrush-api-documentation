# SEO API — Related Keywords

**Price:** 40 API units per line

Provides an extended list of related keywords, synonyms, and variations relevant to a queried term in a chosen database.

## Endpoint

```
GET https://api.semrush.com/
```

## Parameters

| Parameter | Required | Description |
|---|---|---|
| `type` | Yes | Report type. Value: `phrase_related` |
| `key` | Yes | API key from Subscription info > API units. |
| `phrase` | Yes | Keyword or expression to investigate. |
| `database` | Yes | Regional database. See [Databases](seo_api_overview.md#databases). |
| `display_limit` | No | Number of results to return. Default and value of `0`: 10,000. Max returned per call: 100,000 — use `display_offset` for more. |
| `display_offset` | No | Skip N results before returning. If used, increase `display_limit` by the offset value. |
| `export_escape` | No | If `1`, columns are wrapped in double quotes. |
| `export_decode` | No | If `0`, response is sent URL-encoded. If `1`, response is not encoded. |
| `export_columns` | No | Comma-separated columns. Default: `Ph,Nr,Cp,Co,Nq,Td,Rr`. Available: `Ph,Nq,Cp,Co,Nr,Td,Rr,Fk,In,Kd`. See [Columns](seo_api_overview.md#export-columns). |
| `display_sort` | No | Sort column and direction. Values: `nq_asc`, `nq_desc`, `cp_asc`, `cp_desc`, `co_asc`, `co_desc`, `nr_asc`, `nr_desc`, `rr_asc`, `rr_desc`, `kd_asc`, `kd_desc`. |
| `display_filter` | No | Filters. Fields: `Ph,Nq,Cp,Co,Nr,Wc,Fk,Kd`. See [Filters](seo_api_overview.md#filters). |

## Example Request

```
https://api.semrush.com/?type=phrase_related&key=API_KEY&phrase=seo&export_columns=Ph,Nq,Cp,Co,Nr,Td,Rr,Fk&database=us&display_limit=10&display_sort=nq_desc&display_filter=%2B|Nq|Lt|1000
```

## Example Response

```
Keyword;Search Volume;CPC;Competition;Number of Results;Trends;Related Relevance;SERP Features
beginners guide;880;0;0.01;1750000000;0.82,1.00,0.82,1.00,0.82,0.82,0.67,0.82,1.00,1.00,1.00,1.00;0.05;1,6,7,20,21
best po sites;880;0.14;0.38;1040000000;0.67,0.67,0.67,1.00,0.67,0.20,0.20,0.25,0.25,0.04,0.01,0.02;0.05;15,20,21
best seo;880;6.55;0.33;631000000;0.45,0.77,1.00,0.45,0.77,0.77,1.00,0.68,0.45,0.55,0.68,0.55;0.15;4,6,11,22
how seo works;880;3.93;0.28;164000000;0.55,1.00,0.77,0.77,0.68,0.45,0.45,0.45,0.45,0.45,0.77,0.68;0.15;6,11,20,21,22
how to improve seo;880;2.9;0.34;233000000;1.00,0.88,0.88,0.88,0.88,0.88,0.72,0.72,0.72,0.72,1.00,0.88;0.1;11,20,21
```
