# SEO API — Ads Copies (Subfolder)

**Price:** 40 API units per line

Shows unique ad copies Semrush noticed when the subfolder ranked in Google's paid search results for keywords from Semrush databases.

## Endpoint

```
GET https://api.semrush.com/
```

## Parameters

| Parameter | Required | Description |
|---|---|---|
| `type` | Yes | Report type. Value: `subfolder_adwords_unique` |
| `key` | Yes | API key from Subscription info > API units. |
| `subfolder` | Yes | Subfolder to investigate. Example: `example.com/blog/` |
| `database` | Yes | Regional database. See [Databases](seo_api_overview.md#databases). |
| `display_limit` | No | Number of results to return. Default and value of `0`: 10,000. Max value: 4,000,000. Max returned per call: 100,000 — use `display_offset` for more. |
| `display_offset` | No | Skip N results before returning. If used, increase `display_limit` by the offset value. `display_limit` must not exceed 4,000,000. |
| `export_escape` | No | If `1`, columns are wrapped in double quotes. |
| `export_decode` | No | If `0`, response is sent URL-encoded. If `1`, response is not encoded. |
| `export_columns` | No | Comma-separated columns. Default: `Tt,Ds,Vu,Ur,Pc,Un`. Available: `Ph,Un,Tt,Ds,Vu,Ur,Pc,Ts`. See [Columns](seo_api_overview.md#export-columns). |
| `display_sort` | No | Sort column and direction. Values: `pc_asc`, `pc_desc`. |
| `display_filter` | No | Filters. Fields: `Tt,Ds,Vu`. See [Filters](seo_api_overview.md#filters). |

## Example Request

```
https://api.semrush.com/?type=subfolder_adwords_unique&key=API_KEY&display_limit=3&export_columns=Tt,Ds,Vu,Ur,Pc&subfolder=semrush.com/blog/&database=uk
```

## Example Response

The example below appears with `export_escape=1` (columns wrapped in quotes) and commas — preserved from the source page.

```
Title,Description,Visible Url,Url,Number of Keywords
"How to Analyze Competitor Website Traffic with Trends","Friendly interface, live data, millions of keywords to track. Get started!","https://www.semrush.com","https://www.semrush.com/blog/analyzing-competitors-traffic/","10"
"Best Keyword Research Tools: 10 Free & Paid Tools","Friendly interface, live data, millions of keywords to track. Get started!","https://www.semrush.com","https://www.semrush.com/blog/keyword-research-tools/","6"
"Google Ads Account to Create Relevant Ads | Semrush","Stay creative with your marketing campaigns & content. Semrush will take care of the data.","https://www.semrush.com","https://www.semrush.com/blog/google-ads-account/","5"
```
