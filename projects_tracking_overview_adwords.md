# Position Tracking — Adwords Overview Report

**Price:** 100 API units per request

Returns the number of keywords landing the specified domain on each of Google's paid search rankings on SERP, the number of new and lost keywords, the number with improved or decreased rankings, and the number that changed rankings over the selected period.

## Endpoint

```
GET https://api.semrush.com/reports/v1/projects/{campaignID}/tracking/
```

## Parameters

| Parameter | Required | Type | Description |
|---|---|---|---|
| `key` | Yes | string | API key from Subscription info > API units. |
| `action` | Yes | string | Value: `report`. |
| `type` | Yes | string | Value: `tracking_overview_adwords`. |
| `url` | No | string | Tracked URL or competitor URL (with a mask). Defaults to the campaign's URL. |
| `display_tags` | No | string | See [tag filter syntax](projects_tracking_overview.md). |
| `display_tags_condition` | No | string | Newer variant of `display_tags`. |
| `date_begin` | No | date | Start date in `YYYYMMDD` format. |
| `date_end` | No | date | End date in `YYYYMMDD` format. |
| `business_name` | No | string | Business name. Must match the name in Google Business Profile. |

## Response Fields

| Field | Type | Description |
|---|---|---|
| `total` | integer | Number of results. |
| `visibility` | percentage | Visibility index. |
| `differenceVisibility` | percentage | Visibility index difference. |
| `all` / `all_*` | integer | Top 100 keyword counts (same structure as Organic Overview). |
| `top3` / `top3_*` | integer | Top 3 keyword counts. |
| `top10` / `top10_*` | integer | Top 10 (first page) keyword counts. |
| `top20` / `top20_*` | integer | Top 20 (first two pages) keyword counts. |
| `data` | object | SERP position (`0`–`99`) → number of keywords on the end date. |

For the full field list see [Organic overview](projects_tracking_overview_organic.md) — both reports share the same response shape.

## Example Request

```
GET /?key=YOUR_API_KEY&action=report&type=tracking_overview_adwords&url=*.apple.com%2F*&date_begin=20140405&date_end=20140411&linktype_filter=0
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

- [Organic overview report](projects_tracking_overview_organic.md)
- [Adwords positions report](projects_tracking_position_adwords.md)
- [Position Tracking Overview](projects_tracking_overview.md)
