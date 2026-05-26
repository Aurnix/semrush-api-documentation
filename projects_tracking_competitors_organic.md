# Position Tracking — Organic Competitors Discovery Report

**Price:** 1000 API units per competitor

Lists the domains that appear in Google's top 100 organic search results for the keywords from a tracking campaign for the chosen location, along with their average position and visibility.

## Endpoint

```
GET https://api.semrush.com/reports/v1/projects/{campaignID}/tracking/
```

## Parameters

| Parameter | Required | Type | Description |
|---|---|---|---|
| `key` | Yes | string | API key from Subscription info > API units. |
| `action` | Yes | string | Value: `report`. |
| `type` | Yes | string | Value: `tracking_competitors_organic`. |
| `url_type` | No | string | Type of competitor URLs. Allowed: `rootdomain`, `subdomain`, `subfolder`, `url`. Defaults to the campaign setting. |
| `url` | No | string | Competitor(s) (with a mask) to be returned. Multiple: `url={domain1}:{domain2}`. See [URL parameter mask](projects_tracking_overview.md#url-parameter-mask). |
| `main_domain` | No | string | Domain URL (without a mask) returned in a special block at the top of the competitors list. |
| `black_list` | No | string | Excluded domains, separated by `|`. |
| `top_start` | No | integer | Top of the SERP position range to search competitors in. |
| `top_end` | No | integer | Bottom of the SERP position range to search competitors in. |
| `date_begin` | No | date | Start date in `YYYYMMDD` format. |
| `date_end` | No | date | End date in `YYYYMMDD` format. |
| `display_tags` | No | string | Tags separated by `|`. Use `-` to exclude. |
| `display_tags_condition` | No | string | Newer variant of `display_tags`. `|` = OR, `&` = AND. Use `!` to exclude. |
| `display_limit` | No | integer | Number of returned results. Default `10`. |
| `display_offset` | No | integer | Number of lines to skip. |
| `display_sort` | No | string | Allowed: `1_mc_asc`, `1_mc_desc`, `av_asc`, `av_desc`, `cd_asc`, `cd_desc`, `cl_asc`, `cl_desc`, `{DATE}_asc`, `{DATE}_desc`, `sov_asc`, `sov_desc`, `sovdiff_asc`, `sovdiff_desc`, `tr_asc`, `tr_desc`, `trdiff_asc`, `trdiff_desc`, `ur_asc`, `ur_desc`. See [Sortings](projects_tracking_overview.md#sortings). |
| `linktype_filter` | No | integer | Local pack / hotel ranking inclusion. Values: `0` (include both — default), `1` (local pack and hotels only), `2` (exclude local pack), `524288` (exclude hotels), `524290` (exclude local pack and hotels), `536870912` (exclude AI Overview), `536870914` (exclude local pack and AI Overview), `537395202` (exclude local pack, hotels, and AI Overview). |

**Note:** The `url` parameter on this endpoint takes a URL **without** a mask (e.g. `ebay.com` rather than `*.ebay.com/*`).

## Response Fields

| Field | Type | Description |
|---|---|---|
| `total` | integer | Number of results. |
| `limit` | integer | Number of returned results. |
| `offset` | integer | Number of lines skipped. |
| `keywords_count` | integer | Number of keywords used to build the report. |
| `Md` | object | Special block for `main_domain`. Same shape as a `data` entry, plus `Ps` (position in the competitors list). |
| `data` | array | Competitor domains and their metrics. |
| `Dt` | array | Dates and metrics (dates in `YYYYMMDD`, plus a `Diff` entry). |
| `Mc` | integer | Number of keywords. |
| `Av` | float | Average position. |
| `Sq` | integer | Position deviation. |
| `Cl` | float | Visibility. |
| `Sov` | float | Share of Voice. |
| `Tr` | float | Estimated traffic on the specified date. |
| `Tc` | float | Estimated traffic cost on the specified date. |
| `Cd` | float | Visibility change over the period. |
| `Ur` | string | Competitor URL. |

## Example Request

```
GET /?key=YOUR_API_KEY&action=report&type=tracking_competitors_organic&date_begin=20210518&date_end=20210524&top_start=1&top_end=10&url_type=rootdomain&linktype_filter=0&display_sort=20210524_desc&main_domain=apple.com
```

## Example Response

```json
{
  "Md": {
    "Dt": {
      "20210518": { "Mc": 58, "Av": 30.666667, "Sq": 43, "Cl": 33.889567, "Sov": 31.962639, "Tr": 53941.55, "Tc": 44413.093073 },
      "20210524": { "Mc": 57, "Av": 31.950617, "Sq": 44, "Cl": 33.24515,  "Sov": 6.300615,  "Tr": 9495.707333, "Tc": 11272.560507 },
      "Diff":     { "Mc": -1, "Av": 1.28395,    "Sq": 1,  "Cl": -0.644417, "Sov": -25.662024, "Tr": -44445.842667, "Tc": -33140.532566 }
    },
    "Cd": -0.644417,
    "Ur": "apple.com",
    "Ps": 73
  },
  "total": 560,
  "state": "0",
  "limit": 100,
  "offset": 0,
  "keywords_count": 200,
  "data": {
    "0": {
      "Dt": {
        "20210518": { "Mc": 0, "Av": 100,    "Sq": 0, "Cl": 0,          "Sov": 0,          "Tr": "n/a", "Tc": "n/a" },
        "20210524": { "Mc": 1, "Av": 99.545, "Sq": 6, "Cl": 0.04120879, "Sov": 0.00001304, "Tr": 8.1,   "Tc": 9.072 },
        "Diff":     { "Mc": 1, "Av": -0.455, "Sq": 6, "Cl": 0.04120879, "Sov": 0.00001304, "Tr": 8.1,   "Tc": 9.072 }
      },
      "Cd": 0.04120879,
      "Ur": "android.com"
    }
  }
}
```

## See Also

- [Adwords competitors discovery report](projects_tracking_competitors_adwords.md)
- [Add competitors to a tracking campaign](projects_tracking_competitors_add.md)
- [Position Tracking Overview](projects_tracking_overview.md) — sortings, URL mask
