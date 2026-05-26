# SEO API — Winners and Losers

**Price:** 20 API units per line
**Price (historical data):** 100 API units per line

Shows changes in the number of keywords, traffic, and budget estimates of the most popular websites in Google's top 100 organic and paid search results.

## Endpoint

```
GET https://api.semrush.com/
```

## Parameters

| Parameter | Required | Description |
|---|---|---|
| `type` | Yes | Report type. Value: `rank_difference` |
| `key` | Yes | API key from Subscription info > API units. |
| `database` | Yes | Regional database. See [Databases](seo_api_overview.md#databases). |
| `display_limit` | No | Number of results to return. Default and value of `0`: 10,000. Max value: 4,000,000. Max returned per call: 100,000 — use `display_offset` for more. |
| `display_offset` | No | Skip N results before returning. If used, increase `display_limit` by the offset value. `display_limit` must not exceed 4,000,000. |
| `export_escape` | No | If `1`, columns are wrapped in double quotes. |
| `export_decode` | No | If `0`, response is sent URL-encoded. If `1`, response is not encoded. |
| `display_date` | No | Date for the report. Format: `YYYYMM15` (e.g., `20231215` for December 2023). Omit or leave empty for the most recent data. |
| `export_columns` | No | Comma-separated columns. Default: `Dn,Rk,Or,Ot,Oc,Ad,At,Ac,Tm,Um,Am,Bm,Cm`. Available: `Dn,Rk,Or,Ot,Oc,Ad,At,Ac,Om,Tm,Um,Am,Bm,Cm,Sr,St,Sc,Srm,Stm,Scm`. See [Columns](seo_api_overview.md#export-columns). |
| `display_sort` | No | Sort column and direction. Values: `om_asc`, `om_desc`, `tm_asc`, `tm_desc`, `um_asc`, `um_desc`, `am_asc`, `am_desc`, `bm_asc`, `bm_desc`, `cm_asc`, `cm_desc`, `srm_asc`, `srm_desc`, `stm_asc`, `stm_desc`, `scm_asc`, `scm_desc`. |

## Example Request

```
https://api.semrush.com/?type=rank_difference&key=API_KEY&display_limit=5&database=us
```

## Example Response

```
Domain;Rank;Organic Keywords;Organic Traffic;Organic Cost;Adwords Keywords;Adwords Traffic;Adwords Cost;Organic Keywords Difference;Organic Traffic Difference;Organic Cost Difference;Adwords Keywords Difference;Adwords Traffic Difference;Adwords Cost Difference
wikipedia.org;1;83084012;1953530514;1766901500;98;6375;9285;469000;176196;-1008051;1;3;13
sites-domme.com;82912;356281;17749;18861;0;0;0;329506;16924;18008;0;0;0
namvideo.com;32556;996641;56717;37766;0;0;0;251320;9382;2923;0;0;0
suziequimpertraiteur.com;83918;472690;17493;23327;0;0;0;173988;-11050;-12218;0;0;0
pinterest.es;4684;4842602;531065;176004;0;0;0;155799;24012;-2499;0;0;0
```
