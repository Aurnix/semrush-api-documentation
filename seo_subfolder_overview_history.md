# SEO API — Subfolder Overview (history)

**Price:** 10 API units per line

Provides live and historical data on a subfolder's keyword rankings in both organic and paid search in a chosen database.

## Endpoint

```
GET https://api.semrush.com/
```

## Parameters

| Parameter | Required | Description |
|---|---|---|
| `type` | Yes | Report type. Value: `subfolder_rank_history` |
| `key` | Yes | API key from Subscription info > API units. |
| `subfolder` | Yes | Subfolder to investigate. Example: `example.com/blog/` |
| `database` | Yes | Regional database. See [Databases](seo_api_overview.md#databases). |
| `display_limit` | No | Number of results to return. Default and value of `0`: 10,000. Max value: 4,000,000. Max returned per call: 100,000 — use `display_offset` for more. |
| `display_offset` | No | Skip N results before returning. If used, increase `display_limit` by the offset value. `display_limit` must not exceed 4,000,000. |
| `export_escape` | No | If `1`, columns are wrapped in double quotes. |
| `export_decode` | No | If `0`, response is sent URL-encoded. If `1`, response is not encoded. |
| `display_daily` | No | If `1`, returns daily updates on position changes for the last 30 days or more. If omitted, the report shows monthly results for the current and previous months. |
| `export_columns` | No | Comma-separated columns. Default: `Rk,Or,Ot,Oc,Ad,At,Ac,Dt`. Available: `Or,Xn,Ot,Oc,Ad,At,Ac,Dt,FKn,FPn,Sr,Srb,St,Stb,Sc,Rk`. Note: `Rk` returns `0` for URLs, subfolders, and subdomains — only domains receive a Rank value. See [Columns](seo_api_overview.md#export-columns). |
| `display_sort` | No | Sort column and direction. Values: `dt_asc`, `dt_desc`. |

## Example Request

```
https://api.semrush.com/?type=subfolder_rank_history&key=API_KEY&display_limit=10&export_columns=Or,Ot,Oc,Ad,At,Ac,Dt&subfolder=tools.seobook.com/general/&database=us
```

## Example Response

```
Organic Keywords;Organic Traffic;Organic Cost;Adwords Keywords;Adwords Traffic;Adwords Cost;Date
276;327;653;0;0;0;20230215
204;300;648;0;0;0;20230115
271;337;946;0;0;0;20221215
220;324;874;0;0;0;20221115
206;313;954;0;0;0;20221015
```
