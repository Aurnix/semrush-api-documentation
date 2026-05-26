# SEO API — Historical Data (Backlinks)

**Price:** 40 API units per line

Returns monthly historical trends of backlinks and referring domains for the queried root domain. Results are sorted by date from most recent to oldest.

## Endpoint

```
GET https://api.semrush.com/analytics/v1/
```

## Parameters

| Parameter | Required | Description |
|---|---|---|
| `type` | Yes | Report type. Value: `backlinks_historical` |
| `key` | Yes | API key from Subscription info > API units. |
| `target` | Yes | Root domain only. Example: `example.com`. Subdomains and URLs are not supported. |
| `target_type` | Yes | Always `root_domain`. No other values accepted. |
| `export_columns` | Yes | Comma-separated columns to return. Defaults to: `date,backlinks_num,domains_num,score` |
| `display_limit` | No | Number of results to return. Default and value of `0`: 10,000. |
| `display_offset` | No | Number of results to skip before returning data. If used, increase `display_limit` by the offset value. |

## Export Columns

| Column | Description |
|---|---|
| `date` | Unix timestamp of the monthly data point. |
| `backlinks_num` | Total backlinks at this date. |
| `domains_num` | Total referring domains at this date. |
| `score` | Authority Score of the queried domain at this date. |

## Example Request

```
https://api.semrush.com/analytics/v1/?key=YOUR_API_KEY&type=backlinks_historical&target=searchenginejournal.com&target_type=root_domain&export_columns=date,backlinks_num,domains_num&display_limit=5
```

## Example Response

```
date;backlinks_num;domains_num
1618185600;18768868;266988
1617580800;19005841;270238
1616976000;19145818;270371
1616371200;20011497;309865
1615766400;20669614;383991
```
