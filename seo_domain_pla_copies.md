# SEO API — PLA Copies

**Price:** 60 API units per line
**Price (historical data):** 300 API units per line

Shows product listing ad (PLA) copies Semrush noticed when the domain ranked in Google's paid search results for keywords from Semrush databases.

## Endpoint

```
GET https://api.semrush.com/
```

## Parameters

| Parameter | Required | Description |
|---|---|---|
| `type` | Yes | Report type. Value: `domain_shopping_unique` |
| `key` | Yes | API key from Subscription info > API units. |
| `domain` | Yes | Website to investigate. Example: `example.com` |
| `database` | Yes | Regional database. See [Databases](seo_api_overview.md#databases). |
| `display_limit` | No | Number of results to return. Default and value of `0`: 10,000. Max value: 4,000,000. Max returned per call: 100,000 — use `display_offset` for more. |
| `display_offset` | No | Skip N results before returning. If used, increase `display_limit` by the offset value. `display_limit` must not exceed 4,000,000. |
| `export_escape` | No | If `1`, columns are wrapped in double quotes. |
| `export_decode` | No | If `0`, response is sent URL-encoded. If `1`, response is not encoded. |
| `export_columns` | No | Comma-separated columns. Default: `Tt,Pr,Ur,Pc,Un`. Available: `Tt,Pr,Ur,Pc,Un,Ts`. See [Columns](seo_api_overview.md#export-columns). |
| `display_sort` | No | Sort column and direction. Values: `pr_asc`, `pr_desc`, `pc_asc`, `pc_desc`. |
| `display_filter` | No | Filters. Fields: `Tt,Pr`. See [Filters](seo_api_overview.md#filters). |

## Example Request

```
https://api.semrush.com/?type=domain_shopping_unique&key=YOUR_API_KEY&domain=ebay.com&database=us&display_limit=3&export_columns=Tt,Pr,Ur,Pc
```

## Example Response

```
Title;Product Price;Url;Number of Keywords
Windows 7 Professional 32/64 Bit Activation Key;6.1;http://www.ebay.com/i/323416369252;390
Microsoft Windows 7 Ultimate 32/64 Bit SP1&2 Download Link & MS Activation Key;4.99;http://www.ebay.com/i/202550754305;245
1080P DIY Spy Hidden Nanny Micro Pinhole Built-in Battery HD Camera DVR Recorder;32;http://www.ebay.com/i/192495737640;236
```
