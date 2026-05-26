# SEO API — Subdomain Overview (history)

**Price:** 10 API units per line

Provides live and historical data on a subdomain's keyword rankings in both organic and paid search in a chosen database.

## Endpoint

```
GET https://api.semrush.com/
```

## Parameters

| Parameter | Required | Description |
|---|---|---|
| `type` | Yes | Report type. Value: `subdomain_rank_history` |
| `key` | Yes | API key from Subscription info > API units. |
| `subdomain` | Yes | Subdomain to investigate. Example: `shop.example.com` |
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
https://api.semrush.com/?type=subdomain_rank_history&key=API_KEY&display_limit=10&export_columns=Or,Ot,Oc,Ad,At,Ac,Dt&subdomain=partnernetwork.ebay.com&database=us
```

## Example Response

```
Organic Keywords;Organic Traffic;Organic Cost;Adwords Keywords;Adwords Traffic;Adwords Cost;Date
1259;8105;6634;1;7;8;20230215
1125;8133;7633;0;0;0;20230115
1116;5452;11365;0;0;0;20221215
966;5387;9436;2;13;16;20221115
983;5745;7820;0;0;0;20221015
```
