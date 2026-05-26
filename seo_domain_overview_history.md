# SEO API — Domain Overview (history)

**Price:** 10 API units per line

Provides live and historical data on a domain's keyword rankings in both organic and paid search in a chosen database. Monthly rankings are available from as far back as 2012–2016 (depending on the database) or daily rankings for the last 31 days (with `display_daily`).

Compared with `domain_rank` and `domain_ranks`, the `domain_rank_history` report returns monthly historical data for a domain. All three can return the same data when querying the same domain and time frame.

## Endpoint

```
GET https://api.semrush.com/
```

## Parameters

| Parameter | Required | Description |
|---|---|---|
| `type` | Yes | Report type. Value: `domain_rank_history` |
| `key` | Yes | API key from Subscription info > API units. |
| `domain` | Yes | Website to investigate. Example: `example.com` |
| `database` | Yes | Regional database. See [Databases](seo_api_overview.md#databases). |
| `display_limit` | No | Number of results to return. Default and value of `0`: 10,000. Max value: 4,000,000. Max returned per call: 100,000 — use `display_offset` for more. |
| `display_offset` | No | Skip N results before returning. If used, increase `display_limit` by the offset value. `display_limit` must not exceed 4,000,000. |
| `export_escape` | No | If `1`, columns are wrapped in double quotes. |
| `display_daily` | No | If `1`, returns daily updates on position changes for the last 31 days. If omitted, the report shows monthly results for the current and previous months. |
| `export_columns` | No | Comma-separated columns. Default: `Rk,Or,Ot,Oc,Ad,At,Ac,Dt`. Available: `Rk,Or,Xn,Ot,Oc,Ad,At,Ac,Dt,FKn,FPn,Sr,Srb,St,Stb,Sc`. See [Columns](seo_api_overview.md#export-columns). |
| `display_sort` | No | Sort column and direction. Values: `dt_asc`, `dt_desc`. |

## Example Request

```
https://api.semrush.com/?type=domain_rank_history&key=API_KEY&display_limit=10&export_columns=Rk,Or,Ot,Oc,Ad,At,Ac,Dt&domain=ebay.com&database=us
```

## Example Response

```
Rank;Organic Keywords;Organic Traffic;Organic Cost;Adwords Keywords;Adwords Traffic;Adwords Cost;Date
19;31504470;130638193;86905921;855962;25237906;18531300;20181215
19;31428334;130546351;87216370;781997;24688558;18258152;20181115
20;34087220;132189007;87847948;681771;18793935;14881683;20181015
24;36261896;108559244;79568188;596593;18348335;13814442;20180915
17;35872063;145322220;98773137;459219;17132356;11858911;20180815
```
