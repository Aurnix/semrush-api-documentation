# SEO API — Domain Organic Pages

**Price:** 10 API units per line
**Price (historical data):** 50 API units per line

Shows unique pages of the analyzed domain ranking in Google's top 100 organic search results.

## Endpoint

```
GET https://api.semrush.com/
```

## Parameters

| Parameter | Required | Description |
|---|---|---|
| `type` | Yes | Report type. Value: `domain_organic_unique` |
| `key` | Yes | API key from Subscription info > API units. |
| `domain` | Yes | Website to investigate. Example: `example.com` |
| `database` | Yes | Regional database. See [Databases](seo_api_overview.md#databases). |
| `display_limit` | No | Number of results to return. Default and value of `0`: 10,000. Max value: 4,000,000. Max returned per call: 100,000 — use `display_offset` for more. |
| `display_offset` | No | Skip N results before returning. If used, increase `display_limit` by the offset value. `display_limit` must not exceed 4,000,000. |
| `export_escape` | No | If `1`, columns are wrapped in double quotes. |
| `export_decode` | No | If `0`, response is sent URL-encoded. If `1`, response is not encoded. |
| `display_date` | No | Date for the report. Format: `YYYYMM15`. |
| `export_columns` | No | Comma-separated columns. Default: `Ur,Pc,Tg,Tr`. Available: `Ur,Pc,Tg,Tr,Ipu,Ip0,Ip1,Ip2,Ip3,Itu,It0,It1,It2,It3,Sr,St`. See [Columns](seo_api_overview.md#export-columns). |
| `display_sort` | No | Sort column and direction. Default: `tr_desc`. Values: `pc_asc`, `pc_desc`, `tg_asc`, `tg_desc`, `tr_asc`, `tr_desc`, `sr_asc`, `sr_desc`, `st_asc`, `st_desc`. |
| `display_filter` | No | Filters. Fields: `Ur,Pc,Tg,Tr,Ipu,Ip0,Ip1,Ip2,Ip3,Sr,St`. See [Filters](seo_api_overview.md#filters). |

## Example Request

```
https://api.semrush.com/?type=domain_organic_unique&key=YOUR_API_KEY&display_filter=%2B%7CPc%7CGt%7C100&display_limit=10&export_columns=Ur,Pc,Tg,Tr&domain=seobook.com&display_sort=tr_desc&database=us
```

## Example Response

```
Url;Number of Keywords;Traffic;Traffic (%)
http://www.seobook.com/;317;2488;15.14
http://tools.seobook.com/meta-medic/;492;1289;7.84
http://tools.seobook.com/robots-txt/generator/;197;1133;6.89
http://tools.seobook.com/;588;1015;6.17
http://tools.seobook.com/ppc-tools/free-ppc-ad-coupons.html;930;916;5.57
```
