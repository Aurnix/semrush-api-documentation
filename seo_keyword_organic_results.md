# SEO API — Organic Results

**Price:** 10 API units per line
**Price (historical data):** 50 API units per line

Lists domains ranking in Google's top 100 organic search results for a requested keyword.

## Endpoint

```
GET https://api.semrush.com/
```

## Parameters

| Parameter | Required | Description |
|---|---|---|
| `type` | Yes | Report type. Value: `phrase_organic` |
| `key` | Yes | API key from Subscription info > API units. |
| `phrase` | Yes | Keyword or expression to investigate. |
| `database` | Yes | Regional database. See [Databases](seo_api_overview.md#databases). |
| `display_limit` | No | Number of results to return. Default and value of `0`: 10,000. Max returned per call: 100,000 — use `display_offset` for more. When `positions_type=all`, the limit applies to positions, not rows. |
| `display_offset` | No | Skip N results before returning. If used, increase `display_limit` by the offset value. |
| `export_escape` | No | If `1`, columns are wrapped in double quotes. |
| `export_decode` | No | If `0`, response is sent URL-encoded. If `1`, response is not encoded. |
| `display_date` | No | Date for the report. Format: `YYYYMM15` (e.g., `20231215` for December 2023). Omit or leave empty for the most recent data. |
| `export_columns` | No | Comma-separated columns. Default: `Dn,Ur,Fk`. Available: `Po,Pt,Dn,Ur,Fk,Fp,Fl` ⚠️. See [Columns](seo_api_overview.md#export-columns). |
| `positions_type` | No | `organic` (default) — traditional organic positions only; `all` — organic plus SERP Features. When `all`, the `Pt` column returns `-1` for the organic or SERP feature code. |

## Deprecated Columns

| Column | Note |
|---|---|
| `Fl` ⚠️ | Deprecated. Use `Fk` or `Fp` instead. |

## Example Request

```
https://api.semrush.com/?type=phrase_organic&key=API_KEY&phrase=seo&export_columns=Dn,Ur,Fk,Fp&database=us&display_limit=10
```

## Example Response

```
Domain;Url;Keywords SERP Features;SERP Features
moz.com;https://moz.com/beginners-guide-to-seo;1;6
moz.com;https://moz.com/learn/seo/what-is-seo;1;
searchengineland.com;https://searchengineland.com/guide/what-is-seo;1;
google.com;https://developers.google.com/search/docs/beginner/seo-starter-guide;1;6
neilpatel.com;https://neilpatel.com/what-is-seo/;1;
```
