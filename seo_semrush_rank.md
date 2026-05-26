# SEO API — Semrush Rank

**Price:** 10 API units per line
**Price (historical data):** 50 API units per line

Lists the most popular domains ranked by traffic from Google's top 100 organic search results.

## Endpoint

```
GET https://api.semrush.com/
```

## Parameters

| Parameter | Required | Description |
|---|---|---|
| `type` | Yes | Report type. Value: `rank` |
| `key` | Yes | API key from Subscription info > API units. |
| `database` | Yes | Regional database. See [Databases](seo_api_overview.md#databases). |
| `display_limit` | No | Number of results to return. Default and value of `0`: 10,000. Max value: 4,000,000. Max returned per call: 100,000 — use `display_offset` for more. |
| `display_offset` | No | Skip N results before returning. If used, increase `display_limit` by the offset value. `display_limit` must not exceed 4,000,000. |
| `export_escape` | No | If `1`, columns are wrapped in double quotes. |
| `export_decode` | No | If `0`, response is sent URL-encoded. If `1`, response is not encoded. |
| `display_date` | No | Date for the report. Format: `YYYYMM15` (e.g., `20231215` for December 2023). Omit or leave empty for the most recent data. |
| `export_columns` | No | Comma-separated columns. Default: `Dn,Rk,Or,Ot,Oc,Ad,At,Ac`. Available: `Dn,Rk,Or,Ot,Oc,Ad,At,Ac,Sr,St,Sc`. See [Columns](seo_api_overview.md#export-columns). |
| `display_filter` | No | Filters. Fields: `Or,Ot,Oc,Sr,St,Sc`. See [Filters](seo_api_overview.md#filters). |

## Example Request

```
https://api.semrush.com/?key=API_KEY&type=rank&display_limit=10&database=us
```

## Example Response

```
Domain;Rank;Organic Keywords;Organic Traffic;Organic Cost;Adwords Keywords;Adwords Traffic;Adwords Cost
wikipedia.org;1;83084012;1953530514;1766901500;98;6375;9285
youtube.com;2;71381392;874589621;496405761;68366;63473756;29516519
amazon.com;3;76392627;677301991;516247065;7674897;606923091;363744884
facebook.com;4;59801076;629787192;375601566;86015;33960778;26585075
google.com;5;298085025;613488552;566022367;1595846;281663489;487303722
```
