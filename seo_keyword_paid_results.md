# SEO API — Paid Results

**Price:** 20 API units per line
**Price (historical data):** 100 API units per line

Lists domains ranking in Google's paid search results for a requested keyword.

## Endpoint

```
GET https://api.semrush.com/
```

## Parameters

| Parameter | Required | Description |
|---|---|---|
| `type` | Yes | Report type. Value: `phrase_adwords` |
| `key` | Yes | API key from Subscription info > API units. |
| `phrase` | Yes | Keyword or expression to investigate. |
| `database` | Yes | Regional database. See [Databases](seo_api_overview.md#databases). |
| `display_limit` | No | Number of results to return. Default and value of `0`: 10,000. Max returned per call: 100,000 — use `display_offset` for more. |
| `display_offset` | No | Skip N results before returning. If used, increase `display_limit` by the offset value. |
| `export_escape` | No | If `1`, columns are wrapped in double quotes. |
| `export_decode` | No | If `0`, response is sent URL-encoded. If `1`, response is not encoded. |
| `display_date` | No | Date for the report. Format: `YYYYMM15` (e.g., `20231215` for December 2023). Omit or leave empty for the most recent data. |
| `export_columns` | No | Comma-separated columns. Default: `Dn,Vu`. Available: `Dn,Ur,Vu`. See [Columns](seo_api_overview.md#export-columns). |

## Example Request

```
https://api.semrush.com/?type=phrase_adwords&key=API_KEY&phrase=seo&export_columns=Dn,Ur,Vu&database=us&display_limit=10
```

## Example Response

```
Domain;Url;Visible Url
wix.com;http://www.wix.com/;www.wix.com/
webcreationus.com;http://amp.webcreationus.com/google/seo;amp.webcreationus.com/google/seo
brunnerworks.com;http://www.brunnerworks.com/;www.brunnerworks.com/
rankingcoach.com;http://www.rankingcoach.com/;www.rankingcoach.com/
hinadm.com;http://www.hinadm.com/;www.hinadm.com/
```
