# SEO API — Phrase Questions

**Price:** 40 API units per line

Lists phrase questions relevant to a queried term in a chosen database.

## Endpoint

```
GET https://api.semrush.com/
```

## Parameters

| Parameter | Required | Description |
|---|---|---|
| `type` | Yes | Report type. Value: `phrase_questions` |
| `key` | Yes | API key from Subscription info > API units. |
| `phrase` | Yes | Keyword or expression to investigate. |
| `database` | Yes | Regional database. See [Databases](seo_api_overview.md#databases). |
| `display_limit` | No | Number of results to return. Default and value of `0`: 10,000. Max returned per call: 100,000 — use `display_offset` for more. |
| `display_offset` | No | Skip N results before returning. If used, increase `display_limit` by the offset value. |
| `export_escape` | No | If `1`, columns are wrapped in double quotes. |
| `export_decode` | No | If `0`, response is sent URL-encoded. If `1`, response is not encoded. |
| `export_columns` | No | Comma-separated columns. Default: `Ph,Nr,Cp,Co,Nq,Td`. Available: `Ph,Nq,Cp,Co,Nr,Td,In,Kd`. See [Columns](seo_api_overview.md#export-columns). |
| `display_sort` | No | Sort column and direction. Values: `nq_asc`, `nq_desc`, `cp_asc`, `cp_desc`, `co_asc`, `co_desc`, `nr_asc`, `nr_desc`, `kd_asc`, `kd_desc`. |
| `display_filter` | No | Filters. Fields: `Ph,Nq,Cp,Co,Nr,Kd`. See [Filters](seo_api_overview.md#filters). |

## Example Request

```
https://api.semrush.com/?type=phrase_questions&key=API_KEY&phrase=seo&export_columns=Ph,Nq,Cp,Co,Nr,Td&database=us&display_limit=10&display_sort=nq_desc&display_filter=%2B|Nq|Lt|1000
```

## Example Response

```
Keyword;Search Volume;CPC;Competition;Number of Results;Trends
how to seo;880;5.23;0.16;611000000;0.88,1.00,1.00,1.00,0.88,0.88,0.88,0.88,0.88,0.88,0.88,0.88
how does seo work;590;3.6;0.09;183000000;0.67,0.82,0.82,1.00,0.82,0.82,0.82,0.82,0.82,0.82,1.00,0.67
how to improve seo;590;7.11;0.4;135000000;0.82,0.82,1.00,0.82,0.82,1.00,0.82,0.82,0.82,0.82,1.00,0.82
what is seo and how it works;590;5.69;0.18;188000000;0.44,0.54,0.82,1.00,1.00,0.67,0.54,0.67,0.67,0.82,1.00,1.00
how seo works;480;6.62;0.24;163000000;0.81,1.00,1.00,1.00,1.00,0.81,0.81,0.81,0.81,0.66,1.00,1.00
```
