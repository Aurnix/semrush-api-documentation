# Site Audit API — Overview

The Site Audit API lets you crawl websites, identify technical SEO issues, and retrieve structured reports about site health and performance. Use it to run new audits, monitor crawl progress, and access detailed reports on errors, warnings, and notices.

## Method Groups

Site Audit methods are divided into two groups, each with its own base URL. All requests require the `{ID}` placeholder to be replaced with a real project ID. See [how to get your project ID](projects_api_overview.md#get-your-project-id).

**Management** — enable Site Audit on a project and edit campaign settings.

```
https://api.semrush.com/management/v1/projects/{ID}/siteaudit
```

**Reports** — audit results, snapshots, per-page and per-issue data.

```
https://api.semrush.com/reports/v1/projects/{ID}/siteaudit
```

## Filters

Add the `filter` parameter with a URL-encoded string. Each filter follows:

```
[+-]|field|operator|value1;...;valueN
```

| Component | Values |
|---|---|
| `sign` | `+` (include), `-` (exclude) |
| `field` | Field name to filter by, e.g. `source_url` |
| `operator` | `Bw` (begins with), `Ew` (ends with), `Eq` (equals), `Co` (contains) |
| `values` | Values separated by `;` |

**Example**

```
+|source_url|Co|semrush;site_audit
```

To apply multiple filters, repeat the `filter` parameter:

```
https://api.semrush.com/reports/v1/projects/{ID}/siteaudit/snapshot/{snapshotId}/issue/{issueId}?filter={filter1}&filter={filter2}&filter={filter3}
```

## User Agent Types

Used in `userAgentType` (Enable/Edit campaign) and `user_agent_type` (campaign info).

| Value | User Agent |
|---|---|
| `2` | GoogleBot Desktop |
| `3` | GoogleBot Mobile |
| `7` | SiteAuditBot Desktop |
| `8` | SiteAuditBot Mobile |
| `9` | OpenAI-Search |

## Issue IDs

Issue IDs returned in `defects`, `errors`, `warnings`, `notices`, and used in the [Detailed report for issue](projects_siteaudit_issue_detail.md) endpoint.

### Errors

| ID | Description |
|---|---|
| `1` | 5xx errors |
| `2` | 4xx errors |
| `3` | Title tag is missing or empty |
| `4` | Blocked from crawling |
| `6` | Duplicate title tag |
| `7` | Duplicate content |
| `8` | Broken internal links |
| `9` | Pages not crawled |
| `10` | DNS resolution issue |
| `11` | We couldn't open the page's URL |
| `13` | Broken internal images |
| `15` | Duplicate meta descriptions |
| `16` | Invalid robots.txt format |
| `17` | Invalid sitemap.xml format |
| `18` | Incorrect pages found in sitemap.xml |
| `19` | www resolve issues |
| `20` | Viewport not configured |
| `21` | Large HTML page size |
| `22` | Missing canonical tags in AMP pages |
| `26` | Non-secure pages |
| `27` | Certificate Expiration |
| `28` | Old security protocol version |
| `29` | Certificate registered to incorrect name |
| `30` | Issues with mixed content |
| `32` | Neither canonical URL nor 301 redirect from HTTP homepage |
| `33` | Redirect chains and loops |
| `34` | AMP Pages with HTML Issues |
| `35` | AMP Pages with Style and Layout Issues |
| `36` | AMP Pages with Templating Issues |
| `38` | Broken canonical URLs |
| `39` | Multiple canonical URLs |
| `40` | Meta refresh redirects |
| `41` | Broken internal JavaScript and CSS files |
| `42` | Insecure encryption algorithms |
| `43` | Sitemap file too large |
| `44` | Malformed links |
| `45` | Structured data that contains markup errors |
| `46` | Viewport width not set |
| `111` | Slow page load speed |

### Warnings

| ID | Description |
|---|---|
| `12` | Broken external links |
| `14` | Broken external images |
| `31` | Links lead to HTTP pages for HTTPS site |
| `101` | Title element is too short |
| `102` | Title element is too long |
| `103` | Missing h1 |
| `104` | Multiple h1 tags |
| `105` | Duplicate content in h1 and title |
| `106` | Missing meta description |
| `108` | Too many on-page links |
| `109` | Temporary redirects |
| `110` | Missing ALT attributes |
| `112` | Low text to HTML ratio |
| `113` | Too many URL parameters |
| `114` | Missing hreflang and lang attributes |
| `115` | Encoding not declared |
| `116` | Doctype not declared |
| `117` | Low word count |
| `120` | Incompatible plugins used |
| `121` | Frames used |
| `122` | Underscores in URL |
| `123` | Nofollow attributes in internal links |
| `124` | Sitemap.xml not specified in robots.txt |
| `125` | Sitemap.xml not found |
| `126` | HTTPS encryption not used |
| `127` | No SNI support |
| `128` | HTTP URLs in sitemap.xml for HTTPS site |
| `129` | Uncompressed pages |
| `130` | Disallowed internal resources |
| `131` | Uncompressed JavaScript and CSS files |
| `132` | Uncached JavaScript and CSS files |
| `133` | Too large JavaScript and CSS total size |
| `134` | Too many JavaScript and CSS files |
| `135` | Unminified JavaScript and CSS files |
| `136` | Warning — Too long URLs |
| `137` | Llms.txt not found |

### Notices

| ID | Description |
|---|---|
| `201` | Too long URLs |
| `202` | Nofollow attributes in external links |
| `203` | Robots.txt not found |
| `205` | No HSTS support |
| `206` | Orphaned pages (Google Analytics) |
| `207` | Orphaned sitemap pages |
| `208` | Pages have high Document Interactive Time |
| `209` | Blocked by X-Robots-Tag: noindex HTTP header |
| `210` | Disallowed external resources |
| `211` | Broken external JavaScript and CSS files |
| `212` | Page crawl depth |
| `213` | Pages with only one internal link |
| `214` | Permanent redirects |
| `215` | Resources formatted as page links |
| `216` | Links with no anchor text |
| `217` | Links with non-descriptive anchor text |
| `218` | External pages or resources with 403 HTTP status code |
| `219` | Llms.txt has formatting issues |
| `220` | Too much content |
| `221` | Outdated content |
| `222` | Low semantic HTML usage |
| `223` | Content not optimized |

## Method Index

**Management**
- [Enable Site Audit tool](projects_siteaudit_enable.md)
- [Edit campaign](projects_siteaudit_edit.md)

**Reports**
- [Get list of campaign snapshots](projects_siteaudit_snapshots.md)
- [Get text descriptions about issues](projects_siteaudit_issues_meta.md)
- [Run audit](projects_siteaudit_launch.md)
- [Get information about campaign](projects_siteaudit_info.md)
- [Get information about snapshot](projects_siteaudit_snapshot.md)
- [Detailed report for issue](projects_siteaudit_issue_detail.md)
- [Get page ID by URL](projects_siteaudit_page_list.md)
- [Get information about page](projects_siteaudit_page.md)
- [Get snapshots history](projects_siteaudit_history.md)
