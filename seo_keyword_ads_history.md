# SEO API — Keyword Ads History

**Price:** 100 API units per line

Shows domains that have bid on a requested keyword in the last 12 months and their positions in paid search results.

## Endpoint

```
GET https://api.semrush.com/
```

## Parameters

| Parameter | Required | Description |
|---|---|---|
| `type` | Yes | Report type. Value: `phrase_adwords_historical` |
| `key` | Yes | API key from Subscription info > API units. |
| `phrase` | Yes | Keyword or expression to investigate. |
| `database` | Yes | Regional database. See [Databases](seo_api_overview.md#databases). |
| `display_limit` | No | Number of results to return. Default and value of `0`: 10,000. Max returned per call: 100,000 — use `display_offset` for more. |
| `display_offset` | No | Skip N results before returning. If used, increase `display_limit` by the offset value. |
| `export_escape` | No | If `1`, columns are wrapped in double quotes. |
| `export_decode` | No | If `0`, response is sent URL-encoded. If `1`, response is not encoded. |
| `export_columns` | No | Comma-separated columns. Default: `Dn,Ad,At,Ac,Dt,Po,Ur,Tt,Vu`. Available: `Dn,Dt,Po,Ur,Tt,Ds,Vu,At,Ac,Ad`. See [Columns](seo_api_overview.md#export-columns). |

## Example Request

```
https://api.semrush.com/?type=phrase_adwords_historical&key=API_KEY&display_limit=1&export_columns=Dn,Dt,Po,Ur,Tt,Ds,Vu&phrase=movie&database=us
```

## Example Response

```
Domain;Date;Position;Url;Title;Description;Visible Url
blendedmovie.com;20140515;1;47.xg4ken.com/media/redir.php...;Blended Movie - blendedmovie.com;A wildly different family vacation. Out 5/23. Buy Tickets Today!;www.blendedmovie.com/
blendedmovie.com;20140415;;;;;
blendedmovie.com;20140315;;;;;
blendedmovie.com;20140215;;;;;
blendedmovie.com;20140115;;;;;
```
