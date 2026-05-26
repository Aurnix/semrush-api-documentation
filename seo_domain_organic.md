# SEO API — Domain Organic Search Keywords

**Price:** 10 API units per line
**Price (historical data):** 50 API units per line

Lists keywords that bring users to a domain via Google's top 100 organic search results. Monthly rankings are available from as far back as 2012–2016 (depending on the database) and daily rankings for the last 31 days (with `display_daily`).

## Endpoint

```
GET https://api.semrush.com/
```

## Parameters

| Parameter | Required | Description |
|---|---|---|
| `type` | Yes | Report type. Value: `domain_organic` |
| `key` | Yes | API key from Subscription info > API units. |
| `domain` | Yes | Website to investigate. Example: `example.com` |
| `database` | Yes | Regional database. See [Databases](seo_api_overview.md#databases). |
| `display_limit` | No | Number of results to return. Default and value of `0`: 10,000. Max value: 4,000,000. Max returned per call: 100,000 — use `display_offset` for more. |
| `display_offset` | No | Skip N results before returning. If used, increase `display_limit` by the offset value. `display_limit` must not exceed 4,000,000. |
| `export_escape` | No | If `1`, columns are wrapped in double quotes. |
| `display_date` | No | Date for the report. `YYYYMM15` for monthly, `YYYYMMDD` for daily. Defaults to latest available daily ranking. |
| `display_daily` | No | If `1`, returns daily updates for the last 31 days. Applies only when `display_positions` is set. |
| `export_columns` | No | Comma-separated columns. Default: `Ph,Po,Pp,Pd,Nq,Cp,Ur,Tr,Tc,Co,Nr,Td`. Available: `Ph,Po,Pp,Pd,Nq,Cp,Ur,Tr,Tg,Tc,Co,Nr,Td,Kd,Fp,Fk,Ts,In,Pt`. See [Columns](seo_api_overview.md#export-columns). |
| `display_sort` | No | Sort column and direction. Values: `po_asc`, `po_desc`, `tg_asc`, `tg_desc`, `tr_asc`, `tr_desc`, `tc_asc`, `tc_desc`, `nq_asc`, `nq_desc`, `co_asc`, `co_desc`, `kd_asc`, `kd_desc`, `cp_asc`, `cp_desc`, `nr_asc`, `nr_desc`, `ts_asc`, `ts_desc`. |
| `display_positions` | No | `new` — keywords newly in top 100; `lost` — no longer in top 100; `rise` — moved up; `fall` — moved down but still in top 100. |
| `display_positions_type` | No | `organic` (default) — standard organic positions only; `all` — organic plus SERP Features; `serp_features` — SERP Features only. |
| `display_filter` | No | Filters. Fields: `Ph,Po,Nq,Cp,Ur,Tg,Tr,Tc,Nr,Co,Pp,Pd,Fp,Fk,In,Br`. See [Filters](seo_api_overview.md#filters). |

## Example Request

```
https://api.semrush.com/?type=domain_organic&key=YOUR_API_KEY&display_filter=%2B%7CPh%7CCo%7Cseo&display_limit=10&export_columns=Ph,Po,Pp,Pd,Nq,Cp,Ur,Tr,Tc,Co,Nr,Td&domain=seobook.com&display_sort=tr_desc&database=us
```

## Example Response

```
Keyword;Position;Previous Position;Position Difference;Search Volume;CPC;Url;Traffic (%);Traffic Cost (%);Competition;Number of Results;Trends
seo;9;10;1;110000;14.82;http://www.seobook.com/;17.53;44.40;0.50;0;0.81,1.00,1.00,1.00,1.00,0.81,0.81,0.81,0.81,0.81,0.81,0.81
seobook;1;1;0;1300;4.54;http://www.seobook.com/;5.52;4.28;0.32;379000;0.62,0.81,0.62,0.81,0.81,0.62,0.62,0.81,0.81,0.62,1.00,0.81
seo tools;6;6;0;8100;10.54;http://tools.seobook.com/;2.15;3.87;0.54;321000000;0.67,0.82,0.82,1.00,0.82,0.82,0.67,0.67,0.67,0.67,0.82,0.82
```
