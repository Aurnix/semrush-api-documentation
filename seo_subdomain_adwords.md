# SEO API — Subdomain Paid Search Keywords

**Price:** 20 API units per line
**Price (historical data):** 100 API units per line

Lists keywords that bring users to a subdomain via Google's paid search results.

## Endpoint

```
GET https://api.semrush.com/
```

## Parameters

| Parameter | Required | Description |
|---|---|---|
| `type` | Yes | Report type. Value: `subdomain_adwords` |
| `key` | Yes | API key from Subscription info > API units. |
| `subdomain` | Yes | Subdomain to investigate. Example: `shop.example.com` |
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
https://api.semrush.com/?type=subdomain_adwords&key=API_KEY&display_limit=10&export_columns=Ph,Po,Pp,Pd,Nq,Cp,Vu,Tr,Tc,Co,Nr,Td&subdomain=www.ebay.com&display_sort=po_asc&database=us
```

## Example Response

```
Keyword;Position;Previous Position;Position Difference;Search Volume;CPC;Visible Url;Traffic (%);Traffic Cost (%);Competition;Number of Results;Trends
formalities by baum bros victorian rose collection;1;1;0;260;0.00;https://www.ebay.com;0.00;0.00;0.99;29;0.66,0.66,0.81,0.66,0.35,0.29,0.43,0.29,0.22,0.35,0.54,0.66
superman cards 1978 value;1;1;0;30;0.00;https://www.ebay.com;0.00;0.00;0.32;85;0.27,0.18,0.18,0.18,0.18,0.18,1.00,0.18,0.18,0.18,0.18,0.18
traxxas raptor body;1;1;0;90;0.21;https://www.ebay.com/;0.00;0.00;1.00;66;0.82,0.64,0.64,0.64,0.41,0.41,0.64,0.64,0.23,0.52,0.41,0.64
dtm motors;1;1;0;40;0.25;https://www.ebay.com;0.00;0.00;0.11;6810000;0.27,0.18,0.18,0.18,0.18,0.18,1.00,1.00,0.18,0.18,0.18,0.18
1958 encyclopedia britannica for sale;1;1;0;140;0.07;https://www.ebay.com;0.00;0.00;1.00;58;0.07,0.05,0.17,0.17,0.28,0.17,0.43,0.53,0.43,0.35,0.66,0.66
```
