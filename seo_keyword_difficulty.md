# SEO API — Keyword Difficulty

**Price:** 50 API units per line

Provides keyword difficulty — an index that estimates how hard it would be to seize competitors' positions in Google's top 10 organic results for a queried term.

## Endpoint

```
GET https://api.semrush.com/
```

## Parameters

| Parameter | Required | Description |
|---|---|---|
| `type` | Yes | Report type. Value: `phrase_kdi` |
| `key` | Yes | API key from Subscription info > API units. |
| `phrase` | Yes | 1 to 100 keywords separated by semicolons. |
| `database` | Yes | Regional database. See [Databases](seo_api_overview.md#databases). |
| `export_escape` | No | If `1`, columns are wrapped in double quotes. |
| `export_columns` | No | Comma-separated columns. Default: `Ph,Kd`. Available: `Ph,Kd`. See [Columns](seo_api_overview.md#export-columns). |

## Example Request

```
https://api.semrush.com/?type=phrase_kdi&key=API_KEY&export_columns=Ph,Kd&phrase=ebay;seo&database=us
```

## Example Response

```
Keyword;Keyword Difficulty Index

ebay;95.10

seo;78.35
```
