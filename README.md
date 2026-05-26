# Semrush API Documentation — LLM Index

> A complete, LLM-ingestible reference for the Semrush API surface: SEO, Trends, Projects (API key + OAuth 2.0), Position Tracking, Site Audit, Listing Management, and Map Rank Tracker. Each link below points to a single endpoint or concept page; descriptions include the pricing model so cost-aware agents can plan requests before fetching.

## How to use this index

- **One file per endpoint.** Each `.md` is self-contained: title, price, description, endpoint URL, parameter table, example request, example response.
- **Pricing model varies.** SEO endpoints are charged per line of CSV returned (with a higher historical-data rate); some Trends endpoints are per request, others per line. Listing Management and Map Rank Tracker do **not** consume API units.
- **Two response formats.** SEO + Trends return CSV. Projects + Local return JSON.
- **Cross-references are relative.** Links resolve inside this repository; column codes link back to [seo_api_overview.md](seo_api_overview.md), country/database codes to its `#databases` section.
- **For agents:** read [quick_start.md](quick_start.md) and the relevant API overview before composing a call. Always check unit balance ([api_unit_balance.md](api_unit_balance.md)) for SEO/Trends/Projects-API-key requests, since partial billing applies when the balance runs low.

---

## Start here

- [README.md](README.md): Project description (LLM-readable mirror of the Semrush docs).
- [quick_start.md](quick_start.md): Build your first API call — get the key, structure the URL, encode special chars, retrieve and process data.
- [authorization.md](authorization.md): API key vs. OAuth 2.0; Device Authorization Grant flow (recommended) and Semrush Auth flow; token refresh.
- [api_unit_balance.md](api_unit_balance.md): How units are consumed, free balance-check endpoints (Standard + Trends), cost optimization, partial responses, the API query log.
- [faq.md](faq.md): Common questions — Standard vs. Trends, AI traffic measurement, unit consumption models, UI vs. API discrepancies.
- [troubleshooting.md](troubleshooting.md): Why API data may differ from the Semrush UI; common error scenarios.

---

## API products at a glance

| Product | Auth | Format | Billing | Purpose |
|---|---|---|---|---|
| **SEO API** | API key (query) | CSV `;` | Per line (per request for a few) | Domain/keyword/backlink/competitor analytics |
| **Trends API** | API key (query) | CSV `,` | Per request (some per line) | Clickstream-based traffic + audience data |
| **Projects API (API key)** | API key | JSON | Per request | Manage projects (folders) |
| **Projects API (OAuth 2.0)** | Bearer token | JSON | Per request | Same projects ops via OAuth |
| **Position Tracking API** | API key | JSON | Per request / per keyword | Track keyword rankings, visibility, competitors |
| **Site Audit API** | API key | JSON | Per request / per snapshot | Crawl audits, issues, page-level data |
| **Listing Management API** | API key (header `Apikey`) | JSON | Free (Local Pro plan required) | Push business locations to directories |
| **Map Rank Tracker API** | OAuth 2.0 | JSON | Free (uses Map Rank credits) | Geo-grid local rankings, heatmaps, competitors |

---

## SEO API

CSV `;`-delimited responses. Base URL: `https://api.semrush.com/`. Auth: `?key=<KEY>`. Per-line pricing; historical pricing is 5× the live rate on most reports.

### Overview & shared reference

- [seo_api_overview.md](seo_api_overview.md): **Canonical reference.** Full `export_columns` glossary (codes → response columns), regional databases, filters / sortings, error codes, response format. Link any column code (`Ph`, `Po`, `Cp`, `Kd`, `Fp`, `Fk`, `In`, etc.) back to this file.

### Domain reports

- [seo_domain_organic.md](seo_domain_organic.md): Keywords a domain ranks for in Google's top 100 organic results. Supports daily rankings (last 31 days) and monthly back to 2012–2016. 10/50 units per line.
- [seo_domain_adwords.md](seo_domain_adwords.md): Keywords driving traffic to a domain via Google paid search. 20/100 per line.
- [seo_domain_ads_copies.md](seo_domain_ads_copies.md): Unique ad copies the domain ran in paid search. 40 per line.
- [seo_domain_ad_history.md](seo_domain_ad_history.md): Keywords the domain bid on in the last 12 months with paid positions. 100 per line.
- [seo_domain_organic_competitors.md](seo_domain_organic_competitors.md): Domains competing in organic search. 40/200 per line.
- [seo_domain_adwords_competitors.md](seo_domain_adwords_competitors.md): Domains competing in paid search. 40/200 per line.
- [seo_domain_pla_keywords.md](seo_domain_pla_keywords.md): Keywords triggering the domain's Product Listing Ads. 30/150 per line.
- [seo_domain_pla_copies.md](seo_domain_pla_copies.md): Unique PLA copies the domain ran. 60/300 per line.
- [seo_domain_pla_competitors.md](seo_domain_pla_competitors.md): Domains competing via PLAs. 60/300 per line.
- [seo_domain_organic_pages.md](seo_domain_organic_pages.md): Unique pages of the domain ranking in top 100 organic. 10/50 per line.
- [seo_domain_organic_subdomains.md](seo_domain_organic_subdomains.md): Subdomains of the domain ranking in top 100 organic. 10/50 per line.
- [seo_domain_vs_domain.md](seo_domain_vs_domain.md): Compare up to 5 domains by common/unique/all keywords. 80/400 per line.

### Domain overview (pick the right one)

- [seo_domain_overview.md](seo_domain_overview.md): Live or historical metrics in **one** regional database. 10/50 per line.
- [seo_domain_overview_all.md](seo_domain_overview_all.md): Same metrics across **all** databases at once. 10/50 per line.
- [seo_domain_overview_history.md](seo_domain_overview_history.md): Monthly **history** of organic + paid rankings in one database. 10 per line. Use `domain_rank_history` when you need a time series; the three reports overlap when querying the same date.
- [seo_winners_and_losers.md](seo_winners_and_losers.md): Period-over-period changes in keywords/traffic/budget across top sites. 20/100 per line.
- [seo_semrush_rank.md](seo_semrush_rank.md): Top domains ordered by Semrush organic-traffic rank. 10/50 per line.

### Keyword reports

- [seo_keyword_overview.md](seo_keyword_overview.md): Volume/CPC/competition/results for a keyword in **one** database. 10/50 per line.
- [seo_keyword_overview_all.md](seo_keyword_overview_all.md): Same, across **all** databases. 10 per line.
- [seo_keyword_overview_batch.md](seo_keyword_overview_batch.md): Same, for up to 100 keywords in one call. 10/50 per line.
- [seo_keyword_difficulty.md](seo_keyword_difficulty.md): Keyword Difficulty Index (0–100). 50 per line.
- [seo_keyword_related.md](seo_keyword_related.md): Extended related keywords, synonyms, variations. 40 per line.
- [seo_keyword_broad_match.md](seo_keyword_broad_match.md): Broad matches including the queried phrase. 20 per line.
- [seo_keyword_phrase_questions.md](seo_keyword_phrase_questions.md): Question-form variants of a keyword. 40 per line.
- [seo_keyword_organic_results.md](seo_keyword_organic_results.md): Domains ranking in top 100 organic for a keyword. 10/50 per line.
- [seo_keyword_paid_results.md](seo_keyword_paid_results.md): Domains ranking in paid results for a keyword. 20/100 per line.
- [seo_keyword_ads_history.md](seo_keyword_ads_history.md): Domains that bid on a keyword in the last 12 months. 100 per line.

### Subdomain reports

- [seo_subdomain_overview.md](seo_subdomain_overview.md): Subdomain rankings in one database. 10 per line.
- [seo_subdomain_overview_all.md](seo_subdomain_overview_all.md): Across all databases. 10/50 per line.
- [seo_subdomain_overview_history.md](seo_subdomain_overview_history.md): Historical time series. 10 per line.
- [seo_subdomain_organic.md](seo_subdomain_organic.md): Subdomain organic keywords. 10/50 per line.
- [seo_subdomain_adwords.md](seo_subdomain_adwords.md): Subdomain paid keywords. 20/100 per line.
- [seo_subdomain_organic_pages.md](seo_subdomain_organic_pages.md): Subdomain organic pages. 10/50 per line.
- [seo_subdomain_ads_copies.md](seo_subdomain_ads_copies.md): Ad copies a subdomain ran. 40 per line.

### Subfolder reports

- [seo_subfolder_overview.md](seo_subfolder_overview.md): Subfolder rankings in one database. 10/50 per line.
- [seo_subfolder_overview_all.md](seo_subfolder_overview_all.md): Across all databases. 10/50 per line.
- [seo_subfolder_overview_history.md](seo_subfolder_overview_history.md): Historical time series. 10 per line.
- [seo_subfolder_organic.md](seo_subfolder_organic.md): Subfolder organic keywords. 10/50 per line.
- [seo_subfolder_adwords.md](seo_subfolder_adwords.md): Subfolder paid keywords. 20/100 per line.
- [seo_subfolder_organic_pages.md](seo_subfolder_organic_pages.md): Subfolder organic pages. 10/50 per line.
- [seo_subfolder_ads_copies.md](seo_subfolder_ads_copies.md): Ad copies a subfolder ran. 40 per line.

### URL reports

- [seo_url_overview.md](seo_url_overview.md): URL rankings in one database. 10/50 per line.
- [seo_url_overview_all.md](seo_url_overview_all.md): Across all databases. 10/50 per line.
- [seo_url_overview_history.md](seo_url_overview_history.md): Historical time series for a URL. 10 per line.
- [seo_url_organic.md](seo_url_organic.md): Organic keywords for a specific URL. 10/50 per line.
- [seo_url_adwords.md](seo_url_adwords.md): Paid keywords for a specific URL. 20/100 per line.

### Backlink Analytics

- [seo_backlinks_overview.md](seo_backlinks_overview.md): Summary (counts, refdomains, IPs) for a target. **40 per request** (not per line).
- [seo_backlinks.md](seo_backlinks.md): Individual backlinks for a target. 40 per line.
- [seo_backlinks_anchors.md](seo_backlinks_anchors.md): Anchor texts with backlink + refdomain counts. 40 per line.
- [seo_backlinks_pages.md](seo_backlinks_pages.md): Indexed pages with backlink/link counts. 40 per line.
- [seo_backlinks_refdomains.md](seo_backlinks_refdomains.md): Referring domains. 40 per line.
- [seo_backlinks_refips.md](seo_backlinks_refips.md): Referring IP addresses. 40 per line.
- [seo_backlinks_tld.md](seo_backlinks_tld.md): Referring domain distribution by TLD. 40 per line.
- [seo_backlinks_geo.md](seo_backlinks_geo.md): Referring domains by country (IP-based). 40 per line.
- [seo_backlinks_categories.md](seo_backlinks_categories.md): Categories the queried domain belongs to. **50 per request.**
- [seo_backlinks_categories_profile.md](seo_backlinks_categories_profile.md): Categories of the domain's referring domains. 40 per line.
- [seo_backlinks_ascore_profile.md](seo_backlinks_ascore_profile.md): Refdomain distribution by Authority Score (0–100). **100 per request.**
- [seo_backlinks_competitors.md](seo_backlinks_competitors.md): Domains with similar backlink profiles. 40 per line.
- [seo_backlinks_comparison.md](seo_backlinks_comparison.md): Batch comparison of backlink profiles across targets. 40 per line.
- [seo_backlinks_matrix.md](seo_backlinks_matrix.md): Backlinks sent to target + competitors from shared refdomains. 40 per line.
- [seo_backlinks_historical.md](seo_backlinks_historical.md): Monthly historical backlink/refdomain trends. 40 per line.

### Tutorials (SEO)

- [seo_tutorial_keyword_gaps.md](seo_tutorial_keyword_gaps.md): Find untapped keywords with Domain vs. Domain.
- [seo_tutorial_ai_overview_impact.md](seo_tutorial_ai_overview_impact.md): Measure Google AI Overview impact on traffic.
- [seo_tutorial_google_sheets.md](seo_tutorial_google_sheets.md): Import SEO API CSV into Google Sheets.

---

## Trends API

CSV `,`-delimited responses. Base URL: `https://api.semrush.com/analytics/ta/api/v3/`. Auth: `?key=<KEY>`. 10 RPS per account. Empty responses are charged for **most** endpoints — exceptions noted below.

- [trends_api_overview.md](trends_api_overview.md): Plans (Basic vs. Premium), request structure, data availability windows, rate limits, billing.
- [trends_api_resources.md](trends_api_resources.md): Lookup tables — industry category codes (for `category` param), country codes, subcontinent/continent codes.

### Traffic

- [trends_traffic_summary.md](trends_traffic_summary.md): Multi-target traffic metrics (visits, uniques, pages/visit, duration, bounce). 1 per line. **Empty responses not charged.**
- [trends_daily_traffic.md](trends_daily_traffic.md): Day-by-day traffic. 1 per request. **Empty responses not charged.**
- [trends_weekly_traffic.md](trends_weekly_traffic.md): Week-by-week traffic. 1 per request. **Empty responses not charged.**
- [trends_traffic_rank.md](trends_traffic_rank.md): Domains sorted by traffic for benchmarking. 1 per request.
- [trends_traffic_sources.md](trends_traffic_sources.md): Channel breakdown — direct/referral/search/social/email/paid/display/AI. 1 per request.
- [trends_traffic_destinations.md](trends_traffic_destinations.md): Where users go after leaving the target. 1 per request.
- [trends_top_pages.md](trends_top_pages.md): Most-visited pages on a domain/subdomain/subfolder. 1 per request.
- [trends_subdomains.md](trends_subdomains.md): Top subdomains by traffic. 1 per request.
- [trends_subfolders.md](trends_subfolders.md): Top subfolders by traffic. 1 per request.
- [trends_geo_distribution.md](trends_geo_distribution.md): Traffic share by country/subcontinent/continent. 1 per request.
- [trends_purchase_conversion.md](trends_purchase_conversion.md): Monthly purchase-conversion rate. 1 per request.
- [trends_data_accuracy.md](trends_data_accuracy.md): Reliability metric for a domain's traffic data. 1 per request.
- [trends_industry_categories.md](trends_industry_categories.md): All domains in a category with traffic + demographics. **500 per request.**

### Audience demographics & interests

- [trends_audience_insights.md](trends_audience_insights.md): Audience overlap (other domains the audience visits). 1 per request.
- [trends_audience_interests.md](trends_audience_interests.md): Interest categories for the audience. 1 per request.
- [trends_age_sex_distribution.md](trends_age_sex_distribution.md): Age × sex breakdown. 1 per request.
- [trends_household_distribution.md](trends_household_distribution.md): Household-size breakdown. 1 per request.
- [trends_income_distribution.md](trends_income_distribution.md): Income-level breakdown. 1 per request.
- [trends_education_distribution.md](trends_education_distribution.md): Education-level breakdown. 1 per request.
- [trends_occupation_distribution.md](trends_occupation_distribution.md): Occupation breakdown. 1 per request.
- [trends_social_media.md](trends_social_media.md): Social-platform preferences of the audience. 1 per request.

### Tutorials (Trends)

- [trends_tutorial_competitor_analysis.md](trends_tutorial_competitor_analysis.md): End-to-end competitor benchmarking against top 5 rivals (~30 units total).

---

## Projects API

Manage projects (folders that contain Position Tracking / Site Audit / etc. campaigns). Two parallel surfaces: API key (legacy-friendly, returns custom error codes) and OAuth 2.0 (returns HTTP status codes).

- [projects_api_overview.md](projects_api_overview.md): Endpoint groups, auth, response format, error codes (70/120/130/131/132/...), how to find project + campaign IDs.

### Projects (API key)

- [projects_list.md](projects_list.md): List all projects. 100 per request.
- [projects_get.md](projects_get.md): Get one project by ID. 100 per request.
- [projects_create.md](projects_create.md): Create a new project. 100 per request.
- [projects_update.md](projects_update.md): Rename a project. 100 per request.
- [projects_delete.md](projects_delete.md): Delete project + all campaigns in activated tools. 100 per request.

### Projects (OAuth 2.0)

Same operations, OAuth-authorized. Same 100/request pricing.

- [projects_oauth_list.md](projects_oauth_list.md): `ProjectsList`.
- [projects_oauth_get.md](projects_oauth_get.md): `GetProject`.
- [projects_oauth_create.md](projects_oauth_create.md): `CreateProject`.
- [projects_oauth_update.md](projects_oauth_update.md): `UpdateProject`.
- [projects_oauth_delete.md](projects_oauth_delete.md): `RemoveProject`.

### Position Tracking API

Track keyword rankings, visibility, and competitors across search engines and locations. Base URL group documented in the overview.

- [projects_tracking_overview.md](projects_tracking_overview.md): Method groups, base URLs, campaign model.

**Campaign management**

- [projects_tracking_create.md](projects_tracking_create.md): Create a tracking campaign in a project. 100 per request.
- [projects_tracking_campaigns_list.md](projects_tracking_campaigns_list.md): List campaigns in a project. 100 per request.
- [projects_tracking_campaign_dates.md](projects_tracking_campaign_dates.md): Dates when campaign data was harvested. 100 per request.
- [projects_tracking_locations.md](projects_tracking_locations.md): Universal location search (by ID/type/name). 100 per request.
- [projects_tracking_notifications_enable.md](projects_tracking_notifications_enable.md): Enable weekly email reports. 100 per request.
- [projects_tracking_notifications_disable.md](projects_tracking_notifications_disable.md): Disable weekly email reports. 100 per request.

**Keywords & tags**

- [projects_tracking_keywords_add.md](projects_tracking_keywords_add.md): Add keywords to a campaign. **100 per keyword added.**
- [projects_tracking_keywords_remove.md](projects_tracking_keywords_remove.md): Remove tracked keywords. 100 per request.
- [projects_tracking_tags_add.md](projects_tracking_tags_add.md): Assign up to 5 tags per keyword. 100 per request.
- [projects_tracking_tags_remove.md](projects_tracking_tags_remove.md): Remove tags. 100 per request.

**Competitors**

- [projects_tracking_competitors_add.md](projects_tracking_competitors_add.md): Add up to 20 competitor domains. 100 per request.
- [projects_tracking_competitors_remove.md](projects_tracking_competitors_remove.md): Remove competitors. 100 per request.
- [projects_tracking_competitors_organic.md](projects_tracking_competitors_organic.md): Discover organic competitors. **1000 per competitor.**
- [projects_tracking_competitors_adwords.md](projects_tracking_competitors_adwords.md): Discover paid competitors. **1000 per competitor.**

**Reports**

- [projects_tracking_overview_organic.md](projects_tracking_overview_organic.md): Organic SERP overview (new/lost/improved/declined counts). 100 per request.
- [projects_tracking_overview_adwords.md](projects_tracking_overview_adwords.md): Paid SERP overview. 100 per request.
- [projects_tracking_position_organic.md](projects_tracking_position_organic.md): Per-keyword organic positions (supports ChatGPT and other engines configured on the campaign). **100 per keyword added.**
- [projects_tracking_position_adwords.md](projects_tracking_position_adwords.md): Per-keyword paid positions. **100 per keyword added.**
- [projects_tracking_visibility_organic.md](projects_tracking_visibility_organic.md): Organic visibility index over time. 100 per request.
- [projects_tracking_visibility_adwords.md](projects_tracking_visibility_adwords.md): Paid visibility index over time. 100 per request.
- [projects_tracking_landing_pages_organic.md](projects_tracking_landing_pages_organic.md): Organic landing-page URLs ranking for campaign keywords. **1000 per landing page.**
- [projects_tracking_landing_pages_adwords.md](projects_tracking_landing_pages_adwords.md): Paid landing-page URLs. **1000 per landing page.**

### Site Audit API

Crawl audits, technical SEO issues, page-level data.

- [projects_siteaudit_overview.md](projects_siteaudit_overview.md): Method groups, base URLs, project-ID placeholder convention.
- [projects_siteaudit_enable.md](projects_siteaudit_enable.md): Enable the Site Audit tool for a project. 100 per request.
- [projects_siteaudit_edit.md](projects_siteaudit_edit.md): Edit an existing Site Audit campaign (schedule, scope, page limit, JS rendering). 100 per request.
- [projects_siteaudit_launch.md](projects_siteaudit_launch.md): Start a new audit, returns snapshot ID. 100 per request.
- [projects_siteaudit_info.md](projects_siteaudit_info.md): Most-recent-audit summary (errors/warnings/notices, checks, crawl progress). 100 per request.
- [projects_siteaudit_snapshots.md](projects_siteaudit_snapshots.md): List previous audit snapshot IDs + completion dates. 100 per request.
- [projects_siteaudit_snapshot.md](projects_siteaudit_snapshot.md): One snapshot's full overview (score, issues, deltas). **10,000 per request.**
- [projects_siteaudit_history.md](projects_siteaudit_history.md): Audit results over a period. **10,000 per request / per snapshot returned** — multiplies for multi-snapshot queries.
- [projects_siteaudit_issue_detail.md](projects_siteaudit_issue_detail.md): Affected URLs + detection date for a specific issue (latest snapshot only). 100 per request.
- [projects_siteaudit_issues_meta.md](projects_siteaudit_issues_meta.md): Text descriptions of every issue type with cause + remediation guidance. 100 per request.
- [projects_siteaudit_page.md](projects_siteaudit_page.md): Single crawled page with all detected issues. **1,000 per request.**
- [projects_siteaudit_page_list.md](projects_siteaudit_page_list.md): Look up page IDs by URL substring (feeds into `siteaudit_page`). 100 per request.

### Tutorials (Projects)

- [projects_tutorial_ai_serp_visibility.md](projects_tutorial_ai_serp_visibility.md): Monitor and optimize visibility in AI SERP features (Google AI Overview, Bing Ask AI / AI Chat) via Position Tracking.

---

## Local API

JSON responses with a `{ meta, data | error }` envelope. Does **not** consume Semrush API units. Listing Management uses API-key-header auth (`Authorization: Apikey <KEY>`); Map Rank Tracker uses OAuth 2.0 Bearer tokens.

- [local_api_overview.md](local_api_overview.md): Shared envelope, HTTP status codes (400/401/403/404/409/429/499/550/551/553/554), error formats for current vs. deprecated Listing Management vs. Map Rank Tracker.

### Listing Management API (current)

Requires Semrush Local Pro or Business plan. Base URL: `https://api.semrush.com/apis/v4/local/v1/`.

- [local_listing_overview.md](local_listing_overview.md): Base URL, pagination, `update_mask` PATCH semantics, location status lifecycle.
- [local_listing_categories.md](local_listing_categories.md): Paginated business categories by country (feed `id` into create/update).
- [local_listing_list.md](local_listing_list.md): List all locations.
- [local_listing_get.md](local_listing_get.md): Get one location by ID.
- [local_listing_create.md](local_listing_create.md): Create a location. Consumes one Local Pro limit; released on `FAILED`.
- [local_listing_update.md](local_listing_update.md): PATCH a location (only `update_mask` fields are touched).

### Map Rank Tracker API

OAuth 2.0 required. Uses Map Rank Tracker **credits** (not API units); credits reset monthly and do not roll over. Base URL: `https://api.semrush.com/apis/v4/map-rank-tracker/v0/`.

- [local_map_rank_overview.md](local_map_rank_overview.md): Base URL, credit model.
- [local_map_rank_campaigns_list.md](local_map_rank_campaigns_list.md): `GetCampaigns` — paginated, searchable by name/address.
- [local_map_rank_campaign_get.md](local_map_rank_campaign_get.md): `GetCampaign` — single campaign detail.
- [local_map_rank_campaign_create.md](local_map_rank_campaign_create.md): `CreateCampaign` — new geo-grid campaign.
- [local_map_rank_campaign_update.md](local_map_rank_campaign_update.md): `UpdateCampaign` — partial update; unmentioned fields untouched.
- [local_map_rank_campaign_delete.md](local_map_rank_campaign_delete.md): `DeleteCampaign` — permanently delete campaign + data.
- [local_map_rank_collect.md](local_map_rank_collect.md): `CollectCampaign` — triggers data collection; **costs `grid_points × keywords` credits.**
- [local_map_rank_keyword_statuses.md](local_map_rank_keyword_statuses.md): `GetKeywordStatuses` — per-keyword status for a campaign.
- [local_map_rank_heatmap.md](local_map_rank_heatmap.md): `GetHeatmap` — position at each grid point + diff vs. previous report.
- [local_map_rank_metrics.md](local_map_rank_metrics.md): `GetMetrics` — time-series average position + Share of Voice.
- [local_map_rank_top_competitors.md](local_map_rank_top_competitors.md): `GetTopCompetitors` — main business + paginated top competitors with avg position + SoV.
- [local_map_rank_limits.md](local_map_rank_limits.md): `GetUserLimits` — current credit usage and plan caps.

---

## Disambiguation guide

When the user asks for a concept that maps to multiple endpoints, pick by these rules:

- **Domain rankings**: live single-database → `seo_domain_overview.md`; all databases → `seo_domain_overview_all.md`; monthly time series → `seo_domain_overview_history.md`.
- **Keyword volume/CPC**: one keyword, one database → `seo_keyword_overview.md`; one keyword, all databases → `seo_keyword_overview_all.md`; up to 100 keywords at once → `seo_keyword_overview_batch.md`.
- **Competitor lists**: organic → `seo_domain_organic_competitors.md`; paid → `seo_domain_adwords_competitors.md`; PLA → `seo_domain_pla_competitors.md`; backlink-profile similarity → `seo_backlinks_competitors.md`.
- **Backlinks summary vs. listing**: summary metrics → `seo_backlinks_overview.md` (per request); individual links → `seo_backlinks.md` (per line).
- **Project CRUD**: API-key flow → `projects_{list,get,create,update,delete}.md`; OAuth flow → `projects_oauth_*.md`.
- **Tracked keyword positions**: Standard search engines incl. Google + ChatGPT → `projects_tracking_position_organic.md`; Google Ads → `projects_tracking_position_adwords.md`.
- **AI / LLM traffic measurement**: market-share / channel view → `trends_traffic_sources.md` (AI channel); SERP feature presence → `projects_tracking_position_organic.md` + `projects_tutorial_ai_serp_visibility.md`; AI Overview impact on existing traffic → `seo_tutorial_ai_overview_impact.md`.
- **Local rankings**: directory presence / listings → Listing Management API; map-pack / grid rankings → Map Rank Tracker API.

---

## Column-code quick reference

`export_columns` codes are an SEO-API convention. The full table (codes → response column names, descriptions, valid endpoints) lives in [seo_api_overview.md](seo_api_overview.md#export-columns). Most-used codes:

| Code | Column | Notes |
|---|---|---|
| `Ph` | Keyword | The query text. |
| `Po` / `Pp` / `Pd` | Position / Previous Position / Position Difference | Organic or paid rank in top 100. |
| `Nq` | Search Volume | Avg monthly searches, trailing 12mo. |
| `Cp` | CPC | Avg USD Google Ads cost-per-click. |
| `Co` | Competition | Advertiser density, 0–1. |
| `Kd` | Keyword Difficulty Index | 0–100, higher = harder to rank. |
| `Ur` | URL | Ranking URL. |
| `Tr` / `Tc` / `Tg` | Traffic % / Traffic Cost % / Traffic | Traffic share + cost contribution. |
| `Nr` | Number of Results | Total organic results indexed for the keyword. |
| `Td` | Trends | Comma-separated 12-month interest series. |
| `Fp` / `Fk` | SERP Features (domain ranks in / keyword triggers) | Use `FP1..FPn` / `FK1..FKn` for per-feature counts. |
| `In` | Intent | `0` Commercial, `1` Informational, `2` Navigational, `3` Transactional. |
| `Ip0..Ip3`, `Ipu` | Positions by intent | Plus unknown. |
| `It0..It3`, `Itu` | Traffic by intent | Plus unknown. |
| `Ic0..Ic3`, `Icu` | Traffic cost by intent | Plus unknown. |
| `Db` / `Dn` / `Dt` | Database / Domain / Date | Identification columns. |
| `Or` / `Ot` / `Oc` | Organic Keywords / Traffic / Cost | Domain-level totals. |
| `Ad` / `At` / `Ac` | Adwords Keywords / Traffic / Cost | Domain-level paid totals. |
| `Sh` / `Sv` | PLA Keywords / PLA Uniques | Product Listing Ads. |
| `Rk` | Rank | Semrush domain popularity rank. |

Filter operators (used in `display_filter`): `+|<field>|<op>|<value>` (include) or `-|<field>|<op>|<value>` (exclude). Ops include `Co` (contains), `Eq` (equals), `Gt`/`Lt` (gt/lt). URL-encode `|` as `%7C` and `+` as `%2B`.

---

## Maintainer notes

- [handoff_prompt.md](handoff_prompt.md): Internal authoring conventions for this corpus — filename pattern, file structure (Title → Price → Description → Endpoint → Parameters table with Required column → Deprecated Columns → Example Request → Example Response), source-fidelity quirks, when to mark columns deprecated with ⚠️. Not part of the public API surface; useful when adding or correcting files.

---

*Last updated: 2026-05. If an endpoint exists on Semrush's developer portal but is missing from this index, treat the corpus as out-of-date and fall back to the canonical source.*
