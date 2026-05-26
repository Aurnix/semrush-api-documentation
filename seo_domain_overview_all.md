# SEO API — Domain Overview (all databases)

**Price:** 10 API units per line
**Price (historical data):** 50 API units per line

Provides live or historical data on a domain's keyword rankings in both organic and paid search across all regional databases.

## Endpoint

```
GET https://api.semrush.com/
```

## Parameters

| Parameter | Required | Description |
|---|---|---|
| `type` | Yes | Report type. Value: `domain_ranks` |
| `key` | Yes | API key from Subscription info > API units. |
| `domain` | Yes | Website to investigate. Example: `example.com` |
| `database` | No | Regional database. If omitted, the request is sent to all regional databases (about 140 lines depending on your access). See [Databases](seo_api_overview.md#databases). |
| `display_limit` | No | Number of results to return. Default and value of `0`: 10,000. Max value: 4,000,000. Max returned per call: 100,000 — use `display_offset` for more. |
| `display_offset` | No | Skip N results before returning. If used, increase `display_limit` by the offset value. `display_limit` must not exceed 4,000,000. |
| `export_escape` | No | If `1`, columns are wrapped in double quotes. |
| `display_date` | No | Date for the report. Format: `YYYYMM15` (e.g., `20231215` for December 2023). Omit or leave empty for the most recent data. |
| `export_columns` | No | Comma-separated columns. Default: `Db,Dn,Rk,Or,Ot,Oc,Ad,At,Ac,Sh,Sv`. Available: `Db,Dt,Dn,Rk,Or,Ot,Oc,Ad,At,Ac,Sh,Sv,FKn,FPn,Sr,Srb,St,Stb,Sc,Srn,Srl`. See [Columns](seo_api_overview.md#export-columns). |
| `display_sort` | No | Sort column and direction. Values: `rk_asc`, `rk_desc`, `or_asc`, `or_desc`, `ot_asc`, `ot_desc`, `oc_asc`, `oc_desc`, `ad_asc`, `ad_desc`, `at_asc`, `at_desc`, `ac_asc`, `ac_desc`. |

## Example Request

```
https://api.semrush.com/?key=API_KEY&type=domain_ranks&export_columns=Db,Dn,Rk,Or,Ot,Oc,Ad,At,Ac,Sh,Sv&domain=apple.com&database=us
```

## Example Response

```
Database;Domain;Rank;Organic Keywords;Organic Traffic;Organic Cost;Adwords Keywords;Adwords Traffic;Adwords Cost;PLA keywords;PLA uniques
us;apple.com;17;16464474;149904314;169865994;128201;2419518;2807373;38208;1583
```
