# Position Tracking — Adwords Visibility Index Report

**Price:** 100 API units per request

Returns a domain's visibility and visibility changes over the selected period for Google's paid search results.

## Endpoint

```
GET https://api.semrush.com/reports/v1/projects/{campaignID}/tracking/
```

## Parameters

| Parameter | Required | Type | Description |
|---|---|---|---|
| `key` | Yes | string | API key from Subscription info > API units. |
| `action` | Yes | string | Value: `report`. |
| `type` | Yes | string | Value: `tracking_visibility_adwords`. |
| `url` | No | string | Tracked URL or competitor URL (with a mask). Multiple: `url={domain1}:{domain2}`. Defaults to the campaign's URL. See [URL parameter mask](projects_tracking_overview.md#url-parameter-mask). |
| `date_begin` | No | date | Start date in `YYYYMMDD` format. |
| `date_end` | No | date | End date in `YYYYMMDD` format. |
| `display_tags` | No | string | Tags separated by `|`. Use `-` to exclude. OR groups included tags; if both included and excluded tags exist, each category uses OR internally and AND between categories. |
| `display_tags_condition` | No | string | Newer variant of `display_tags`. `|` = OR, `&` = AND. Use `!` to exclude. |
| `display_filter` | No | string | Filter for `Ph`, `Nq`, and `Cp` columns. See [Filters](projects_tracking_overview.md#filters). |

## Response Fields

| Field | Type | Description |
|---|---|---|
| `total` | integer | Number of results. |
| `data` | array | Dates and metrics. |
| `Dt` | date | Date in `YYYYMMDD` format. |
| `Vi` | float | Absolute visibility value. |
| `Vr` | float | Relative visibility value. |
| `Av` | float | Average position. |
| `Sov` | float | Share of Voice. |
| `Tr` | float | Estimated traffic on the specified date. |
| `Tc` | float | Estimated traffic cost on the specified date. |

## Example Request

```
GET /?key=YOUR_API_KEY&action=report&type=tracking_visibility_adwords&date_begin=20140401&date_end=20140411&url=*.apple.com%2F*
```

## Example Response

```json
{
  "total": "7",
  "state": "0",
  "data": {
    "0": {
      "Dt": "20210518",
      "Vi": 23000000,
      "Vr": 11.5,
      "Av": 10.745,
      "Sov": 1.11,
      "Tr": 690766.666,
      "Tc": 815932.3328
    },
    "6": {
      "Dt": "20210524",
      "Vi": 16000000,
      "Vr": 8,
      "Av": 11.13,
      "Sov": 0.83,
      "Tr": 517833.3329,
      "Tc": 515993.6663
    }
  }
}
```

## See Also

- [Organic visibility index report](projects_tracking_visibility_organic.md)
- [Adwords positions report](projects_tracking_position_adwords.md)
- [Position Tracking Overview](projects_tracking_overview.md) — filters
