# SEO API — Ads Copies (Subdomain)

**Price:** 40 API units per line

Shows unique ad copies Semrush noticed when the subdomain ranked in Google's paid search results for keywords from Semrush databases.

## Endpoint

```
GET https://api.semrush.com/
```

## Parameters

| Parameter | Required | Description |
|---|---|---|
| `type` | Yes | Report type. Value: `subdomain_adwords_unique` |
| `key` | Yes | API key from Subscription info > API units. |
| `subdomain` | Yes | Subdomain to investigate. Example: `shop.example.com` |
| `database` | Yes | Regional database. See [Databases](seo_api_overview.md#databases). |
| `display_limit` | No | Number of results to return. Default and value of `0`: 10,000. Max value: 4,000,000. Max returned per call: 100,000 — use `display_offset` for more. |
| `display_offset` | No | Skip N results before returning. If used, increase `display_limit` by the offset value. `display_limit` must not exceed 4,000,000. |
| `export_escape` | No | If `1`, columns are wrapped in double quotes. |
| `export_decode` | No | If `0`, response is sent URL-encoded. If `1`, response is not encoded. |
| `export_columns` | No | Comma-separated columns. Default: `Tt,Ds,Vu,Ur,Pc,Un`. Available: `Ph,Un,Tt,Ds,Vu,Ur,Pc,Ts`. See [Columns](seo_api_overview.md#export-columns). |
| `display_sort` | No | Sort column and direction. Values: `pc_asc`, `pc_desc`. |
| `display_filter` | No | Filters. Fields: `Tt,Ds,Vu`. See [Filters](seo_api_overview.md#filters). |

## Example Request

```
https://api.semrush.com/?type=subdomain_adwords_unique&key=API_KEY&display_limit=3&export_columns=Tt,Ds,Vu,Ur,Pc&subdomain=www.ebay.com&database=us
```

## Example Response

```
Title;Description;Visible Url;Url;Number of Keywords
Authentic Designer Goods - Clothing Shoes and Accessories;Prada Gucci Burberry Lanvin Chanel ;www.ebay.com/usr/luxeloveshop;http://www.ebay.com/usr/luxeloveshop&ved=0CHYQ0Qw;633
Boat For Sale on eBay;Huge selection of Boat For Sale.Free Shipping available. Buy Now!;www.ebay.com/;http://rover.ebay.com/rover/1/711-42618-2056-0/...;361
```
