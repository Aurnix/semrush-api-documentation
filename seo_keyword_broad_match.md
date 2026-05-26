# SEO API — Broad Match Keyword

**Price:** 20 API units per line

Lists broad matches and alternate search queries that include particular keywords or keyword expressions.

## Endpoint

```
GET https://api.semrush.com/
```

## Parameters

| Parameter | Required | Description |
|---|---|---|
| `type` | Yes | Report type. Value: `phrase_fullsearch` |
| `key` | Yes | API key from Subscription info > API units. |
| `phrase` | Yes | Keyword or expression to investigate. |
| `database` | Yes | Regional database. See [Databases](seo_api_overview.md#databases). |
| `display_limit` | No | Number of results to return. Default and value of `0`: 10,000. Max returned per call: 100,000 — use `display_offset` for more. |
| `display_offset` | No | Skip N results before returning. If used, increase `display_limit` by the offset value. |
| `export_escape` | No | If `1`, columns are wrapped in double quotes. |
| `export_decode` | No | If `0`, response is sent URL-encoded. If `1`, response is not encoded. |
| `export_columns` | No | Comma-separated columns. Default: `Ph,Nr,Cp,Co,Nq,Td`. Available: `Ph,Nq,Cp,Co,Nr,Td,Fk,In,Kd`. See [Columns](seo_api_overview.md#export-columns). |
| `display_sort` | No | Sort column and direction. Values: `nq_asc`, `nq_desc`, `cp_asc`, `cp_desc`, `co_asc`, `co_desc`, `nr_asc`, `nr_desc`, `kd_asc`, `kd_desc`. |
| `display_filter` | No | Filters. Fields: `Ph,Nq,Cp,Co,Nr,Wc,Fk,Kd`. See [Filters](seo_api_overview.md#filters). |

## Example Request

```
https://api.semrush.com/?type=phrase_fullsearch&key=API_KEY&phrase=seo&export_columns=Ph,Nq,Cp,Co,Nr,Td,Fk,In&database=us&display_limit=10&display_sort=nq_desc&display_filter=%2B|Nq|Lt|1000
```

## Example Response

```
Keyword;Search Volume;CPC;Competition;Number of Results;Trends;SERP Features;Intent
actor lee seo jin;880;0;0;20900000;0.24,0.16,0.16,0.30,0.34,0.44,0.20,0.16,0.13,0.44,0.07,1.00;5,9,13,21,36;1
affordable seo packages;880;8.09;0.01;51100000;0.46,0.31,0.37,0.31,0.25,0.20,0.31,0.52,0.52,0.46,0.52,0.84;6,7,20,21,36,45,52;1
affordable seo services for small businesses;880;9.81;0.03;28200000;0.13,0.30,0.24,0.36,0.30,0.45,0.81,0.62,1.00,0.81,0.62,0.55;5,6,7,9,21,36,52;1
ahn seo-hyun;880;0;0;89;0.55,0.62,0.55,0.55,0.62,0.62,0.01,0.24,0.55,0.62,0.81,1.00;21,36;1
ai seo tool;880;6.63;0.3;162000000;0.20,0.16,0.65,0.08,0.20,1.00,0.44,0.24,0.11,0.24,0.11,0.13;6,7,9,21,36,38,52;1,0
```
