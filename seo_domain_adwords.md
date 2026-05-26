# SEO API — Domain Paid Search Keywords

**Price:** 20 API units per line
**Price (historical data):** 100 API units per line

Lists keywords that bring users to a domain via Google's paid search results.

## Endpoint

```
GET https://api.semrush.com/
```

## Parameters

| Parameter | Required | Description |
|---|---|---|
| `type` | Yes | Report type. Value: `domain_adwords` |
| `key` | Yes | API key from Subscription info > API units. |
| `domain` | Yes | Website to investigate. Example: `example.com` |
| `database` | Yes | Regional database. See [Databases](seo_api_overview.md#databases). |
| `display_limit` | No | Number of results to return. Default and value of `0`: 10,000. Max value: 1,000,000. Max returned per call: 100,000 — use `display_offset` for more. |
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
https://api.semrush.com/?type=domain_adwords&key=YOUR_API_KEY&display_limit=10&export_columns=Ph,Po,Pp,Pd,Nq,Cp,Vu,Tr,Tc,Co,Nr,Td&domain=ebay.com&display_sort=po_asc&database=us
```

## Example Response

```
Keyword;Position;Previous Position;Position Difference;Search Volume;CPC;Visible Url;Traffic (%);Traffic Cost;Competition;Number of Results;Trends
g tube pads amazon;1;1;0;30;0.36;www.ebay.com/;0.00;0;0.88;3130000;0.14,0.14,0.43,0.14,0.71,0.14,0.57,0.14,1.00,0.14,0.14,0.14
13.8 v power supply;1;1;0;140;1.24;www.ebay.com/;0.00;8;1.00;9750000;0.82,0.82,0.52,1.00,0.82,0.65,0.65,0.65,0.82,0.82,0.82,1.00
ruger 22 250 magazine;1;1;0;10;0.02;www.ebay.com/22+250+magazine;0.00;0;0.64;1370000;1.00,0.60,0.80,0.40,0.20,0.20,0.20,0.20,0.20,0.20,0.20,0.40
```
