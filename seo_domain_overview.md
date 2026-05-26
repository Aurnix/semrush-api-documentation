# SEO API — Domain Overview (one database)

**Price:** 10 API units per line
**Price (historical data):** 50 API units per line

Provides live or historical data on a domain's keyword rankings in both organic and paid search in a chosen regional database.

## Endpoint

```
GET https://api.semrush.com/
```

## Parameters

| Parameter | Required | Description |
|---|---|---|
| `type` | Yes | Report type. Value: `domain_rank` |
| `key` | Yes | API key from Subscription info > API units. |
| `domain` | Yes | Website to investigate. Example: `example.com` |
| `database` | Yes | Regional database. See [Databases](seo_api_overview.md#databases). |
| `export_escape` | No | If `1`, columns are wrapped in double quotes. |
| `export_decode` | No | If `0`, response is sent URL-encoded. If `1`, response is not encoded. |
| `display_date` | No | Date for the report. Format: `YYYYMM15` (e.g., `20231215` for December 2023). Omit or leave empty for the most recent data. |
| `export_columns` | No | Comma-separated columns. Default: `Dn,Rk,Or,Ot,Oc,Ad,At,Ac`. Available: `Dn,Rk,Or,Xn,Ot,Oc,Ad,At,Ac,FKn,FPn,Ipu,Ip0,Ip1,Ip2,Ip3,Itu,It0,It1,It2,It3,Icu,Ic0,Ic1,Ic2,Ic3,Sr,Srb,St,Stb,Sc,Srn,Srl`. See [Columns](seo_api_overview.md#export-columns). |

## Example Request

```
https://api.semrush.com/?type=domain_rank&key=API_KEY&export_columns=Dn,Rk,Or,Ot,Oc,Ad,At,Ac&domain=seobook.com&database=us
```

## Example Response

```
Domain;Rank;Organic Keywords;Organic Traffic;Organic Cost;Adwords Keywords;Adwords Traffic;Adwords Cost
seobook.com;24041;5249;37332;143496;0;0;0
```
