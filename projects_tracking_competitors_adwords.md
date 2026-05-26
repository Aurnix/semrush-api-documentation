# Position Tracking — Adwords Competitors Discovery Report

**Price:** 1000 API units per competitor

Lists the domains that appear in Google's paid search results for the keywords from a tracking campaign for the chosen location, along with their average position and visibility.

## Endpoint

```
GET https://api.semrush.com/reports/v1/projects/{campaignID}/tracking/
```

## Parameters

| Parameter | Required | Type | Description |
|---|---|---|---|
| `key` | Yes | string | API key from Subscription info > API units. |
| `action` | Yes | string | Value: `report`. |
| `type` | Yes | string | Value: `tracking_competitors_adwords`. |
| `url_type` | No | string | Type of competitor URLs. Allowed: `rootdomain`, `subdomain`, `subfolder`, `url`. Defaults to the campaign setting. |
| `main_domain` | No | string | Domain URL (without a mask) returned in a special block at the top of the competitors list. |
| `url` | No | string | Competitor(s) (with a mask) to be returned. Multiple: `url={domain1}:{domain2}`. |
| `black_list` | No | string | Excluded domains, separated by `|`. |
| `top_start` | No | integer | Top of the SERP position range to search competitors in. |
| `top_end` | No | integer | Bottom of the SERP position range to search competitors in. |
| `date_begin` | No | date | Start date in `YYYYMMDD` format. |
| `date_end` | No | date | End date in `YYYYMMDD` format. |
| `display_limit` | No | integer | Number of returned results. Default `10`. |
| `display_offset` | No | integer | Number of lines to skip. |
| `display_sort` | No | string | Allowed: `av_asc`, `av_desc`, `cd_asc`, `cd_desc`, `cl_asc`, `cl_desc`, `{DATE}_asc`, `{DATE}_desc`, `ur_asc`, `ur_desc`. See [Sortings](projects_tracking_overview.md#sortings). |

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
GET /?key=YOUR_API_KEY&action=report&type=tracking_competitors_adwords&date_begin=20210518&date_end=20210524&top_start=1&top_end=10&url_type=rootdomain&display_sort=20210524_desc&main_domain=apple.com
```

## Example Response

```json
{
  "Md": {
    "Dt": {
      "20210518": { "Mc": 4, "Av": 11.45679,  "Sq": 2,  "Cl": 4.938272,  "Sov": 1.399827, "Tr": 2416.666667, "Tc": 4625.166667 },
      "20210524": { "Mc": 2, "Av": 11.728395, "Sq": 1,  "Cl": 2.469136,  "Sov": 0.924851, "Tr": 1596.666667, "Tc": 3659.166667 },
      "Diff":     { "Mc": -2,"Av": 0.271605,  "Sq": -1, "Cl": -2.469136, "Sov": -0.474976,"Tr": -820,         "Tc": -966 }
    },
    "Cd": -2.469136,
    "Ur": "apple.com",
    "Ps": 5
  },
  "total": 45,
  "state": "0",
  "limit": 10,
  "offset": 0,
  "keywords_count": 200,
  "data": {
    "0": {
      "Dt": {
        "20210518": { "Mc": 22, "Av": 10.8,  "Sq": 3, "Cl": 11, "Sov": 1.013759, "Tr": 629766.67, "Tc": 687222.33 },
        "20210524": { "Mc": 16, "Av": 11.13, "Sq": 2, "Cl": 8,  "Sov": 0.833576, "Tr": 517833.33, "Tc": 515993.67 },
        "Diff":     { "Mc": -6, "Av": 0.33,  "Sq": 0, "Cl": -3, "Sov": -0.180183,"Tr": -111933.33,"Tc": -171228.67 }
      },
      "Cd": -3,
      "Ur": "apple.com"
    }
  }
}
```

## See Also

- [Organic competitors discovery report](projects_tracking_competitors_organic.md)
- [Add competitors to a tracking campaign](projects_tracking_competitors_add.md)
- [Position Tracking Overview](projects_tracking_overview.md) — sortings, URL mask
