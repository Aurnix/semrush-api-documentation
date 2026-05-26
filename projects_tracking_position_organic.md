# Position Tracking — Organic Positions Report

**Price:** 100 API units per keyword added

Lists all keywords from a Position Tracking campaign, top 100 rankings of the specified URLs for those keywords, and position changes over the selected timeframe. In addition to Google, this endpoint supports campaigns targeted to all Search Engine options available in Position Tracking, including ChatGPT. Rankings and visibility data are returned based on the specific search engine selected in the campaign configuration.

## Endpoint

```
GET https://api.semrush.com/reports/v1/projects/{campaignID}/tracking/
```

## Parameters

| Parameter | Required | Type | Description |
|---|---|---|---|
| `key` | Yes | string | API key from Subscription info > API units. |
| `action` | Yes | string | Value: `report`. |
| `type` | Yes | string | Value: `tracking_position_organic`. |
| `url` | No | string | Tracked URL or competitor URL (with a mask). Multiple: `url={domain1}:{domain2}`. Defaults to the campaign's URL. See [URL parameter mask](projects_tracking_overview.md#url-parameter-mask). |
| `top_filter` | No | string | Positions filter. Allowed: `top_3`, `top_3_income`, `top_3_leave`, `top_3_down`, `top_3_up`, `top_1page`, `top_1page_income`, `top_1page_leave`, `top_1page_down`, `top_1page_up`, `top_2page`, `top_2page_income`, `top_2page_leave`, `top_2page_down`, `top_2page_up`, `top_100`, `top_100_income`, `top_100_leave`, `top_100_down`, `top_100_up`. |
| `date_begin` | No | date | Start date in `YYYYMMDD` format. |
| `date_end` | No | date | End date in `YYYYMMDD` format. |
| `display_tags` | No | string | Tags separated by `|`. Use `-` to exclude. OR groups included tags; if both included and excluded tags exist, each category uses OR internally and AND between categories. |
| `display_tags_condition` | No | string | Newer variant of `display_tags`. `|` = OR, `&` = AND. Use `!` to exclude. |
| `display_filter` | No | string | Filter for the `Ph`, `Nq`, and `Cp` columns. See [Filters](projects_tracking_overview.md#filters). |
| `display_limit` | No | integer | Number of returned results. Default `10`. |
| `display_offset` | No | integer | Number of lines to skip. |
| `display_sort` | No | string | Allowed: `cp_asc`, `cp_desc`, `{DOMAIN_N}_be_asc`, `{DOMAIN_N}_be_desc`, `{DOMAIN_N}_diff_asc`, `{DOMAIN_N}_diff_desc`, `{DOMAIN_N}_pos_asc`, `{DOMAIN_N}_pos_desc`, `nq_asc`, `nq_desc`, `ph_asc`, `ph_desc`, `sov_asc`, `sov_desc`, `sovdiff_asc`, `sovdiff_desc`, `{DOMAIN_N}_vd_asc`, `{DOMAIN_N}_vd_desc`, `vi_asc`, `vi_desc`. See [Sortings](projects_tracking_overview.md#sortings). |
| `linktype_filter` | No | integer | Local pack / hotel ranking inclusion. Values: `0` (include both — default), `1` (local pack and hotels only), `2` (exclude local pack), `524288` (exclude hotels), `524290` (exclude local pack and hotels), `536870912` (exclude AI Overview), `536870914` (exclude local pack and AI Overview), `537395202` (exclude local pack, hotels, and AI Overview). |
| `use_volume` | No | string | CPC/volume level. Allowed: `national`, `regional`, `local`. Defaults to the bottom-most available level. |
| `business_name` | No | string | Business name. Must match the Google Business Profile name. |
| `serp_feature_filter` | No | string | Filter for keywords containing a specific SERP feature. See [SERP features](projects_tracking_overview.md#serp-features). |

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
| `Sov` | array | Domain Share of Voice on the specified date. |
| `Sf` | array | SERP features present on the SERP for the date. See [SERP features](projects_tracking_overview.md#serp-features). |
| `Sfc` | object | SERP feature counts: `Ex` (keywords with feature in SERP), `Ne` (keywords without it), `De` (keywords where tracked domain ranks inside the feature), `Dn` (keywords where it does not). |
| `Tr` | array | Estimated traffic on the specified date. |
| `Tc` | array | Estimated traffic cost on the specified date. |
| `Lu` | object | Landing URLs. |
| `Lt` | array | Ranking type. See [SERP features](projects_tracking_overview.md#serp-features). |
| `In` | array | Keyword intents: `i` (informational), `n` (navigational), `t` (transactional), `c` (commercial). |

## Example Request

```
GET /?key=YOUR_API_KEY&action=report&type=tracking_position_organic&url=*.apple.com%2F*:*.amazon.com%2F*&date_begin=20210521&date_end=20210527&linktype_filter=0&display_tags=tag1%26!tag2&display_sort=0_pos_asc
```

## Example Response

```json
{
  "total": 2,
  "state": "0",
  "limit": 10,
  "offset": 0,
  "data": {
    "0": {
      "Pi": "801444466689038445",
      "Ph": "facebook",
      "Kb": 20170908,
      "Tg": { "0": "tag1" },
      "In": { "0": "i", "1": "c" },
      "Cp": "1.44",
      "Nq": "185000000",
      "Gs": "0",
      "Dt": {
        "20210521": { "*.apple.com/*": 4, "*.amazon.com/*": 32 },
        "20210527": { "*.apple.com/*": 3, "*.amazon.com/*": 38 }
      },
      "Be": { "*.apple.com/*": 4, "*.amazon.com/*": 32 },
      "Fi": { "*.apple.com/*": 3, "*.amazon.com/*": 38 },
      "Diff": { "*.apple.com/*": 1, "*.amazon.com/*": -6 },
      "Diff1": { "*.apple.com/*": 0, "*.amazon.com/*": -10 },
      "Diff7": { "*.apple.com/*": 97, "*.amazon.com/*": 62 },
      "Diff30": { "*.apple.com/*": 97, "*.amazon.com/*": 62 },
      "Vi": {
        "20210521": { "*.apple.com/*": 10.8516, "*.amazon.com/*": 1.0714 },
        "20210527": { "*.apple.com/*": 13.0494, "*.amazon.com/*": 0.9065 },
        "Diff":     { "*.apple.com/*": 2.1978,  "*.amazon.com/*": -0.1649 }
      },
      "Sov": {
        "20210521": { "*.apple.com/*": 0.02, "*.amazon.com/*": 0.07 },
        "20210527": { "*.apple.com/*": 0.03, "*.amazon.com/*": 0.05 },
        "Diff":     { "*.apple.com/*": 0.01, "*.amazon.com/*": -0.02 }
      },
      "Sf": {
        "20210521": ["new", "twt", "rev", "stl", "kng"],
        "20210527": ["new", "twt", "rev", "stl", "kng"]
      },
      "Tr": {
        "20210521": { "*.apple.com/*": 487166.66, "*.amazon.com/*": 48100 },
        "20210527": { "*.apple.com/*": 585833.33, "*.amazon.com/*": 40700 }
      },
      "Tc": {
        "20210521": { "*.apple.com/*": 701520, "*.amazon.com/*": 69264 },
        "20210527": { "*.apple.com/*": 843600, "*.amazon.com/*": 58608 }
      },
      "Lu": {
        "20210521": {
          "*.apple.com/*": "https://apps.apple.com/us/app/facebook/id284882215",
          "*.amazon.com/*": "https://www.amazon.com/Facebook/dp/B0094BB4TW"
        },
        "20210527": {
          "*.apple.com/*": "https://apps.apple.com/us/app/facebook/id284882215",
          "*.amazon.com/*": "https://www.amazon.com/Facebook/dp/B0094BB4TW"
        }
      },
      "Lt": {
        "20210521": { "*.apple.com/*": ["rev"], "*.amazon.com/*": ["rev"] },
        "20210527": { "*.apple.com/*": ["rev"], "*.amazon.com/*": ["rev"] }
      }
    }
  }
}
```

## See Also

- [Adwords positions report](projects_tracking_position_adwords.md)
- [Organic visibility index report](projects_tracking_visibility_organic.md)
- [Organic landing pages report](projects_tracking_landing_pages_organic.md)
- [Position Tracking Overview](projects_tracking_overview.md) — sortings, filters, SERP features
