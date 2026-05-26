# SEO API — Keyword Overview (all databases)

**Price:** 10 API units per line

Provides a keyword summary — volume, CPC, competition level, and number of results — across all regional databases.

## Endpoint

```
GET https://api.semrush.com/
```

## Parameters

| Parameter | Required | Description |
|---|---|---|
| `type` | Yes | Report type. Value: `phrase_all` |
| `key` | Yes | API key from Subscription info > API units. |
| `phrase` | Yes | Keyword or expression to investigate. |
| `database` | No | Regional database. If omitted, the request is sent to all regional databases. See [Databases](seo_api_overview.md#databases). |
| `export_escape` | No | If `1`, columns are wrapped in double quotes. |
| `export_decode` | No | If `0`, response is sent URL-encoded. If `1`, response is not encoded. |
| `export_columns` | No | Comma-separated columns. Default: `Dt,Db,Ph,Nq,Cp,Co`. Available: `Dt,Db,Ph,Nq,Cp,Co,Nr,In,Kd`. See [Columns](seo_api_overview.md#export-columns). |

## Example Request

```
https://api.semrush.com/?type=phrase_all&key=API_KEY&phrase=seo&export_columns=Dt,Db,Ph,Nq,Cp,Co,Nr
```

## Example Response

```
Date;Database;Keyword;Search Volume;CPC;Competition
201903;bo;seo;390;0.44;0.03
201903;hu;seo;1900;0.82;0.45
201903;th;seo;5400;0.96;0.49
201903;cr;seo;590;0.43;0.14
```
