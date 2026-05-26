# SEO API — Subfolder Organic Search Keywords

**Price:** 10 API units per line
**Price (historical data):** 50 API units per line

Lists keywords that bring users to a subfolder via Google's top 100 organic search results.

## Endpoint

```
GET https://api.semrush.com/
```

## Parameters

| Parameter | Required | Description |
|---|---|---|
| `type` | Yes | Report type. Value: `subfolder_organic` |
| `key` | Yes | API key from Subscription info > API units. |
| `subfolder` | Yes | Subfolder to investigate. Example: `example.com/blog/` |
| `database` | Yes | Regional database. See [Databases](seo_api_overview.md#databases). |
| `display_limit` | No | Number of results to return. Default and value of `0`: 10,000. Max value: 4,000,000. Max returned per call: 100,000 — use `display_offset` for more. |
| `display_offset` | No | Skip N results before returning. If used, increase `display_limit` by the offset value. `display_limit` must not exceed 4,000,000. |
| `export_escape` | No | If `1`, columns are wrapped in double quotes. |
| `display_date` | No | Date for the report. Format: `YYYYMM15`. |
| `display_daily` | No | If `1`, returns daily updates on position changes for the last 30 days or more. Applies only when `display_positions` is set. |
| `export_columns` | No | Comma-separated columns. Default: `Ph,Po,Pp,Pd,Nq,Cp,Ur,Tr,Tc,Co,Nr,Td`. Available: `Ph,Po,Pp,Pd,Nq,Cp,Ur,Tr,Tg,Tc,Co,Nr,Td,Kd,Fp,Fk,Ts,In,Pt`. See [Columns](seo_api_overview.md#export-columns). |
| `display_sort` | No | Sort column and direction. Values: `po_asc`, `po_desc`, `tg_asc`, `tg_desc`, `tr_asc`, `tr_desc`, `tc_asc`, `tc_desc`, `nq_asc`, `nq_desc`, `co_asc`, `co_desc`, `kd_asc`, `kd_desc`, `cp_asc`, `cp_desc`, `nr_asc`, `nr_desc`, `ts_asc`, `ts_desc`. |
| `display_positions` | No | `new` — keywords newly in top 100; `lost` — no longer in top 100; `rise` — moved up; `fall` — moved down but still in top 100. |
| `display_positions_type` | No | `organic` (default) — standard organic positions only; `all` — organic plus SERP Features; `serp_features` — SERP Features only. |
| `display_filter` | No | Filters. Fields: `Ph,Po,Nq,Cp,Ur,Tg,Tr,Tc,Nr,Co,Pp,Pd,Fp,Fk,In,Br`. See [Filters](seo_api_overview.md#filters). |

## Example Request

```
https://api.semrush.com/?type=subfolder_organic&key=API_KEY&display_filter=%2B%7CPh%7CCo%7Cseo&display_limit=10&export_columns=Ph,Po,Pp,Pd,Nq,Cp,Ur,Tr,Tc,Co,Nr,Td&subfolder=tools.seobook.com/general/&display_sort=tr_desc&database=us
```

## Example Response

```
Keyword;Position;Previous Position;Position Difference;Search Volume;CPC;Url;Traffic (%);Traffic Cost (%);Competition;Number of Results;Trends
seo keyword density checker;4;4;0;20;2.03;http://tools.seobook.com/general/keyword-density/;0.38;0.41;0.24;2000000;0.14,0.09,0.09,0.09,0.09,0.09,0.09,0.09,0.09,0.09,0.09,0.09
seo keyword density;10;10;0;90;3.45;http://tools.seobook.com/general/keyword-density/;0.38;1.25;0.01;2330000;0.52,0.33,0.52,0.42,0.23,0.66,0.52,0.42,0.33,0.42,1.00,0.33
seo analiser;69;69;0;110;4.61;http://tools.seobook.com/general/keyword-density/;0.00;0.00;0.17;10700000;0.07,0.28,0.28,0.05,0.05,0.05,0.28,0.66,0.17,1.00,0.35,0.66
seo spyder;74;74;0;70;3.57;http://tools.seobook.com/general/spider-test/;0.00;0.00;0.03;2230000;0.17,0.05,0.64,0.64,0.11,1.00,0.11,1.00,0.11,0.00,0.17,0.52
seo analysier;79;79;0;30;4.84;http://tools.seobook.com/general/keyword-density/;0.00;0.00;0.17;8550000;0.00,0.00,0.03,0.07,0.00,0.00,0.00,0.00,1.00,0.26,0.00,0.00
```
