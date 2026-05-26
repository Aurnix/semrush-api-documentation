# SEO API — Batch Keyword Overview (one database)

**Price:** 10 API units per line
**Price (historical data):** 50 API units per line

Provides a summary of up to 100 keywords — volume, CPC, competition level, and number of results — in a chosen regional database.

## Endpoint

```
GET https://api.semrush.com/
```

## Parameters

| Parameter | Required | Description |
|---|---|---|
| `type` | Yes | Report type. Value: `phrase_these` |
| `key` | Yes | API key from Subscription info > API units. |
| `phrase` | Yes | Up to 100 keywords separated by semicolons. |
| `database` | Yes | Regional database. See [Databases](seo_api_overview.md#databases). |
| `export_escape` | No | If `1`, columns are wrapped in double quotes. |
| `export_decode` | No | If `0`, response is sent URL-encoded. If `1`, response is not encoded. |
| `display_date` | No | Date for the report. Format: `YYYYMM15` (e.g., `20231215` for December 2023). Omit or leave empty for the most recent data. |
| `export_columns` | No | Comma-separated columns. Default: `Ph,Nq,Cp,Co,Nr,Td`. Available: `Ph,Nq,Cp,Co,Nr,Td,In,Kd`. See [Columns](seo_api_overview.md#export-columns). |

## Example Request

```
https://api.semrush.com/?type=phrase_these&key=API_KEY&phrase=ebay;seo&export_columns=Ph,Nq,Cp,Co,Nr,Td&database=us
```

## Example Response

```
Keyword;Search Volume;CPC;Competition;Number of Results
ebay;45500000;0.54;0.01;1880000000
seo;110000;14.82;0.5;678000000
```
