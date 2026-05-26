# SEO API — URL Overview (one database)

**Price:** 10 API units per line
**Price (historical data):** 50 API units per line

Provides live or historical data on a URL's keyword rankings in both organic and paid search in a chosen regional database.

## Endpoint

```
GET https://api.semrush.com/
```

## Parameters

| Parameter | Required | Description |
|---|---|---|
| `type` | Yes | Report type. Value: `url_rank` |
| `key` | Yes | API key from Subscription info > API units. |
| `url` | Yes | URL to investigate. Example: `https://example.com/shop/gift-cards` |
| `database` | Yes | Regional database. See [Databases](seo_api_overview.md#databases). |
| `export_escape` | No | If `1`, columns are wrapped in double quotes. |
| `export_decode` | No | If `0`, response is sent URL-encoded. If `1`, response is not encoded. |
| `display_date` | No | Date for the report. Format: `YYYYMM15`. |
| `export_columns` | No | Comma-separated columns. Default: `Rk,Or,Ot,Oc,Ad,At,Ac`. Available: `Dn,Or,Xn,Ot,Oc,Ad,At,Ac,FKn,FPn,Ipu,Ip0,Ip1,Ip2,Ip3,Itu,It0,It1,It2,It3,Icu,Ic0,Ic1,Ic2,Ic3,Sr,Srb,St,Stb,Sc,Srn,Srl,Rk`. Note: `Rk` returns `0` for URLs, subfolders, and subdomains — only domains receive a Rank value. See [Columns](seo_api_overview.md#export-columns). |

## Example Request

```
https://api.semrush.com/?type=url_rank&key=API_KEY&export_columns=Or,Ot,Oc,Ad,At,Ac&url=https%3A%2F%2Fwww.ebay.com%2Fsignin%2F&database=us
```

## Example Response

```
Organic Keywords;Organic Traffic;Organic Cost;Adwords Keywords;Adwords Traffic;Adwords Cost
507;394412;89819;1;15;2
```
