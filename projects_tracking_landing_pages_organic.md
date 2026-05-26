# Position Tracking — Organic Landing Pages Report

**Price:** 1000 API units per landing page

Lists all URLs from Google's top 100 search results that the specified domain appears in for the keywords from a tracking campaign.

## Endpoint

```
GET https://api.semrush.com/reports/v1/projects/{campaignID}/tracking/
```

## Parameters

| Parameter | Required | Type | Description |
|---|---|---|---|
| `key` | Yes | string | API key from Subscription info > API units. |
| `action` | Yes | string | Value: `report`. |
| `type` | Yes | string | Value: `tracking_landing_pages_organic`. |
| `url` | Yes | string | Tracked URL or competitor URL (**without a mask**). Multiple: `url={domain1}:{domain2}`. |
| `date_begin` | No | date | Start date in `YYYYMMDD` format. |
| `date_end` | No | date | End date in `YYYYMMDD` format. |
| `display_tags` | No | string | Tags separated by `|`. Use `-` to exclude. OR groups included tags; if both included and excluded tags exist, each category uses OR internally and AND between categories. |
| `display_tags_condition` | No | string | Newer variant of `display_tags`. `|` = OR, `&` = AND. Use `!` to exclude. |
| `display_filter` | No | string | Filter for `Ph`, `Nq`, and `Cp` columns. See [Filters](projects_tracking_overview.md#filters). |
| `display_limit` | No | integer | Number of returned results. Default `10`. |
| `display_offset` | No | integer | Number of lines to skip. |
| `display_sort` | No | string | Allowed: `0_mc_asc`, `0_mc_desc`, `1_mc_asc`, `1_mc_desc`, `md_asc`, `md_desc`, `0_tr_asc`, `0_tr_desc`, `1_tr_asc`, `1_tr_desc`, `trdiff_asc`, `trdiff_desc`, `0_av_asc`, `0_av_desc`, `1_av_asc`, `1_av_desc`, `ad_asc`, `ad_desc`, `0_nq_asc`, `0_nq_desc`, `1_nq_asc`, `1_nq_desc`, `rd_asc`, `rd_desc`. See [Sortings](projects_tracking_overview.md#sortings). |
| `newlost_filter` | No | string | Return only new or lost URLs. Allowed: `new`, `lost`. |
| `linktype_filter` | No | integer | Local pack / hotel ranking inclusion. Values: `0` (include both — default), `1` (local pack and hotels only), `2` (exclude local pack), `524288` (exclude hotels), `524290` (exclude local pack and hotels), `536870912` (exclude AI Overview), `536870914` (exclude local pack and AI Overview), `537395202` (exclude local pack, hotels, and AI Overview). |
| `use_volume` | No | string | CPC/volume level. Allowed: `national`, `regional`, `local`. Defaults to the bottom-most available level. |

## Response Fields

| Field | Type | Description |
|---|---|---|
| `total` | integer | Number of results. |
| `limit` | integer | Number of returned results. |
| `offset` | integer | Number of lines skipped. |
| `new` | integer | Number of new URLs (didn't rank on the start date, ranks for at least one keyword on the end date). |
| `lost` | integer | Number of lost URLs (ranked on the start date, doesn't rank on the end date). |
| `keywords` | integer | Number of keywords used to build the report. |
| `Pc` | object | Counts of HTTP and HTTPS URLs. |
| `data` | array | Landing URLs and their metrics. |
| `Ur` | string | URL that ranks for the keyword. |
| `Tp` | string | `new` or `lost`. See definitions for `new`/`lost` above. |
| `Mc` | integer | Number of keywords the URL ranks for on the specified date. |
| `Av` | float | Average position for those keywords on the specified date. |
| `Tr` | float | Estimated traffic on the specified date. |
| `Tc` | float | Estimated traffic cost on the specified date. |
| `Rq` | integer | Total volume for the keywords the URL ranks for on the specified date. |
| `Kw` | array | List of keywords the URL ranks for. |
| `Kw → Pi` | string | Keyword ID. |
| `Kw → Ph` | string | Keyword the URL ranks for. |
| `Kw → Tp` | string | Per-keyword `new` / `lost`. |
| `Kw → Rq` | integer | Keyword volume. |
| `Kw → Gs` | integer | Volume crawling status. `0` = crawled, `1` = not crawled. |
| `Kw → Tg` | array | Keyword tags. |
| `Kw → Dt` | array | Dates and positions. |
| `Kw → Lt` | array | Ranking type. See [SERP features](projects_tracking_overview.md#serp-features). |
| `Kw → In` | array | Keyword intents: `i` (informational), `n` (navigational), `t` (transactional), `c` (commercial). |
| `Dt → [date] → In` | array | URL-level intent breakdown. Four items per intent: `Kc` (keywords count), `Tr` (traffic), `Kp` (percentage), `Na` (intent name — `i`/`n`/`t`/`c`). |

## Example Request

```
GET /?key=YOUR_API_KEY&action=report&type=tracking_landing_pages_organic&date_begin=20210518&date_end=20210524&url=apple.com&linktype_filter=0&display_sort=1_mc_desc
```

## Example Response

```json
{
  "total": 310,
  "state": "0",
  "limit": 100,
  "offset": 0,
  "new": 34,
  "lost": 32,
  "keywords": 200,
  "Pc": { "http": 2, "https": 308 },
  "data": {
    "0": {
      "Ur": "https://apps.apple.com/us/app/zillow-real-estate-rentals/id310738695",
      "Tp": "",
      "Dt": {
        "20210518": {
          "Mc": 1, "Av": 3, "Tr": 52566.67, "Tc": 9987.67, "Rq": 16600000,
          "In": [
            { "Kc": 1, "Tr": 269.36, "Kp": 50, "Na": "i" },
            { "Kc": 0, "Tr": 0,      "Kp": 0,  "Na": "n" },
            { "Kc": 1, "Tr": 269.36, "Kp": 50, "Na": "t" },
            { "Kc": 0, "Tr": 0,      "Kp": 0,  "Na": "c" }
          ]
        },
        "20210524": {
          "Mc": 1, "Av": 4, "Tr": 43713.33, "Tc": 8305.53, "Rq": 16600000,
          "In": [
            { "Kc": 1, "Tr": 269.36, "Kp": 50, "Na": "i" },
            { "Kc": 0, "Tr": 0,      "Kp": 0,  "Na": "n" },
            { "Kc": 1, "Tr": 269.36, "Kp": 50, "Na": "t" },
            { "Kc": 0, "Tr": 0,      "Kp": 0,  "Na": "c" }
          ]
        },
        "Diff": {
          "Mc": 0, "Av": -1, "Tr": -8853.33, "Tc": -1682.13, "Rq": 0,
          "In": [
            { "Kc": 0, "Tr": -176.86, "Na": "i" },
            { "Kc": 0, "Tr": 0,        "Na": "n" }
          ]
        }
      },
      "Kw": [
        {
          "Pi": "5243708147689083041",
          "Ph": "zillow",
          "Tp": "",
          "Rq": 16600000,
          "Gs": 1,
          "Tg": {},
          "In": { "0": "i", "1": "t" },
          "Dt": { "20210518": 3, "20210524": 4, "Diff": -1 },
          "Tr": { "20210518": 52566.67, "20210524": 43713.33, "Diff": -8853.33 },
          "Tc": { "20210518": 9987.67,  "20210524": 8305.53,  "Diff": -1682.13 },
          "Lt": { "20210518": ["rev"], "20210524": ["rev"] }
        }
      ],
      "Amp": 0
    }
  }
}
```

## See Also

- [Adwords landing pages report](projects_tracking_landing_pages_adwords.md)
- [Organic positions report](projects_tracking_position_organic.md)
- [Position Tracking Overview](projects_tracking_overview.md) — sortings, filters
