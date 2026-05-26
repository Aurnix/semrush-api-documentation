# SEO API — Domain PLA Search Keywords

**Price:** 30 API units per line
**Price (historical data):** 150 API units per line

Lists keywords that trigger a domain's product listing ads (PLA) to appear in Google's paid search results.

## Endpoint

```
GET https://api.semrush.com/
```

## Parameters

| Parameter | Required | Description |
|---|---|---|
| `type` | Yes | Report type. Value: `domain_shopping` |
| `key` | Yes | API key from Subscription info > API units. |
| `domain` | Yes | Website to investigate. Example: `example.com` |
| `database` | Yes | Regional database. See [Databases](seo_api_overview.md#databases). |
| `display_limit` | No | Number of results to return. Default and value of `0`: 10,000. Max value: 4,000,000. Max returned per call: 100,000 — use `display_offset` for more. |
| `display_offset` | No | Skip N results before returning. If used, increase `display_limit` by the offset value. `display_limit` must not exceed 4,000,000. |
| `export_escape` | No | If `1`, columns are wrapped in double quotes. |
| `export_decode` | No | If `0`, response is sent URL-encoded. If `1`, response is not encoded. |
| `export_columns` | No | Comma-separated columns. Default: `Ph,Po,Pp,Pd,Nq,Sn,Ur,Tt,Pr,Ts`. Available: `Ph,Po,Pp,Pd,Nq,Sn,Ur,Tt,Pr,Ts`. See [Columns](seo_api_overview.md#export-columns). |
| `display_sort` | No | Sort column and direction. Values: `po_asc`, `po_desc`, `nq_asc`, `nq_desc`, `pr_asc`, `pr_desc`. |
| `display_filter` | No | Filters. Fields: `Ph,Po,Nq,Ur,Tt,Pr`. See [Filters](seo_api_overview.md#filters). |

## Example Request

```
https://api.semrush.com/?type=domain_shopping&key=YOUR_API_KEY&domain=ebay.com&database=us&display_limit=3&display_sort=nq_desc&export_columns=Ph,Po,Pp,Pd,Nq,Sn,Ur,Tt,Pr,Ts
```

## Example Response

```
Keyword;Position;Previous Position;Position Difference;Search Volume;Shop Name;Url;Title;Product Price;Timestamp
apple watch;5;0;-5;1830000;eBay;http://www.ebay.com/i/123473122981;Apple Watch Series 2 - 38MM - Aluminum Case - White Sport Band - Smartwatch;169.99;1548155351
playstation;5;0;-5;673000;eBay;http://www.ebay.com/i/113408567972;877 Fully Tested Ps Vita PCH-1100 AB01 Crystal Black Console System Fw 3.68;95.94;1548148745
playstation;7;0;-7;673000;eBay;http://www.ebay.com/i/113493854733;Sony PlayStation 2 PS2 Fat Console Controller W/ Cords - Boots Up Refurbished;34.07;1548148745
```
