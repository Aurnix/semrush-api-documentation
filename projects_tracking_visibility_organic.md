# Position Tracking — Organic Visibility Index Report

**Price:** 100 API units per request

Returns a domain's visibility and visibility changes over the selected period.

## Endpoint

```
GET https://api.semrush.com/reports/v1/projects/{campaignID}/tracking/
```

## Parameters

| Parameter | Required | Type | Description |
|---|---|---|---|
| `key` | Yes | string | API key from Subscription info > API units. |
| `action` | Yes | string | Value: `report`. |
| `type` | Yes | string | Value: `tracking_visibility_organic`. |
| `url` | No | string | Tracked URL or competitor URL (with a mask). Multiple: `url={domain1}:{domain2}`. Defaults to the campaign's URL. See [URL parameter mask](projects_tracking_overview.md#url-parameter-mask). |
| `date_begin` | No | date | Start date in `YYYYMMDD` format. |
| `date_end` | No | date | End date in `YYYYMMDD` format. |
| `display_tags` | No | string | Tags separated by `|`. Use `-` to exclude. OR groups included tags; if both included and excluded tags exist, each category uses OR internally and AND between categories. |
| `display_tags_condition` | No | string | Newer variant of `display_tags`. `|` = OR, `&` = AND. Use `!` to exclude. |
| `display_filter` | No | string | Filter for `Ph`, `Nq`, and `Cp` columns. See [Filters](projects_tracking_overview.md#filters). |
| `linktype_filter` | No | integer | Local pack / hotel ranking inclusion. Values: `0` (include both — default), `1` (local pack and hotels only), `2` (exclude local pack), `524288` (exclude hotels), `524290` (exclude local pack and hotels), `536870912` (exclude AI Overview), `536870914` (exclude local pack and AI Overview), `537395202` (exclude local pack, hotels, and AI Overview). |
| `use_volume` | No | string | CPC/volume level. Allowed: `national`, `regional`, `local`. Defaults to the bottom-most available level. |
| `business_name` | No | string | Business name. Must match the Google Business Profile name. |
| `serp_feature_filter` | No | string | Filter for keywords containing a specific SERP feature. See [SERP features](projects_tracking_overview.md#serp-features). |

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
GET /?key=YOUR_API_KEY&action=report&type=tracking_visibility_organic&date_begin=20210518&date_end=20210524&url=*.apple.com%2F*&linktype_filter=0
```

## Example Response

```json
{
  "total": "7",
  "state": "0",
  "data": {
    "0": {
      "Dt": "20210518",
      "Vi": 33397900,
      "Vr": 45.8762,
      "Av": 8.075,
      "Sov": 5.89,
      "Tr": 3258225.0324,
      "Tc": 9745148.8893
    },
    "6": {
      "Dt": "20210524",
      "Vi": 32230100,
      "Vr": 44.2721,
      "Av": 8.165,
      "Sov": 5.55,
      "Tr": 3230495.1761,
      "Tc": 9866793.9995
    }
  }
}
```

## See Also

- [Adwords visibility index report](projects_tracking_visibility_adwords.md)
- [Organic positions report](projects_tracking_position_organic.md)
- [Position Tracking Overview](projects_tracking_overview.md) — filters, SERP features
