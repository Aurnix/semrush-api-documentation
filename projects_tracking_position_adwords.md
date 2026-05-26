# Position Tracking — Adwords Positions Report

**Price:** 100 API units per keyword added

Lists all keywords from a tracking campaign, the Google paid search rankings of the specified URLs for those keywords, and position changes over the selected period.

## Endpoint

```
GET https://api.semrush.com/reports/v1/projects/{campaignID}/tracking/
```

## Parameters

| Parameter | Required | Type | Description |
|---|---|---|---|
| `key` | Yes | string | API key from Subscription info > API units. |
| `action` | Yes | string | Value: `report`. |
| `type` | Yes | string | Value: `tracking_position_adwords`. |
| `url` | No | string | Tracked URL or competitor URL (with a mask). Multiple: `url={domain1}:{domain2}`. Defaults to the campaign's URL. See [URL parameter mask](projects_tracking_overview.md#url-parameter-mask). |
| `date_begin` | No | date | Start date in `YYYYMMDD` format. |
| `date_end` | No | date | End date in `YYYYMMDD` format. |
| `display_tags` | No | string | Tags separated by `|`. Use `-` to exclude. OR groups included tags; if both included and excluded tags exist, each category uses OR internally and AND between categories. |
| `display_tags_condition` | No | string | Newer variant of `display_tags`. `|` = OR, `&` = AND. Use `!` to exclude. |
| `display_filter` | No | string | Filter for the `Ph`, `Nq`, and `Cp` columns. See [Filters](projects_tracking_overview.md#filters). |
| `display_limit` | No | integer | Number of returned results. Default `10`. |
| `display_offset` | No | integer | Number of lines to skip. |
| `display_sort` | No | string | Allowed: `cp_asc`, `cp_desc`, `{DOMAIN_N}_be_asc`, `{DOMAIN_N}_be_desc`, `{DOMAIN_N}_di_asc`, `{DOMAIN_N}_di_desc`, `{DOMAIN_N}_pos_asc`, `{DOMAIN_N}_pos_desc`, `nq_asc`, `nq_desc`, `ph_asc`, `ph_desc`. See [Sortings](projects_tracking_overview.md#sortings). |

## Response Fields

| Field | Type | Description |
|---|---|---|
| `total` | integer | Number of results. |
| `limit` | integer | Number of returned results. |
| `offset` | integer | Number of lines skipped. |
| `data` | array | Keywords and their metrics. |
| `Pi` | string | Keyword ID. |
| `Ph` | string | Keyword the URL ranks for. |
| `Kb` | string | Date the keyword was added to the tracking campaign. |
| `Tg` | array | Keyword tags. |
| `Cp` | float | Average CPC in USD (Google Ads). |
| `Nq` | integer | Average monthly searches (12-month average). |
| `Gs` | integer | Volume crawling status. `0` = crawled, `1` = not crawled. |
| `Dt` | array | Dates and positions (dates in `YYYYMMDD`). |
| `Be` | array | Ranking at the start of the period. |
| `Fi` | array | Ranking at the end of the period. |
| `Diff` | array | Ranking difference over the period. |
| `Diff1` | array | Ranking difference vs. previous day. |
| `Diff7` | array | Ranking difference over one week. |
| `Diff30` | array | Ranking difference over one month. |
| `Vi` | array | Domain visibility on the specified date. |
| `Sf` | array | SERP features present on the SERP. See [SERP features](projects_tracking_overview.md#serp-features). |
| `Sfc` | object | SERP feature counts: `Ex`, `Ne`, `De`, `Dn`. See [Organic positions](projects_tracking_position_organic.md) for details. |
| `Tr` | array | Estimated traffic on the specified date. |
| `Tc` | array | Estimated traffic cost on the specified date. |
| `Lu` | object | Landing URLs. |
| `Lt` | array | Ranking type. `org`: Organic. `adt`: AdWords top. `adb`: AdWords bottom. |

## Example Request

```
GET /?key=YOUR_API_KEY&action=report&type=tracking_position_adwords&url=*.apple.com%2F*:*.walmart.com%2F*&date_begin=20210522&date_end=20210528&display_sort=0_pos_asc&display_tags_condition=tag1%26!tag2
```

## Example Response

```json
{
  "total": 4,
  "state": "0",
  "limit": 10,
  "offset": 0,
  "data": {
    "0": {
      "Pi": "5331787400075558242",
      "Ph": "appl",
      "Kb": 20170908,
      "Tg": { "0": "tag2" },
      "Cp": "1.00",
      "Nq": "165000",
      "Gs": "0",
      "Dt": {
        "20210522": { "*.apple.com/*": "-", "*.walmart.com/*": "-" },
        "20210528": { "*.apple.com/*": 1,   "*.walmart.com/*": "-" }
      },
      "Be":    { "*.apple.com/*": "-", "*.walmart.com/*": "-" },
      "Fi":    { "*.apple.com/*": 1,   "*.walmart.com/*": "-" },
      "Diff":  { "*.apple.com/*": 11,  "*.walmart.com/*": "-" },
      "Diff1": { "*.apple.com/*": 0,   "*.walmart.com/*": "-" },
      "Diff7": { "*.apple.com/*": 11,  "*.walmart.com/*": "-" },
      "Diff30":{ "*.apple.com/*": 11,  "*.walmart.com/*": "-" },
      "Vi": {
        "20210522": { "*.apple.com/*": 0,  "*.walmart.com/*": 0 },
        "20210528": { "*.apple.com/*": 25, "*.walmart.com/*": 0 },
        "Diff":     { "*.apple.com/*": 25, "*.walmart.com/*": 0 }
      },
      "Sf": {
        "20210522": ["new", "knw", "stl", "kng"],
        "20210528": ["new", "rel", "adt", "knw", "rev", "stl", "kng"]
      },
      "Tr": {
        "20210522": { "*.apple.com/*": 0,    "*.walmart.com/*": 0 },
        "20210528": { "*.apple.com/*": 5500, "*.walmart.com/*": 0 }
      },
      "Tc": {
        "20210522": { "*.apple.com/*": 0,    "*.walmart.com/*": 0 },
        "20210528": { "*.apple.com/*": 5500, "*.walmart.com/*": 0 }
      },
      "Lu": {
        "20210522": { "*.apple.com/*": "", "*.walmart.com/*": "" },
        "20210528": { "*.apple.com/*": "https://www.apple.com/", "*.walmart.com/*": "" }
      },
      "Lt": {
        "20210522": { "*.apple.com/*": ["org"], "*.walmart.com/*": ["org"] },
        "20210528": { "*.apple.com/*": ["adt"], "*.walmart.com/*": ["org"] }
      }
    }
  }
}
```

## See Also

- [Organic positions report](projects_tracking_position_organic.md)
- [Adwords visibility index report](projects_tracking_visibility_adwords.md)
- [Adwords landing pages report](projects_tracking_landing_pages_adwords.md)
- [Position Tracking Overview](projects_tracking_overview.md) — sortings, filters, SERP features
