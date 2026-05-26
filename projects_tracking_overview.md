# Position Tracking API — Overview

The Position Tracking API lets you monitor keyword rankings, visibility, and competitors' performance across search engines and locations. Provides access to ranking data for specific keywords, devices, and regions.

## Method Groups

Position Tracking methods are divided into three groups, each with its own base URL.

**Management** — create campaigns and manage email notifications.

```
https://api.semrush.com/management/v1/projects/{projectID or campaignID}/tracking/
```

**Available regions** — list of countries with their regions and cities.

```
https://api.semrush.com/management/v1/info/
```

**Reports** — campaign report data. All report requests use HTTP GET.

```
https://api.semrush.com/reports/v1/projects/{campaignID}/tracking/
```

All requests require the `{campaignID}` placeholder to be replaced with a real campaign ID. See [how to get your campaign ID](projects_api_overview.md#get-your-campaign-id).

## URL Parameter Mask

Use the appropriate mask in requests with the `url` parameter:

| URL Type | Mask Example |
|---|---|
| `rootdomain` | `*.ebay.com/*` |
| `subdomain` | `www.ebay.com/*` |
| `subfolder` | `*.ebay.com/motors/*` |
| `URL` | `http://www.ebay.com/motors/` |

Some requests — including [Organic landing pages](projects_tracking_landing_pages_organic.md), [Organic competitors discovery](projects_tracking_competitors_organic.md), and [Adwords competitors discovery](projects_tracking_competitors_adwords.md) — require a URL without a mask. For example, the `url` parameter for the `rootdomain` URL type will be `ebay.com`.

## URL Encoding

Encode parameter values containing special characters such as `/` in the URL.

When using the `display_tags_condition` parameter, tag values containing special characters must be **double-encoded**. For example, the `name&co` tag must be submitted as `name%2526co` — `%25` decodes to `%`, then `%26` decodes to `&`.

## Tag Sanitization Rules

All tags in campaign update or filter parameters are sanitized before use:

- Any characters other than letters, digits, spaces, or these allowed symbols: `.`, `&`, `-`, `$`, `+`, `'`, `#` — are removed.
- Two or more consecutive spaces are replaced with a single space.
- Three or more consecutive underscores are replaced with two underscores.
- Underscores at the start or end of tags are trimmed.
- Tags are converted to lowercase and spaces are trimmed.

## Sortings

Used in the `display_sort` parameter. `{DATE}` is a date in `YYYYMMDD` format. `{DOMAIN_N}` is a domain number (`0`, `1`, `2`, `3`, `4`).

| Value | Description |
|---|---|
| `ad_asc` / `ad_desc` | By difference in average position over the selected period |
| `0_av_asc` / `0_av_desc` | By average position on the start date |
| `1_av_asc` / `1_av_desc` | By average position on the end date |
| `av_asc` / `av_desc` | By average position |
| `{DOMAIN_N}_be_asc` / `_be_desc` | By position at the start date |
| `cd_asc` / `cd_desc` | By visibility change |
| `cl_asc` / `cl_desc` | By visibility |
| `cp_asc` / `cp_desc` | By CPC |
| `{DATE}_asc` / `{DATE}_desc` | By date |
| `{DOMAIN_N}_diff_asc` / `_diff_desc` | By position change |
| `{DOMAIN_N}_fi_asc` / `_fi_desc` | By position at the end date |
| `{DOMAIN_N}_pos_asc` / `_pos_desc` | By position at the end date |
| `0_mc_asc` / `0_mc_desc` | By number of keywords on a specific URL on SERP — start date |
| `1_mc_asc` / `1_mc_desc` | By number of keywords on a specific URL on SERP — end date |
| `md_asc` / `md_desc` | By difference in number of keywords on a specific URL on SERP |
| `0_nq_asc` / `0_nq_desc` | By volume on the start date |
| `1_nq_asc` / `1_nq_desc` | By volume on the end date |
| `nq_asc` / `nq_desc` | By volume |
| `ph_asc` / `ph_desc` | By keyword |
| `rd_asc` / `rd_desc` | By difference in volume over the period |
| `sov_asc` / `sov_desc` | By Share of Voice |
| `sovdiff_asc` / `sovdiff_desc` | By difference in Share of Voice over the period |
| `0_tr_asc` / `0_tr_desc` | By estimated traffic on the start date |
| `1_tr_asc` / `1_tr_desc` | By estimated traffic on the end date |
| `trdiff_asc` / `trdiff_desc` | By difference in estimated traffic over the period |
| `ur_asc` / `ur_desc` | By URL |
| `vi_asc` / `vi_desc` | By visibility |
| `0_vd_asc` / `0_vd_desc` | By difference in visibility over the period |

## Filters

Add the `display_filter` parameter with a URL-encoded string. Filter parameters are separated by `|`. Up to **25 filter parameters** per request.

Each filter follows: `<sign>|<field>|<operation>|<value>`.

| Component | Values |
|---|---|
| `sign` | `+` (include), `-` (exclude) |
| `field` | `Ph` (Phrase), `Cp` (Average CPC in USD, Google Ads), `Nq` (Average monthly searches over last 12 months) |
| `operation` | Metrics fields: `Eq` (exactly matching), `Gt` (greater than), `Lt` (less than). Text fields: `Bw` (begins with), `Ew` (ends with), `Eq` (exactly matching), `Co` (containing) |
| `value` | String to filter for |

**Example** — keywords containing "phone", volume > 10,000, CPC > 2:

```
display_filter=+|Ph|Co|phone|+|Nq|Gt|10000|+|Cp|Gt|2
```

URL-encoded:

```
display_filter=%2B%7CPh%7CCo%7Cphone%7C%2B%7CNq%7CGt%7C10000%7C%2B%7CCp%7CGt%7C2
```

## SERP Features

Letter codes used in `serp_feature_filter` and in the `Sf` / `Lt` response fields.

| Code | Name | Description |
|---|---|---|
| `aai` | Ask AI | An AI-generated response. |
| `adb` | Google Ads bottom | Ads at the bottom of the first search results page. |
| `adt` | Google Ads top | Ads at the top of the first search results page. |
| `aic` | AI chat | An AI-generated chat response. |
| `aim` | AI summary | A brief AI-generated summary. |
| `aio` | AI overview | A summarized AI-generated overview. |
| `ais` | AI stories | AI-generated stories. |
| `amp` | AMP | Mobile-friendly pages; Google doesn't distinguish them from other results. |
| `app` | Apps block | Block displaying apps among organic results. |
| `asr` | AI search results | Block containing links used by Google AI to generate the answer. |
| `car` | Organic carousel | Horizontally scrollable images at the top of search results. |
| `ctt` | Citations | Block containing links referenced by ChatGPT in its quotes. |
| `drp` | Double response | Block containing two ChatGPT answers for selection. |
| `flg` | Flights | Block displaying flights related to a search query. |
| `fsn` | Featured snippet | Short answer to the search query with a third-party link. |
| `geo` | Local pack | Map with three local results at the top of the SERP. |
| `hot` | Hotels | Block displaying hotels related to a search query. |
| `img` | Images | Collection of images, usually at the top of the SERP. |
| `ind` | Indented | List of related pages from the highest organic result. |
| `job` | Jobs | Job listings related to a search query. |
| `kng` | Knowledge panel | Block with brief information about a topic, to the right of organic results. |
| `knw` | Instant answer | Direct answer in a gray-bordered box at the top. |
| `mac` | Media actions | Block showing details about movies/TV shows and links to streaming platforms. |
| `new` | Top stories | Card-style snippet with up to three news results. |
| `org` | Organic | An organic search result. |
| `rel` | People also ask | Expandable grid box of related questions between search results. |
| `res` | Related searches | List of related searches among organic results. |
| `rev` | Reviews | Organic results marked with star ratings. |
| `rsp` | Response | Block containing a ChatGPT answer. |
| `shp` | Shopping ads | Horizontally scrollable paid shopping results at the top for product queries. |
| `spb` | Sports Onebox | Block showing platforms for live sporting events. |
| `stl` | Sitelinks | Set of links under the main organic result for brand queries. |
| `tea` | Teaser | Map with three local business results (hotels and restaurants) at the top. |
| `twt` | Twitter | Carousel of tweets among organic results. |
| `vib` | Featured video | Video result at the top of all organic results. |
| `vid` | Video | Video results with thumbnails among organic results. |

### `serp_feature_filter`

Filter [Organic positions](projects_tracking_position_organic.md) and [Organic visibility index](projects_tracking_visibility_organic.md) reports for keywords containing a specific SERP feature, optionally scoped to a specific domain ranking inside the feature.

Format: `-<sf>,<domain>`

- `-` (optional): Excludes the specified SERP feature if present.
- `sf`: SERP feature code (e.g., `geo` for Local Pack, `fsn` for Featured Snippet).
- `domain` (optional): Index in the `url` parameter list. Numbering starts at `0`.

**Examples**

Keywords with a Featured Snippet for the first domain (apple.com):

```
https://api.semrush.com/reports/v1/projects/{campaignID}/tracking/?type=tracking_position_organic&key=YOUR_API_KEY&action=report&url=*.apple.com%2F*:*.amazon.com&serp_feature_filter=fsn,0
```

Keywords with a Featured Snippet for the second domain (amazon.com):

```
https://api.semrush.com/reports/v1/projects/{campaignID}/tracking/?type=tracking_position_organic&key=YOUR_API_KEY&action=report&url=*.apple.com%2F*:*.amazon.com%2F*&serp_feature_filter=fsn,1
```

## Method Index

**Management**
- [Create a Position Tracking campaign](projects_tracking_create.md)
- [Enable email notifications](projects_tracking_notifications_enable.md)
- [Disable email notifications](projects_tracking_notifications_disable.md)
- [Add keywords](projects_tracking_keywords_add.md)
- [Remove keywords](projects_tracking_keywords_remove.md)
- [Add tags to keywords](projects_tracking_tags_add.md)
- [Remove tags from keywords](projects_tracking_tags_remove.md)
- [Add competitors](projects_tracking_competitors_add.md)
- [Remove competitors](projects_tracking_competitors_remove.md)
- [Get a list of campaigns](projects_tracking_campaigns_list.md)

**Available regions**
- [Universal location search](projects_tracking_locations.md)

**Reports**
- [Campaign dates](projects_tracking_campaign_dates.md)
- [Organic overview](projects_tracking_overview_organic.md)
- [Adwords overview](projects_tracking_overview_adwords.md)
- [Organic positions](projects_tracking_position_organic.md)
- [Adwords positions](projects_tracking_position_adwords.md)
- [Organic competitors discovery](projects_tracking_competitors_organic.md)
- [Adwords competitors discovery](projects_tracking_competitors_adwords.md)
- [Organic visibility index](projects_tracking_visibility_organic.md)
- [Adwords visibility index](projects_tracking_visibility_adwords.md)
- [Organic landing pages](projects_tracking_landing_pages_organic.md)
- [Adwords landing pages](projects_tracking_landing_pages_adwords.md)
