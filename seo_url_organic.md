# SEO API — URL Organic Search Keywords

**Price:** 10 API units per line
**Price (historical data):** 50 API units per line

Lists keywords that bring users to a URL via Google's top 100 organic search results.

## Endpoint

```
GET https://api.semrush.com/
```

## Parameters

| Parameter | Required | Description |
|---|---|---|
| `type` | Yes | Report type. Value: `url_organic` |
| `key` | Yes | API key from Subscription info > API units. |
| `url` | Yes | URL of a landing page to investigate. Example: `http://example.com/` |
| `database` | Yes | Regional database. See [Databases](seo_api_overview.md#databases). |
| `display_limit` | No | Number of results to return. Default and value of `0`: 10,000. Max value: 4,000,000. Max returned per call: 100,000 — use `display_offset` for more. |
| `display_offset` | No | Skip N results before returning. If used, increase `display_limit` by the offset value. `display_limit` must not exceed 4,000,000. |
| `export_escape` | No | If `1`, columns are wrapped in double quotes. |
| `export_decode` | No | If `0`, response is sent URL-encoded. If `1`, response is not encoded. |
| `display_date` | No | Date for the report. Format: `YYYYMM15`. |
| `export_columns` | No | Comma-separated columns. Default: `Ph,Po,Nq,Cp,Co,Tr,Tc,Nr,Td,Fp,Ts`. Available: `Ph,Po,Pp,Nq,Cp,Co,Kd,Tr,Tg,Tc,Nr,Td,Fp,Fk,Ts,In,Pt`. See [Columns](seo_api_overview.md#export-columns). |
| `display_sort` | No | Sort column and direction. Values: `po_asc`, `po_desc`, `tg_asc`, `tg_desc`, `tr_asc`, `tr_desc`, `tc_asc`, `tc_desc`, `nq_asc`, `nq_desc`. |
| `display_positions_type` | No | `organic` (default) — standard organic positions only; `all` — organic plus SERP Features; `serp_features` — SERP Features only. |
| `display_filter` | No | Filters. Fields: `Ph,Po,Nq,Cp,Ur,Tg,Tr,Tc,Nr,Co,Pp,Pd,Fp,Fk,In,Br`. See [Filters](seo_api_overview.md#filters). |

## Example Request

```
https://api.semrush.com/?type=url_organic&key=API_KEY&display_limit=10&export_columns=Ph,Po,Nq,Cp,Co,Tr,Tc,Nr,Td&url=http://tools.seobook.com/&database=us
```

## Example Response

```
Keyword;Position;Search Volume;CPC;Competition;Traffic (%);Traffic Cost;Number of Results;Trends
seo tools;4;8100;10.54;0.54;3.21;5976;226000000;0.67,0.82,0.82,1.00,0.82,0.82,0.67,0.67,0.67,0.67,0.82,0.82
free seo tools;6;1600;7.18;0.60;0.45;574;209000000;0.68,0.84,1.00,1.00,1.00,0.84,0.84,1.00,1.00,0.84,1.00,0.84
seo book keyword suggestion tool free download;1;70;0.00;0.14;0.31;0;775000;0.29,1.00,0.00,0.43,0.00,0.00,0.14,0.00,0.14,0.00,0.00,0.43
seo tools search engine software;2;210;0.00;0.02;0.15;0;37600000;0.54,1.00,1.00,0.81,0.65,0.81,1.00,0.81,0.81,0.81,0.54,0.35
tools seobook;1;30;16.96;0.29;0.13;407;162000;0.27,0.08,0.04,0.04,0.04,0.04,0.04,0.04,0.54,1.00,1.00,0.04
```
