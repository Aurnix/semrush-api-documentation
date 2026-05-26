# Position Tracking — Adwords Landing Pages Report

**Price:** 1000 API units per landing page

Lists all URLs from Google's paid search results that the specified domain appears in for the keywords from a tracking campaign.

## Endpoint

```
GET https://api.semrush.com/reports/v1/projects/{campaignID}/tracking/
```

## Parameters

| Parameter | Required | Type | Description |
|---|---|---|---|
| `key` | Yes | string | API key from Subscription info > API units. |
| `action` | Yes | string | Value: `report`. |
| `type` | Yes | string | Value: `tracking_landing_pages_adwords`. |
| `url` | Yes | string | Tracked URL or competitor URL (with a mask). Multiple: `url={domain1}:{domain2}`. See [URL parameter mask](projects_tracking_overview.md#url-parameter-mask). |
| `date_begin` | No | date | Start date in `YYYYMMDD` format. |
| `date_end` | No | date | End date in `YYYYMMDD` format. |
| `display_tags` | No | string | Tags separated by `|`. Use `-` to exclude. OR groups included tags; if both included and excluded tags exist, each category uses OR internally and AND between categories. |
| `display_tags_condition` | No | string | Newer variant of `display_tags`. `|` = OR, `&` = AND. Use `!` to exclude. |
| `display_filter` | No | string | Filter for `Ph`, `Nq`, and `Cp` columns. See [Filters](projects_tracking_overview.md#filters). |
| `display_limit` | No | integer | Number of returned results. Default `10`. |
| `display_offset` | No | integer | Number of lines to skip. |
| `display_sort` | No | string | Allowed: `0_mc_asc`, `0_mc_desc`, `1_mc_asc`, `1_mc_desc`, `md_asc`, `md_desc`, `0_tr_asc`, `0_tr_desc`, `1_tr_asc`, `1_tr_desc`, `trdiff_asc`, `trdiff_desc`, `0_av_asc`, `0_av_desc`, `1_av_asc`, `1_av_desc`, `ad_asc`, `ad_desc`, `0_nq_asc`, `0_nq_desc`, `1_nq_asc`, `1_nq_desc`, `rd_asc`, `rd_desc`. See [Sortings](projects_tracking_overview.md#sortings). |
| `newlost_filter` | No | string | Return only new or lost URLs. Allowed: `new`, `lost`. |

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
| `Tp` | string | `new` or `lost`. |
| `Mc` | integer | Number of keywords the URL ranks for on the specified date. |
| `Av` | float | Average position on the specified date. |
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
| `Lt` | array | Ranking type: `org` (Organic), `adt` (AdWords top), `adb` (AdWords bottom). |

## Example Request

```
GET /?key=YOUR_API_KEY&action=report&type=tracking_landing_pages_adwords&date_begin=20210518&date_end=20210524&url=*.apple.com%2F*&linktype_filter=0&display_sort=1_mc_desc
```

## Example Response

> The source response example was truncated mid-payload; reproduced here verbatim.

```json
{
  "total": 4,
  "state": "0",
  "limit": 500,
  "offset": 0,
  "new": 0,
  "lost": 2,
  "keywords": 200,
  "Pc": { "http": 0, "https": 3 },
  "data": {
    "0": {
      "Ur": "https://music.apple.com/",
      "Tp": "lost",
      "Dt": {
        "20210518": {
          "Mc": 1
        }
      }
    }
  }
}
```

## See Also

- [Organic landing pages report](projects_tracking_landing_pages_organic.md)
- [Adwords positions report](projects_tracking_position_adwords.md)
- [Position Tracking Overview](projects_tracking_overview.md) — sortings, filters
