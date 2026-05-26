# Position Tracking — Organic Overview Report

**Price:** 100 API units per request

Returns the number of keywords landing the specified domain on each of the top 100 positions on SERP, the number of new and lost keywords, the number with improved or decreased rankings, and the number that changed rankings over the selected period.

## Endpoint

```
GET https://api.semrush.com/reports/v1/projects/{campaignID}/tracking/
```

## Parameters

| Parameter | Required | Type | Description |
|---|---|---|---|
| `key` | Yes | string | API key from Subscription info > API units. |
| `action` | Yes | string | Value: `report`. |
| `type` | Yes | string | Value: `tracking_overview_organic`. |
| `url` | No | string | Tracked URL or competitor URL (with a mask). For multiple domains: `url={domain1}:{domain2}`. Defaults to the campaign's URL. See [URL parameter mask](projects_tracking_overview.md#url-parameter-mask). |
| `display_tags` | No | string | Tags separated by `|`. Use `-` to exclude. OR logic groups included tags; if both included and excluded tags exist, each category uses OR internally and AND between categories. |
| `display_tags_condition` | No | string | Newer variant of `display_tags`. `|` = OR, `&` = AND. Use `!` to exclude. |
| `date_begin` | No | date | Start date in `YYYYMMDD` format. |
| `date_end` | No | date | End date in `YYYYMMDD` format. |
| `linktype_filter` | No | integer | Local pack and hotel ranking inclusion. Values: `0` (include both — default), `1` (local pack and hotels only, organic excluded), `2` (exclude local pack), `524288` (exclude hotels), `524290` (exclude local pack and hotels), `536870912` (exclude AI Overview), `536870914` (exclude local pack and AI Overview), `537395202` (exclude local pack, hotels, and AI Overview). |
| `business_name` | No | string | Business name. Must match the name in Google Business Profile. |

## Response Fields

| Field | Type | Description |
|---|---|---|
| `total` | integer | Number of results. |
| `visibility` | percentage | Visibility index. |
| `differenceVisibility` | percentage | Visibility index difference. |
| `all` | integer | Number of keywords ranking in the top 100. |
| `all_difference` | integer | Difference in top-100 keywords. |
| `all_improved` | integer | Improved keywords in the top 100. |
| `all_declined` | integer | Declined keywords in the top 100. |
| `all_left` | integer | Keywords that no longer rank in the top 100. |
| `all_entered` | integer | Keywords that entered the top 100. |
| `top3` / `top3_*` | integer | Same set of metrics for top 3. |
| `top10` / `top10_*` | integer | Same set of metrics for top 10 (first page). |
| `top20` / `top20_*` | integer | Same set of metrics for top 20 (first two pages). |
| `data` | object | SERP position (`0`–`99`) → number of keywords on the end date. |

## Example Request

```
GET /?key=YOUR_API_KEY&action=report&type=tracking_overview_organic&url=*.apple.com%2F*&date_begin=20140405&date_end=20140411&linktype_filter=0
```

## Example Response

```json
{
  "total": 199,
  "visibility": 15.9602,
  "differenceVisibility": 1.7159,
  "all": 146,
  "all_improved": 67,
  "all_declined": 32,
  "all_difference": 3,
  "all_left": 3,
  "all_entered": 6,
  "top3": 36,
  "top3_improved": 8,
  "top3_declined": 2,
  "top3_difference": 2,
  "top3_left": 1,
  "top3_entered": 3,
  "top10": 67,
  "top10_improved": 19,
  "top10_declined": 13,
  "top10_difference": 6,
  "top10_left": 1,
  "top10_entered": 7,
  "top20": 97,
  "top20_improved": 36,
  "top20_declined": 19,
  "top20_difference": 10,
  "top20_left": 1,
  "top20_entered": 11,
  "data": {
    "0": 47,
    "1": 17,
    "2": 2
  }
}
```

## See Also

- [Adwords overview report](projects_tracking_overview_adwords.md)
- [Organic positions report](projects_tracking_position_organic.md)
- [Position Tracking Overview](projects_tracking_overview.md)
