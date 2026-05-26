# SEO API — Subdomain Overview (all databases)

**Price:** 10 API units per line
**Price (historical data):** 50 API units per line

Provides live or historical data on a subdomain's keyword rankings in both organic and paid search across all regional databases.

## Endpoint

```
GET https://api.semrush.com/
```

## Parameters

| Parameter | Required | Description |
|---|---|---|
| `type` | Yes | Report type. Value: `subdomain_ranks` |
| `key` | Yes | API key from Subscription info > API units. |
| `subdomain` | Yes | Subdomain to investigate. Example: `shop.example.com` |
| `database` | No | Regional database. If omitted, the request is sent to all regional databases. See [Databases](seo_api_overview.md#databases). |
| `display_limit` | No | Number of results to return. Default and value of `0`: 10,000. Max value: 4,000,000. Max returned per call: 100,000 — use `display_offset` for more. |
| `display_offset` | No | Skip N results before returning. If used, increase `display_limit` by the offset value. `display_limit` must not exceed 4,000,000. |
| `export_escape` | No | If `1`, columns are wrapped in double quotes. |
| `display_date` | No | Date for the report. Format: `YYYYMM15`. |
| `export_columns` | No | Comma-separated columns. Default: `Db,Rk,Or,Ot,Oc,Ad,At,Ac,Sh,Sv`. Available: `Db,Dt,Dn,Or,Ot,Oc,Ad,At,Ac,Sh,Sv,FKn,FPn,Sr,Srb,St,Stb,Sc,Srn,Srl,Rk`. Note: `Rk` returns `0` for URLs, subfolders, and subdomains — only domains receive a Rank value. See [Columns](seo_api_overview.md#export-columns). |
| `display_sort` | No | Sort column and direction. Values: `or_asc`, `or_desc`, `ot_asc`, `ot_desc`, `oc_asc`, `oc_desc`, `ad_asc`, `ad_desc`, `at_asc`, `at_desc`, `ac_asc`, `ac_desc`. |

## Example Request

```
https://api.semrush.com/?key=API_KEY&type=subdomain_ranks&export_columns=Db,Or,Ot,Oc,Ad,At,Ac,Sh,Sv&subdomain=partnernetwork.ebay.com&database=us
```

## Example Response

```
Database;Organic Keywords;Organic Traffic;Organic Cost;Adwords Keywords;Adwords Traffic;Adwords Cost;PLA keywords;PLA uniques
us;1052;5383;8074;1;7;8;0;0
```
