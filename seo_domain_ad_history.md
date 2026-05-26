# SEO API — Domain Ad History

**Price:** 100 API units per line

Shows keywords a domain has bid on in the last 12 months along with its positions in paid search results.

## Endpoint

```
GET https://api.semrush.com/
```

## Parameters

| Parameter | Required | Description |
|---|---|---|
| `type` | Yes | Report type. Value: `domain_adwords_historical` |
| `key` | Yes | API key from Subscription info > API units. |
| `domain` | Yes | Website to investigate. Example: `example.com` |
| `database` | Yes | Regional database. See [Databases](seo_api_overview.md#databases). |
| `display_limit` | No | Number of results to return. Default and value of `0`: 10,000. Max value: 4,000,000. Max returned per call: 100,000 — use `display_offset` for more. |
| `display_offset` | No | Skip N results before returning. If used, increase `display_limit` by the offset value. `display_limit` must not exceed 4,000,000. |
| `export_escape` | No | If `1`, columns are wrapped in double quotes. |
| `export_columns` | No | Comma-separated columns. Default: `Ph,Dt,Po,Cp,Nq,Tr,Ur,Tt,Ds,Vu,Cv`. Available: `Ph,Dt,Po,Cp,Nq,Tr,Ur,Tt,Ds,Vu,Cv`. See [Columns](seo_api_overview.md#export-columns). |
| `display_sort` | No | Sort column and direction. Values: `cv_asc`, `cv_desc`. |
| `display_filter` | No | Filters. Fields: `Ph,Nq,Cp,Tr`. See [Filters](seo_api_overview.md#filters). |

## Example Request

```
https://api.semrush.com/?type=domain_adwords_historical&key=YOUR_API_KEY&display_limit=1&export_columns=Ph,Dt,Po,Cp,Nq,Tr,Ur,Tt,Ds,Vu&domain=amazon.com&database=us
```

## Example Response

```
Keyword;Date;Position;CPC;Search Volume;Traffic (%);Url;Title;Description;Visible Url
amazon;20181215;1;0.02;83100000;3905700;https://www.amazon.com/;Amazon.com Official Site | Free 2-Day Shipping with Prime Ad www.amazon.com/;Earth's biggest selection of books, electronics, apparel & more at low prices. Fast Shipping. Try Prime for Free.;
amazon;20181115;1;0.02;83100000;3905700;https://www.amazon.com/;Amazon.com® Official Site | Huge Selection & Great Prices Ad www.amazon.com/;Free Two-Day Shipping with Prime. Read Ratings & Reviews. Explore Amazon Devices. Fast Shipping.;
amazon;20181015;1;0.02;83100000;3905700;http://www.amazon.com/;Amazon.com Official Site | Huge Selection & Great Prices;Free Two-Day Shipping with Prime. Read Ratings & Reviews. Try Prime for Free.;www.amazon.com/
```
