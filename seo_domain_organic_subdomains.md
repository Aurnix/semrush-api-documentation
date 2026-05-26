# SEO API — Domain Organic Subdomains

**Price:** 10 API units per line
**Price (historical data):** 50 API units per line

Shows subdomains of the analyzed domain ranking in Google's top 100 organic search results.

## Endpoint

```
GET https://api.semrush.com/
```

## Parameters

| Parameter | Required | Description |
|---|---|---|
| `type` | Yes | Report type. Value: `domain_organic_subdomains` |
| `key` | Yes | API key from Subscription info > API units. |
| `domain` | Yes | Website to investigate. Example: `example.com` |
| `database` | Yes | Regional database. See [Databases](seo_api_overview.md#databases). |
| `display_limit` | No | Number of results to return. Default and value of `0`: 10,000. Max value: 4,000,000. Max returned per call: 100,000 — use `display_offset` for more. |
| `display_offset` | No | Skip N results before returning. If used, increase `display_limit` by the offset value. `display_limit` must not exceed 4,000,000. |
| `export_escape` | No | If `1`, columns are wrapped in double quotes. |
| `export_decode` | No | If `0`, response is sent URL-encoded. If `1`, response is not encoded. |
| `display_date` | No | Date for the report. Format: `YYYYMM15`. |
| `export_columns` | No | Comma-separated columns. Default: `Ur,Pc,Tg,Tr`. Available: `Ur,Pc,Tg,Tr,Sr,St`. See [Columns](seo_api_overview.md#export-columns). |
| `display_sort` | No | Sort column and direction. Values: `pc_asc`, `pc_desc`, `tg_asc`, `tg_desc`, `tr_asc`, `tr_desc`, `sr_asc`, `sr_desc`, `st_asc`, `st_desc`. |

## Example Request

```
https://api.semrush.com/?type=domain_organic_subdomains&key=YOUR_API_KEY&display_limit=10&export_columns=Ur,Pc,Tg,Tr&domain=apple.com&database=us
```

## Example Response

```
Url;Number of Keywords;Traffic;Traffic (%)
itunes.apple.com;12576097;80811145;53.47
www.apple.com;1461853;43132944;28.54
support.apple.com;1255701;21914725;14.50
discussions.apple.com;1042589;2163623;1.43
trailers.apple.com;67190;799797;0.53
```
