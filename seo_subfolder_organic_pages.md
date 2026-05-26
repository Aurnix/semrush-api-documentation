# SEO API — Subfolder Organic Pages

**Price:** 10 API units per line
**Price (historical data):** 50 API units per line

Shows unique pages of the analyzed subfolder ranking in Google's top 100 organic search results.

## Endpoint

```
GET https://api.semrush.com/
```

## Parameters

| Parameter | Required | Description |
|---|---|---|
| `type` | Yes | Report type. Value: `subfolder_organic_unique` |
| `key` | Yes | API key from Subscription info > API units. |
| `subfolder` | Yes | Subfolder to investigate. Example: `example.com/blog/` |
| `database` | Yes | Regional database. See [Databases](seo_api_overview.md#databases). |
| `display_limit` | No | Number of results to return. Default and value of `0`: 10,000. Max value: 4,000,000. Max returned per call: 100,000 — use `display_offset` for more. |
| `display_offset` | No | Skip N results before returning. If used, increase `display_limit` by the offset value. `display_limit` must not exceed 4,000,000. |
| `export_escape` | No | If `1`, columns are wrapped in double quotes. |
| `export_decode` | No | If `0`, response is sent URL-encoded. If `1`, response is not encoded. |
| `display_date` | No | Date for the report. Format: `YYYYMM15`. Defaults to current date if unset. |
| `export_columns` | No | Comma-separated columns. Default: `Ur,Pc,Tg,Tr`. Available: `Ur,Pc,Tg,Tr,Ipu,Ip0,Ip1,Ip2,Ip3,Itu,It0,It1,It2,It3,Sr,St`. See [Columns](seo_api_overview.md#export-columns). |
| `display_sort` | No | Sort column and direction. Values: `pc_asc`, `pc_desc`, `tg_asc`, `tg_desc`, `tr_asc`, `tr_desc`, `sr_asc`, `sr_desc`, `st_asc`, `st_desc`. |
| `display_filter` | No | Filters. Fields: `Ur,Pc,Tg,Tr,Ipu,Ip0,Ip1,Ip2,Ip3,Sr,St`. See [Filters](seo_api_overview.md#filters). |

## Example Request

```
https://api.semrush.com/?type=subfolder_organic_unique&key=API_KEY&display_filter=%2B%7CPc%7CGt%7C100&display_limit=5&export_columns=Ur,Pc,Tg,Tr&subfolder=ebay.com/help/&display_sort=tr_desc&database=us
```

## Example Response

The example below appears with `export_escape=1` (columns wrapped in quotes) and commas — preserved from the source page.

```
Url,Number of Keywords,Traffic,Traffic (%)
"https://www.ebay.com/help/buying/search-tips/purchase-history?id=4047","494","21074","19.45"
"https://www.ebay.com/help/account/signing-account/signing-account?id=4189","271","1786","1.64"
"https://www.ebay.com/help/account/default/ebay-account?id=4188","239","69789","64.43"
"https://www.ebay.com/help/selling/fees-credits-invoices/selling-fees?id=4822","233","161","0.14"
"https://www.ebay.com/help/buying/shipping-delivery/tracking-item?id=4027","232","672","0.62"
```
