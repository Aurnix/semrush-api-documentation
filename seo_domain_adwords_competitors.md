# SEO API — Competitors in Paid Search

**Price:** 40 API units per line
**Price (historical data):** 200 API units per line

Lists a domain's competitors in paid search results.

The `Common Keywords` field in the response represents the value of the `Np` column — the number of paid keywords for which both the analyzed domain and the competitor domain have active advertisements.

## Endpoint

```
GET https://api.semrush.com/
```

## Parameters

| Parameter | Required | Description |
|---|---|---|
| `type` | Yes | Report type. Value: `domain_adwords_adwords` |
| `key` | Yes | API key from Subscription info > API units. |
| `domain` | Yes | Website to investigate. Example: `example.com` |
| `database` | Yes | Regional database. See [Databases](seo_api_overview.md#databases). |
| `display_limit` | No | Number of results to return. Default and value of `0`: 10,000. Max value: 4,000,000. Max returned per call: 100,000 — use `display_offset` for more. |
| `display_offset` | No | Skip N results before returning. If used, increase `display_limit` by the offset value. `display_limit` must not exceed 4,000,000. |
| `export_escape` | No | If `1`, columns are wrapped in double quotes. |
| `export_decode` | No | If `0`, response is sent URL-encoded. If `1`, response is not encoded. |
| `display_date` | No | Date for the report. Format: `YYYYMM15`. |
| `export_columns` | No | Comma-separated columns. Default: `Dn,Cr,Np,Ad,At,Ac,Or`. Available: `Dn,Cr,Np,Ad,At,Ac,Or`. See [Columns](seo_api_overview.md#export-columns). |
| `display_sort` | No | Sort column and direction. Values: `np_desc`, `np_asc`, `cr_desc`, `cr_asc`. |

## Example Request

```
https://api.semrush.com/?type=domain_adwords_adwords&key=YOUR_API_KEY&display_limit=10&export_columns=Dn,Cr,Np,Ad,At,Ac,Or&domain=ebay.com&database=us
```

## Example Response

```
Domain;Competitor Relevance;Common Keywords;Adwords Keywords;Adwords Traffic;Adwords Cost;Organic Keywords
bestdeals.today;0.07;192427;4180961;231702687;219085005;98743
amazon.com;0.07;337566;7674897;606923091;363744884;76392627
discount99.us;0.04;21583;82580;486315;307513;0
netdeals.com;0.03;27343;740384;38400483;28864800;6
walmart.com;0.03;21533;558633;146423426;31455771;19967088
```
