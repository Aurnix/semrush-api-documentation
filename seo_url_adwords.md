# SEO API — URL Paid Search Keywords

**Price:** 20 API units per line
**Price (historical data):** 100 API units per line

Lists keywords that bring users to a URL via Google's paid search results.

## Endpoint

```
GET https://api.semrush.com/
```

## Parameters

| Parameter | Required | Description |
|---|---|---|
| `type` | Yes | Report type. Value: `url_adwords` |
| `key` | Yes | API key from Subscription info > API units. |
| `url` | Yes | URL of a landing page to investigate. Example: `http://example.com/` |
| `database` | Yes | Regional database. See [Databases](seo_api_overview.md#databases). |
| `display_limit` | No | Number of results to return. Default and value of `0`: 10,000. Max value: 4,000,000. Max returned per call: 100,000 — use `display_offset` for more. |
| `display_offset` | No | Skip N results before returning. If used, increase `display_limit` by the offset value. `display_limit` must not exceed 4,000,000. |
| `export_escape` | No | If `1`, columns are wrapped in double quotes. |
| `export_decode` | No | If `0`, response is sent URL-encoded. If `1`, response is not encoded. |
| `display_date` | No | Date for the report. Format: `YYYYMM15`. |
| `export_columns` | No | Comma-separated columns. Default: `Ph,Po,Nq,Cp,Co,Tr,Tc,Nr,Td,Tt,Ds`. Available: `Ph,Po,Nq,Cp,Co,Tg,Tr,Tc,Nr,Td,Tt,Ds,Ts`. See [Columns](seo_api_overview.md#export-columns). |
| `display_sort` | No | Sort column and direction. Values: `po_asc`, `po_desc`, `tg_asc`, `tg_desc`, `tr_asc`, `tr_desc`, `tc_asc`, `tc_desc`, `nq_asc`, `nq_desc`. |
| `display_filter` | No | Filters. Fields: `Ph,Po,Nq,Cp,Ur,Tg,Tr,Tc,Nr,Co,Pp,Pd`. See [Filters](seo_api_overview.md#filters). |

## Example Request

```
https://api.semrush.com/?type=url_adwords&key=API_KEY&display_limit=5&export_columns=Ph,Po,Nq,Cp,Co,Tr,Tc,Nr,Td,Tt,Ds&url=http://www.amazon.com/&database=us
```

## Example Response

```
Keyword;Position;Search Volume;CPC;Competition;Traffic (%);Traffic Cost;Number of Results;Trends;Title;Description
amazon;1;83100000;0.02;0.16;0.68;78114;81;1.00,0.67,0.67,0.67,0.67,0.67,0.67,0.81,0.67,0.67,0.67,0.81;Amazon.com Official Site | Huge Selection & Great Prices;Free Two-Day Shipping with Prime. Read Ratings & Reviews. Try Prime for Free. Explore Amazon Devices. Shop Best Sellers & Deals. Save with Our Low Prices. Shop Our Huge Selection. Fast Shipping.
amazon;1;83100000;0.02;0.16;0.68;78114;75;1.00,0.67,0.67,0.67,0.67,0.67,0.67,0.81,0.67,0.67,0.67,0.81;Amazon.com Official Site | Huge Selection & Great Prices;Free Two-Day Shipping with Prime. Shop Our Huge Selection. Try Prime for Free.
amazon;1;83100000;0.02;0.16;0.68;78114;2680000000;1.00,0.67,0.67,0.67,0.67,0.67,0.67,0.81,0.67,0.67,0.67,0.81;Amazon.com | Amazon® Official Site | Huge Selection & Great Prices;Free Two-Day Shipping with Prime. Explore Amazon Devices. Shop Our Huge Selection. Read Ratings & Reviews. Try Prime for Free. Fast Shipping. Save with Our Low Prices.
```
