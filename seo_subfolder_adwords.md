# SEO API — Subfolder Paid Search Keywords

**Price:** 20 API units per line
**Price (historical data):** 100 API units per line

Lists keywords that bring users to a subfolder via Google's paid search results.

## Endpoint

```
GET https://api.semrush.com/
```

## Parameters

| Parameter | Required | Description |
|---|---|---|
| `type` | Yes | Report type. Value: `subfolder_adwords` |
| `key` | Yes | API key from Subscription info > API units. |
| `subfolder` | Yes | Subfolder to investigate. Example: `example.com/blog/` |
| `database` | Yes | Regional database. See [Databases](seo_api_overview.md#databases). |
| `display_limit` | No | Number of results to return. Default and value of `0`: 10,000. Max value: 4,000,000. Max returned per call: 100,000 — use `display_offset` for more. |
| `display_offset` | No | Skip N results before returning. If used, increase `display_limit` by the offset value. `display_limit` must not exceed 4,000,000. |
| `export_escape` | No | If `1`, columns are wrapped in double quotes. |
| `export_decode` | No | If `0`, response is sent URL-encoded. If `1`, response is not encoded. |
| `display_date` | No | Date for the report. Format: `YYYYMM15`. |
| `export_columns` | No | Comma-separated columns. Default: `Ph,Po,Pp,Pd,Nq,Cp,Vu,Tr,Tc,Co,Nr,Td`. Available: `Ph,Po,Pp,Pd,Ab,Nq,Cp,Tg,Tr,Tc,Co,Nr,Td,Tt,Ds,Vu,Ur,Ts,Un`. See [Columns](seo_api_overview.md#export-columns). |
| `display_sort` | No | Sort column and direction. Values: `po_asc`, `po_desc`, `tg_asc`, `tg_desc`, `tr_asc`, `tr_desc`, `tc_asc`, `tc_desc`, `nq_asc`, `nq_desc`. |
| `display_positions` | No | `new` — keywords newly in top 100; `lost` — no longer in top 100; `rise` — moved up; `fall` — moved down but still in top 100. |
| `display_filter` | No | Filters. Fields: `Ph,Po,Nq,Cp,Ur,Tg,Tr,Tc,Nr,Co,Pp,Pd,Un`. See [Filters](seo_api_overview.md#filters). |

## Example Request

```
https://api.semrush.com/?type=subfolder_adwords&key=API_KEY&display_limit=10&export_columns=Ph,Po,Pp,Pd,Nq,Cp,Ur,Tr,Tc,Co,Nr,Td&subfolder=ebay.com/help/&display_sort=po_asc&database=us
```

## Example Response

```
Keyword;Position;Previous Position;Position Difference;Search Volume;CPC;Url;Traffic (%);Traffic Cost (%);Competition;Number of Results;Trends
ebayebay;1;1;0;2900;0.32;https://www.ebay.com/help/home;2.03;0.75;0.46;70;0.66,0.24,0.66,0.44,0.35,0.66,0.66,0.53,0.35,0.66,1.00,0.29
how to withdraw offer on ebay;1;0;-1;30;1.00;https://www.ebay.com/help/buying/buy-now/making-best-offer?id=4019;0.01;0.01;0.14;81;0.09,0.09,0.09,0.09,0.09,0.09,0.09,0.09,0.09,0.04,0.52,0.14
contact enay;1;1;0;70;1.85;https://www.ebay.com/help/-/contact-ebay/contact-ebay?id=4379;0.04;0.10;0.08;84;0.63,0.36,0.45,0.45,1.00,0.45,1.00,0.45,0.63,0.45,0.36,0.45
ebay how to cancel offer;1;1;0;90;1.00;https://www.ebay.com/help/buying/buy-now/making-best-offer?id=4019;0.05;0.06;0.14;55;0.64,0.52,0.64,0.64,0.52,0.64,0.64,0.52,0.41,0.52,0.64,0.64
myebaywatchlist;1;1;0;40;2.73;https://www.ebay.com/help/buying/search-tips/watchlist?id=4046;0.01;0.08;0.08;43;0.06,0.00,0.00,0.00,1.00,0.00,0.00,0.00,0.00,0.00,0.02,0.00
```
