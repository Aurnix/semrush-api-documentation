# SEO API — Backlinks

**Price:** 40 API units per line

Lists backlinks for a domain, root domain, or URL.

## Endpoint

```
GET https://api.semrush.com/analytics/v1/
```

## Parameters

| Parameter | Required | Description |
|---|---|---|
| `type` | Yes | Report type. Value: `backlinks` |
| `key` | Yes | API key from Subscription info > API units. |
| `target` | Yes | Root domain, subdomain, or URL to investigate. Example: `example.com`, `www.example.com`, or `http://www.example.com` |
| `target_type` | Yes | Type of target. Values: `root_domain`, `domain` (use for subdomains), `url` |
| `export_columns` | No | Comma-separated columns to return. Defaults to: `page_score,source_title,source_url,target_url,anchor,external_num,internal_num,first_seen,last_seen`. Note: `page_score` returns the same data as `page_ascore`; use `page_ascore` to request it explicitly. |
| `display_sort` | No | Column to sort by. Default: `page_ascore_desc`. Values: `page_ascore_asc`, `page_ascore_desc`, `last_seen_asc`, `last_seen_desc`, `first_seen_asc`, `first_seen_desc` |
| `display_limit` | No | Number of results to return. Default and value of `0`: 10,000. Range: `0–1,000,000`. |
| `display_offset` | No | Number of results to skip before returning data. If used, increase `display_limit` by the offset value. |
| `display_filter` | No | Filters to apply. Available filter fields: `type`, `zone`, `ip`, `refdomain`, `anchor`, `newlink`, `lostlink`, `urlanchor`, `redirects`. Note: `urlanchor` cannot be used for domains with a large backlink profile. |

## Export Columns

| Column | Description |
|---|---|
| `page_ascore` | Page Authority Score — URL quality metric based on backlinks, referring domains, organic traffic. (`page_score` is an alias.) |
| `response_code` | Server response code of the source page. |
| `source_size` | Size of source page in bytes. |
| `external_num` | Number of external links on the source page. |
| `internal_num` | Number of internal links on the source page. |
| `redirect_url` | Last URL in a redirect chain. |
| `source_url` | URL of the source (linking) page. |
| `source_title` | Title of the source page. |
| `image_url` | URL of the image backlink's location. |
| `target_url` | URL of the target (linked) page. |
| `target_title` | Title of the target page. |
| `anchor` | Clickable backlink text. |
| `image_alt` | Alt text of the backlink image. |
| `last_seen` | Unix timestamp when Semrush last noticed the backlink. |
| `first_seen` | Unix timestamp when Semrush first noticed the backlink. |
| `nofollow` | Whether the link is nofollow. Values: `true`, `false`. |
| `form` | Whether the link is from a form. Values: `true`, `false`. |
| `frame` | Whether the link is from an `<iframe>`. Values: `true`, `false`. |
| `image` | Whether the link is from an image. Values: `true`, `false`. |
| `sitewide` | Whether the link appears on multiple pages of the source site. Values: `true`, `false`. |
| `newlink` | Whether the link is new. Values: `true`, `false`. |
| `lostlink` | Whether the link is lost. Values: `true`, `false`. |

## Example Request

Filter for new follow backlinks:

```
https://api.semrush.com/analytics/v1/?key=YOUR_API_KEY&type=backlinks&target=searchenginejournal.com&target_type=root_domain&export_columns=page_ascore,source_title,source_url,target_url,anchor,external_num,internal_num,first_seen,last_seen&display_limit=5&display_filter=%2B%7Ctype%7C%7Cnewlink%7C%2B%7Ctype%7C%7Cfollow
```

## Example Response

```
page_ascore;source_title;source_url;target_url;anchor;external_num;internal_num;first_seen;last_seen
80;JDN : E-business, FinTech, Big Data, IoT...;https://www.journaldunet.com/;https://www.searchenginejournal.com/duckduckgo-.../343073/#close;A partir de mars 2020 DuckDuckGo...;137;177;1578929242;1578990011
76;cnBeta.COM - 中文业界资讯站;https://www.cnbeta.com/;https://www.searchenginejournal.com/duckduckgo-.../343073/#close;将成为欧盟 Android 设备的默认搜索引擎选项;68;558;1578902621;1578928080
71;Podcast Alley - Your Place for Podcasting News;https://www.podcastalley.com/;https://www.searchenginejournal.com/bing-pages.../342897/;Introducing Bing Pages & This Week's Digital Marketing News [PODCAST];94;10;1578913376;1578917297
```
