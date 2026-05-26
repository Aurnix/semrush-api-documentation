# SEO API — PLA Competitors

**Price:** 60 API units per line
**Price (historical data):** 300 API units per line

Lists domains the requested domain is competing against in Google's paid search results with product listing ads (PLA).

The `Common Keywords` field in the response represents the value of the `Np` column — the number of keywords for which both the analyzed domain and the competitor domain have active product listing ads.

## Endpoint

```
GET https://api.semrush.com/
```

## Parameters

| Parameter | Required | Description |
|---|---|---|
| `type` | Yes | Report type. Value: `domain_shopping_shopping` |
| `key` | Yes | API key from Subscription info > API units. |
| `domain` | Yes | Website to investigate. Example: `example.com` |
| `database` | Yes | Regional database. See [Databases](seo_api_overview.md#databases). |
| `display_limit` | No | Number of results to return. Default and value of `0`: 10,000. Max value: 4,000,000. Max returned per call: 100,000 — use `display_offset` for more. |
| `display_offset` | No | Skip N results before returning. If used, increase `display_limit` by the offset value. `display_limit` must not exceed 4,000,000. |
| `export_escape` | No | If `1`, columns are wrapped in double quotes. |
| `export_decode` | No | If `0`, response is sent URL-encoded. If `1`, response is not encoded. |
| `export_columns` | No | Comma-separated columns. Default: `Dn,Cr,Np,Ad,At,Ac,Or,Sh`. Available: `Dn,Cr,Np,Sh,Ad,At,Ac,Or`. See [Columns](seo_api_overview.md#export-columns). |
| `display_sort` | No | Sort column and direction. Values: `np_asc`, `np_desc`, `cr_asc`, `cr_desc`. |

## Example Request

```
https://api.semrush.com/?type=domain_shopping_shopping&key=YOUR_API_KEY&domain=ebay.com&database=us&display_limit=10&display_sort=np_desc&export_columns=Dn,Cr,Np,Ad,At,Ac,Or
```

## Example Response

```
Domain;Competitor Relevance;Common Keywords;Adwords Keywords;Adwords Traffic;Adwords Cost;Organic Keywords
walmart.com;0.17;316712;555313;145469121;30624447;19966933
amazon.com;0.13;488457;7126039;568143801;329123277;76322373
etsy.com;0.08;117812;38328;22363968;3015402;9654230
newegg.com;0.05;61108;11250;6273638;2207224;2190128
jet.com;0.05;60721;9777;151975;161632;634721
```
