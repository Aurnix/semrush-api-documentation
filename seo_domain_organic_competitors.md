# SEO API — Competitors in Organic Search

**Price:** 40 API units per line
**Price (historical data):** 200 API units per line

Lists a domain's competitors in organic search results.

The `Common Keywords` field in the response represents the value of the `Np` column — the number of organic keywords for which both the analyzed domain and the competitor domain rank within Google's top 100.

## Endpoint

```
GET https://api.semrush.com/
```

## Parameters

| Parameter | Required | Description |
|---|---|---|
| `type` | Yes | Report type. Value: `domain_organic_organic` |
| `key` | Yes | API key from Subscription info > API units. |
| `domain` | Yes | Website to investigate. Example: `example.com` |
| `database` | Yes | Regional database. See [Databases](seo_api_overview.md#databases). |
| `display_limit` | No | Number of results to return. Default and value of `0`: 10,000. Max value: 4,000,000. Max returned per call: 100,000 — use `display_offset` for more. |
| `display_offset` | No | Skip N results before returning. If used, increase `display_limit` by the offset value. `display_limit` must not exceed 4,000,000. |
| `export_escape` | No | If `1`, columns are wrapped in double quotes. |
| `export_decode` | No | If `0`, response is sent URL-encoded. If `1`, response is not encoded. |
| `display_date` | No | Date for the report. Format: `YYYYMM15`. |
| `export_columns` | No | Comma-separated columns. Default: `Dn,Cr,Np,Or,Ot,Oc,Ad`. Available: `Dn,Cr,Np,Or,Ot,Oc,Ad,Sr,St,Sc`. See [Columns](seo_api_overview.md#export-columns). |
| `display_sort` | No | Sort column and direction. Values: `np_desc`, `np_asc`, `cr_desc`, `cr_asc`. |

## Example Request

```
https://api.semrush.com/?type=domain_organic_organic&key=YOUR_API_KEY&display_limit=10&export_columns=Dn,Cr,Np,Or,Ot,Oc,Ad&domain=seobook.com&database=us
```

## Example Response

```
Domain;Competitor Relevance;Common Keywords;Organic Keywords;Organic Traffic;Organic Cost;Adwords Keywords
seochat.com;0.13;338;11021;5640;9690;0
seocentro.com;0.12;237;2196;8091;43478;0
internetmarketingninjas.com;0.12;323;15751;16182;30168;20
webconfs.com;0.12;265;6689;4291;14093;0
link-assistant.com;0.12;326;18255;13089;51583;26
```
