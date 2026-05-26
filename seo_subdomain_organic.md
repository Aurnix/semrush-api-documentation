# SEO API — Subdomain Organic Search Keywords

**Price:** 10 API units per line
**Price (historical data):** 50 API units per line

Lists keywords that bring users to a subdomain via Google's top 100 organic search results.

## Endpoint

```
GET https://api.semrush.com/
```

## Parameters

| Parameter | Required | Description |
|---|---|---|
| `type` | Yes | Report type. Value: `subdomain_organic` |
| `key` | Yes | API key from Subscription info > API units. |
| `subdomain` | Yes | Subdomain to investigate. Example: `shop.example.com` |
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
https://api.semrush.com/?type=subdomain_organic&key=API_KEY&display_filter=%2B%7CPh%7CCo%7Cseo&display_limit=10&export_columns=Ph,Po,Pp,Pd,Nq,Cp,Ur,Tr,Tc,Co,Nr,Td&subdomain=tools.seobook.com&display_sort=tr_desc&database=us
```

## Example Response

```
Keyword;Position;Previous Position;Position Difference;Search Volume;CPC;Url;Traffic (%);Traffic Cost (%);Competition;Number of Results;Trends
tools seobook;1;1;0;40;0.00;http://tools.seobook.com/;2.81;0.00;0.13;123000;0.27,1.00,0.18,0.18,0.18,0.18,1.00,0.18,0.18,0.18,0.18,0.18
seo toolbar;3;3;0;260;2.69;http://tools.seobook.com/seo-toolbar/;1.84;2.51;0.04;4590000;0.18,0.11,0.05,0.03,0.81,0.28,0.23,0.44,0.35,0.44,1.00,0.81
seo tools;28;30;2;12100;4.34;http://tools.seobook.com/;1.58;3.43;0.26;257000000;0.81,0.66,0.66,0.81,0.81,1.00,0.81,0.81,0.81,0.81,1.00,1.00
seo book keyword tool;1;1;0;20;3.08;http://tools.seobook.com/keyword-tools/seobook/;1.40;2.15;0.14;4050000;0.11,0.07,0.07,0.07,0.07,0.07,0.07,0.07,0.26,0.07,0.07,0.07
free seo tools;18;20;2;4400;4.61;http://tools.seobook.com/;1.14;2.64;0.29;192000000;0.81,0.81,0.66,0.81,0.81,0.81,1.00,0.81,0.81,0.81,1.00,1.00
```
