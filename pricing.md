---
title: Semrush API Pricing — Per-Endpoint API Unit Consumption
description: Consolidated cost table for every endpoint in the Semrush API surface. Lists per-request / per-line / per-keyword unit consumption, historical-data surcharges, and which endpoints are free.
version: 2026.05
canonical_source: https://developer.semrush.com/api/
format: markdown
billing_units:
  api_units: SEO API, Trends API, Projects API (both API key and OAuth 2.0), Position Tracking, Site Audit
  local_pro_limits: Listing Management — Create Location (one Local Pro limit per active location; released on FAILED)
  map_rank_credits: Map Rank Tracker — CollectCampaign (grid_points × keywords credits per collection)
pricing_models:
  per_line: Cost multiplied by the number of CSV rows in the response. Partial billing applies when balance runs low.
  per_request: Fixed cost regardless of response size.
  per_keyword: Cost multiplied by the number of keywords supplied in the request (Position Tracking only).
  per_competitor: Cost multiplied by the number of competitors returned (Position Tracking discovery reports).
  per_landing_page: Cost multiplied by the number of landing pages returned (Position Tracking landing pages reports).
  per_snapshot: Cost multiplied by the number of snapshots returned (Site Audit history).
historical_surcharge: "Most SEO API per-line endpoints charge 5× the live rate when `display_date` requests historical data. Endpoints with no historical tier listed below have a single price applied to both live and historical queries."
empty_response_policy:
  seo_api: Charged for response lines actually returned. No charge if zero lines.
  trends_api: Varies by endpoint — see the "Empty charged?" column.
  projects_api: Per-request endpoints are charged regardless of result content.
  local_api: Not billed in API units.
---

# Semrush API Pricing — Per-Endpoint API Unit Consumption

> A single-page lookup of how many **API units** each endpoint consumes. Use this to estimate cost before a batch run, choose between equivalent endpoints, or decide whether `display_limit` / column trimming is worth it. Every row links back to the endpoint's full spec in this repo.

## How to read this document

- **API units** are the universal billing token for SEO, Trends, Projects, Position Tracking, and Site Audit. Check your balance with the free endpoints in [api_unit_balance.md](api_unit_balance.md).
- **Per-line** endpoints multiply the listed cost by the number of CSV rows actually returned. Cap output with `display_limit` to control cost.
- **Per-request** endpoints charge a fixed cost regardless of response size.
- **Historical** column shows the surcharge when querying historical data (typically 5× the live rate on per-line SEO endpoints). A `—` means there is no separate historical tier and the live price applies to all dates.
- **Listing Management** consumes Local Pro **location limits**, not API units. **Map Rank Tracker** consumes Map Rank Tracker **credits**, not API units. Both are tracked separately from the API-unit balance.
- For "partial billing" behavior when balance is low, see [api_unit_balance.md](api_unit_balance.md#partial-responses).

## Quick reference — billing model per product

| Product | Billing model | Where prices live | Free endpoints |
|---|---|---|---|
| **SEO API** | Per line (5 endpoints fixed per request) | This page → [SEO API](#seo-api) | `countapiunits.html` |
| **Trends API** | Per request (one is per line) | This page → [Trends API](#trends-api) | `analytics/ta/limits/key/` |
| **Projects API (API key)** | Per request | This page → [Projects API](#projects-api) | — |
| **Projects API (OAuth 2.0)** | Per request | This page → [Projects API](#projects-api-oauth-20) | — |
| **Position Tracking API** | Per request / per keyword / per competitor / per landing page | This page → [Position Tracking API](#position-tracking-api) | — |
| **Site Audit API** | Per request (some snapshot-multiplied) | This page → [Site Audit API](#site-audit-api) | — |
| **Listing Management API** | Free of API units (consumes Local Pro location limits) | This page → [Listing Management API](#listing-management-api) | All endpoints |
| **Map Rank Tracker API** | Free of API units (consumes Map Rank credits on `CollectCampaign` only) | This page → [Map Rank Tracker API](#map-rank-tracker-api) | All endpoints |

---

## Free / utility endpoints

| Endpoint | URL | Cost | Notes |
|---|---|---|---|
| Check Standard API unit balance | `GET http://www.semrush.com/users/countapiunits.html` | **Free (0 units)** | See [api_unit_balance.md](api_unit_balance.md#standard-api--check-balance). |
| Check Trends API unit balance | `GET http://api.semrush.com/analytics/ta/limits/key/{KEY}` | **Free (0 units)** | 10 RPS; see [api_unit_balance.md](api_unit_balance.md#trends-api--check-balance). |

---

## SEO API

CSV `;`-delimited responses. Base URL: `https://api.semrush.com/`. Auth: `?key=<KEY>`. Per-line pricing dominates; historical pricing is 5× the live rate on most reports.

### Domain reports

| Endpoint | Live cost | Historical cost | Billing | File |
|---|---|---|---|---|
| Domain Organic Search Keywords | 10 / line | 50 / line | per line | [seo_domain_organic.md](seo_domain_organic.md) |
| Domain Paid Search Keywords | 20 / line | 100 / line | per line | [seo_domain_adwords.md](seo_domain_adwords.md) |
| Domain Ads Copies | 40 / line | — | per line | [seo_domain_ads_copies.md](seo_domain_ads_copies.md) |
| Domain Ad History | 100 / line | — | per line | [seo_domain_ad_history.md](seo_domain_ad_history.md) |
| Competitors in Organic Search | 40 / line | 200 / line | per line | [seo_domain_organic_competitors.md](seo_domain_organic_competitors.md) |
| Competitors in Paid Search | 40 / line | 200 / line | per line | [seo_domain_adwords_competitors.md](seo_domain_adwords_competitors.md) |
| Domain PLA Search Keywords | 30 / line | 150 / line | per line | [seo_domain_pla_keywords.md](seo_domain_pla_keywords.md) |
| PLA Copies | 60 / line | 300 / line | per line | [seo_domain_pla_copies.md](seo_domain_pla_copies.md) |
| PLA Competitors | 60 / line | 300 / line | per line | [seo_domain_pla_competitors.md](seo_domain_pla_competitors.md) |
| Domain Organic Pages | 10 / line | 50 / line | per line | [seo_domain_organic_pages.md](seo_domain_organic_pages.md) |
| Domain Organic Subdomains | 10 / line | 50 / line | per line | [seo_domain_organic_subdomains.md](seo_domain_organic_subdomains.md) |
| Domain vs. Domain | 80 / line | 400 / line | per line | [seo_domain_vs_domain.md](seo_domain_vs_domain.md) |

### Domain overview

| Endpoint | Live cost | Historical cost | Billing | File |
|---|---|---|---|---|
| Domain Overview (one database) | 10 / line | 50 / line | per line | [seo_domain_overview.md](seo_domain_overview.md) |
| Domain Overview (all databases) | 10 / line | 50 / line | per line | [seo_domain_overview_all.md](seo_domain_overview_all.md) |
| Domain Overview (history) | 10 / line | — | per line | [seo_domain_overview_history.md](seo_domain_overview_history.md) |
| Winners and Losers | 20 / line | 100 / line | per line | [seo_winners_and_losers.md](seo_winners_and_losers.md) |
| Semrush Rank | 10 / line | 50 / line | per line | [seo_semrush_rank.md](seo_semrush_rank.md) |

### Keyword reports

| Endpoint | Live cost | Historical cost | Billing | File |
|---|---|---|---|---|
| Keyword Overview (one database) | 10 / line | 50 / line | per line | [seo_keyword_overview.md](seo_keyword_overview.md) |
| Keyword Overview (all databases) | 10 / line | — | per line | [seo_keyword_overview_all.md](seo_keyword_overview_all.md) |
| Batch Keyword Overview (one database) | 10 / line | 50 / line | per line | [seo_keyword_overview_batch.md](seo_keyword_overview_batch.md) |
| Keyword Difficulty | 50 / line | — | per line | [seo_keyword_difficulty.md](seo_keyword_difficulty.md) |
| Related Keywords | 40 / line | — | per line | [seo_keyword_related.md](seo_keyword_related.md) |
| Broad Match Keyword | 20 / line | — | per line | [seo_keyword_broad_match.md](seo_keyword_broad_match.md) |
| Phrase Questions | 40 / line | — | per line | [seo_keyword_phrase_questions.md](seo_keyword_phrase_questions.md) |
| Organic Results | 10 / line | 50 / line | per line | [seo_keyword_organic_results.md](seo_keyword_organic_results.md) |
| Paid Results | 20 / line | 100 / line | per line | [seo_keyword_paid_results.md](seo_keyword_paid_results.md) |
| Keyword Ads History | 100 / line | — | per line | [seo_keyword_ads_history.md](seo_keyword_ads_history.md) |

### Subdomain reports

| Endpoint | Live cost | Historical cost | Billing | File |
|---|---|---|---|---|
| Subdomain Overview (one database) | 10 / line | — | per line | [seo_subdomain_overview.md](seo_subdomain_overview.md) |
| Subdomain Overview (all databases) | 10 / line | 50 / line | per line | [seo_subdomain_overview_all.md](seo_subdomain_overview_all.md) |
| Subdomain Overview (history) | 10 / line | — | per line | [seo_subdomain_overview_history.md](seo_subdomain_overview_history.md) |
| Subdomain Organic Search Keywords | 10 / line | 50 / line | per line | [seo_subdomain_organic.md](seo_subdomain_organic.md) |
| Subdomain Paid Search Keywords | 20 / line | 100 / line | per line | [seo_subdomain_adwords.md](seo_subdomain_adwords.md) |
| Subdomain Organic Pages | 10 / line | 50 / line | per line | [seo_subdomain_organic_pages.md](seo_subdomain_organic_pages.md) |
| Subdomain Ads Copies | 40 / line | — | per line | [seo_subdomain_ads_copies.md](seo_subdomain_ads_copies.md) |

### Subfolder reports

| Endpoint | Live cost | Historical cost | Billing | File |
|---|---|---|---|---|
| Subfolder Overview (one database) | 10 / line | 50 / line | per line | [seo_subfolder_overview.md](seo_subfolder_overview.md) |
| Subfolder Overview (all databases) | 10 / line | 50 / line | per line | [seo_subfolder_overview_all.md](seo_subfolder_overview_all.md) |
| Subfolder Overview (history) | 10 / line | — | per line | [seo_subfolder_overview_history.md](seo_subfolder_overview_history.md) |
| Subfolder Organic Search Keywords | 10 / line | 50 / line | per line | [seo_subfolder_organic.md](seo_subfolder_organic.md) |
| Subfolder Paid Search Keywords | 20 / line | 100 / line | per line | [seo_subfolder_adwords.md](seo_subfolder_adwords.md) |
| Subfolder Organic Pages | 10 / line | 50 / line | per line | [seo_subfolder_organic_pages.md](seo_subfolder_organic_pages.md) |
| Subfolder Ads Copies | 40 / line | — | per line | [seo_subfolder_ads_copies.md](seo_subfolder_ads_copies.md) |

### URL reports

| Endpoint | Live cost | Historical cost | Billing | File |
|---|---|---|---|---|
| URL Overview (one database) | 10 / line | 50 / line | per line | [seo_url_overview.md](seo_url_overview.md) |
| URL Overview (all databases) | 10 / line | 50 / line | per line | [seo_url_overview_all.md](seo_url_overview_all.md) |
| URL Overview (history) | 10 / line | — | per line | [seo_url_overview_history.md](seo_url_overview_history.md) |
| URL Organic Search Keywords | 10 / line | 50 / line | per line | [seo_url_organic.md](seo_url_organic.md) |
| URL Paid Search Keywords | 20 / line | 100 / line | per line | [seo_url_adwords.md](seo_url_adwords.md) |

### Backlink Analytics

> Three Backlink endpoints are **per request** (fixed cost): Backlinks Overview, Categories, and Authority Score Profile. The rest are per line.

| Endpoint | Live cost | Historical cost | Billing | File |
|---|---|---|---|---|
| Backlinks Overview | **40 / request** | — | per request | [seo_backlinks_overview.md](seo_backlinks_overview.md) |
| Backlinks | 40 / line | — | per line | [seo_backlinks.md](seo_backlinks.md) |
| Anchors | 40 / line | — | per line | [seo_backlinks_anchors.md](seo_backlinks_anchors.md) |
| Indexed Pages | 40 / line | — | per line | [seo_backlinks_pages.md](seo_backlinks_pages.md) |
| Referring Domains | 40 / line | — | per line | [seo_backlinks_refdomains.md](seo_backlinks_refdomains.md) |
| Referring IPs | 40 / line | — | per line | [seo_backlinks_refips.md](seo_backlinks_refips.md) |
| TLD Distribution | 40 / line | — | per line | [seo_backlinks_tld.md](seo_backlinks_tld.md) |
| Referring Domains by Country | 40 / line | — | per line | [seo_backlinks_geo.md](seo_backlinks_geo.md) |
| Categories | **50 / request** | — | per request | [seo_backlinks_categories.md](seo_backlinks_categories.md) |
| Categories Profile | 40 / line | — | per line | [seo_backlinks_categories_profile.md](seo_backlinks_categories_profile.md) |
| Authority Score Profile | **100 / request** | — | per request | [seo_backlinks_ascore_profile.md](seo_backlinks_ascore_profile.md) |
| Competitors (Backlinks) | 40 / line | — | per line | [seo_backlinks_competitors.md](seo_backlinks_competitors.md) |
| Batch Comparison | 40 / line | — | per line | [seo_backlinks_comparison.md](seo_backlinks_comparison.md) |
| Comparison by Referring Domains | 40 / line | — | per line | [seo_backlinks_matrix.md](seo_backlinks_matrix.md) |
| Historical Data (Backlinks) | 40 / line | — | per line | [seo_backlinks_historical.md](seo_backlinks_historical.md) |

---

## Trends API

CSV `,`-delimited responses. Base URL: `https://api.semrush.com/analytics/ta/api/v3/`. Auth: `?key=<KEY>`. 10 RPS per account. Most endpoints are per-request; **Traffic Summary** is per-line.

> **Empty-response policy varies.** Most Trends endpoints **do** charge when the response is empty. The four traffic time-series endpoints (Summary, Daily, Weekly) **do not** charge for empty responses. The "Empty charged?" column below captures this.

| Endpoint | Cost | Billing | Empty charged? | File |
|---|---|---|---|---|
| Traffic Summary | 1 / line | per line | **No** — only charged for domains that return data | [trends_traffic_summary.md](trends_traffic_summary.md) |
| Daily Traffic | 1 / request | per request | **No** | [trends_daily_traffic.md](trends_daily_traffic.md) |
| Weekly Traffic | 1 / request | per request | **No** | [trends_weekly_traffic.md](trends_weekly_traffic.md) |
| Traffic Rank | 1 / request | per request | Yes | [trends_traffic_rank.md](trends_traffic_rank.md) |
| Traffic Sources | 1 / request | per request | Yes | [trends_traffic_sources.md](trends_traffic_sources.md) |
| Traffic Destinations | 1 / request | per request | Yes | [trends_traffic_destinations.md](trends_traffic_destinations.md) |
| Top Pages | 1 / request | per request | Yes | [trends_top_pages.md](trends_top_pages.md) |
| Subdomains | 1 / request | per request | Yes | [trends_subdomains.md](trends_subdomains.md) |
| Subfolders | 1 / request | per request | Yes | [trends_subfolders.md](trends_subfolders.md) |
| Geo Distribution | 1 / request | per request | Yes | [trends_geo_distribution.md](trends_geo_distribution.md) |
| Purchase Conversion | 1 / request | per request | Yes | [trends_purchase_conversion.md](trends_purchase_conversion.md) |
| Data Accuracy | 1 / request | per request | Yes | [trends_data_accuracy.md](trends_data_accuracy.md) |
| Industry Categories | **500 / request** | per request | Yes | [trends_industry_categories.md](trends_industry_categories.md) |
| Audience Insights | 1 / request | per request | Yes | [trends_audience_insights.md](trends_audience_insights.md) |
| Audience Interests | 1 / request | per request | Yes | [trends_audience_interests.md](trends_audience_interests.md) |
| Age and Sex Distribution | 1 / request | per request | Yes | [trends_age_sex_distribution.md](trends_age_sex_distribution.md) |
| Household Distribution | 1 / request | per request | Yes | [trends_household_distribution.md](trends_household_distribution.md) |
| Income Distribution | 1 / request | per request | Yes | [trends_income_distribution.md](trends_income_distribution.md) |
| Education Distribution | 1 / request | per request | Yes | [trends_education_distribution.md](trends_education_distribution.md) |
| Occupation Distribution | 1 / request | per request | Yes | [trends_occupation_distribution.md](trends_occupation_distribution.md) |
| Social Media | 1 / request | per request | Yes | [trends_social_media.md](trends_social_media.md) |

---

## Projects API

JSON responses. Two parallel auth surfaces (API key vs. OAuth 2.0) — same operations, same per-request pricing. Requires the **SEO Business** subscription plus available API units.

### Projects API (API key)

| Endpoint | Cost | Billing | File |
|---|---|---|---|
| List Projects | 100 / request | per request | [projects_list.md](projects_list.md) |
| Get Project | 100 / request | per request | [projects_get.md](projects_get.md) |
| Create Project | 100 / request | per request | [projects_create.md](projects_create.md) |
| Update Project | 100 / request | per request | [projects_update.md](projects_update.md) |
| Delete Project | 100 / request | per request | [projects_delete.md](projects_delete.md) |

### Projects API (OAuth 2.0)

> Same 100/request pricing as the API-key flow. The per-endpoint pages don't restate the price — it inherits from the Projects API overview.

| Endpoint | Cost | Billing | File |
|---|---|---|---|
| ProjectsList | 100 / request | per request | [projects_oauth_list.md](projects_oauth_list.md) |
| GetProject | 100 / request | per request | [projects_oauth_get.md](projects_oauth_get.md) |
| CreateProject | 100 / request | per request | [projects_oauth_create.md](projects_oauth_create.md) |
| UpdateProject | 100 / request | per request | [projects_oauth_update.md](projects_oauth_update.md) |
| RemoveProject | 100 / request | per request | [projects_oauth_delete.md](projects_oauth_delete.md) |

---

## Position Tracking API

JSON responses. Most endpoints are 100 per request, but four reports scale per keyword/competitor/landing-page returned — these can get expensive fast on large campaigns.

### Campaign management

| Endpoint | Cost | Billing | File |
|---|---|---|---|
| Create Campaign | 100 / request | per request | [projects_tracking_create.md](projects_tracking_create.md) |
| List Campaigns | 100 / request | per request | [projects_tracking_campaigns_list.md](projects_tracking_campaigns_list.md) |
| Campaign Dates | 100 / request | per request | [projects_tracking_campaign_dates.md](projects_tracking_campaign_dates.md) |
| Universal Location Search | 100 / request | per request | [projects_tracking_locations.md](projects_tracking_locations.md) |
| Enable Email Notifications | 100 / request | per request | [projects_tracking_notifications_enable.md](projects_tracking_notifications_enable.md) |
| Disable Email Notifications | 100 / request | per request | [projects_tracking_notifications_disable.md](projects_tracking_notifications_disable.md) |

### Keywords & tags

| Endpoint | Cost | Billing | File |
|---|---|---|---|
| Add Keywords | **100 / keyword added** | per keyword | [projects_tracking_keywords_add.md](projects_tracking_keywords_add.md) |
| Remove Keywords | 100 / request | per request | [projects_tracking_keywords_remove.md](projects_tracking_keywords_remove.md) |
| Add Tags | 100 / request | per request | [projects_tracking_tags_add.md](projects_tracking_tags_add.md) |
| Remove Tags | 100 / request | per request | [projects_tracking_tags_remove.md](projects_tracking_tags_remove.md) |

### Competitors

| Endpoint | Cost | Billing | File |
|---|---|---|---|
| Add Competitors | 100 / request | per request | [projects_tracking_competitors_add.md](projects_tracking_competitors_add.md) |
| Remove Competitors | 100 / request | per request | [projects_tracking_competitors_remove.md](projects_tracking_competitors_remove.md) |
| Organic Competitors Discovery | **1000 / competitor** | per competitor | [projects_tracking_competitors_organic.md](projects_tracking_competitors_organic.md) |
| Adwords Competitors Discovery | **1000 / competitor** | per competitor | [projects_tracking_competitors_adwords.md](projects_tracking_competitors_adwords.md) |

### Reports

| Endpoint | Cost | Billing | File |
|---|---|---|---|
| Organic Overview | 100 / request | per request | [projects_tracking_overview_organic.md](projects_tracking_overview_organic.md) |
| Adwords Overview | 100 / request | per request | [projects_tracking_overview_adwords.md](projects_tracking_overview_adwords.md) |
| Organic Positions | **100 / keyword added** | per keyword | [projects_tracking_position_organic.md](projects_tracking_position_organic.md) |
| Adwords Positions | **100 / keyword added** | per keyword | [projects_tracking_position_adwords.md](projects_tracking_position_adwords.md) |
| Organic Visibility Index | 100 / request | per request | [projects_tracking_visibility_organic.md](projects_tracking_visibility_organic.md) |
| Adwords Visibility Index | 100 / request | per request | [projects_tracking_visibility_adwords.md](projects_tracking_visibility_adwords.md) |
| Organic Landing Pages | **1000 / landing page** | per landing page | [projects_tracking_landing_pages_organic.md](projects_tracking_landing_pages_organic.md) |
| Adwords Landing Pages | **1000 / landing page** | per landing page | [projects_tracking_landing_pages_adwords.md](projects_tracking_landing_pages_adwords.md) |

---

## Site Audit API

JSON responses. Most endpoints are 100 per request, but three reports cost **1,000** or **10,000** units per request — and the History endpoint multiplies by snapshot count.

| Endpoint | Cost | Billing | File |
|---|---|---|---|
| Enable Site Audit Tool | 100 / request | per request | [projects_siteaudit_enable.md](projects_siteaudit_enable.md) |
| Edit Campaign | 100 / request | per request | [projects_siteaudit_edit.md](projects_siteaudit_edit.md) |
| Run Audit | 100 / request | per request | [projects_siteaudit_launch.md](projects_siteaudit_launch.md) |
| Get Campaign Info | 100 / request | per request | [projects_siteaudit_info.md](projects_siteaudit_info.md) |
| List Snapshots | 100 / request | per request | [projects_siteaudit_snapshots.md](projects_siteaudit_snapshots.md) |
| Get Snapshot | **10,000 / request** | per request | [projects_siteaudit_snapshot.md](projects_siteaudit_snapshot.md) |
| Get Snapshots History | **10,000 / request × snapshots returned** | per snapshot | [projects_siteaudit_history.md](projects_siteaudit_history.md) |
| Issue Detail | 100 / request | per request | [projects_siteaudit_issue_detail.md](projects_siteaudit_issue_detail.md) |
| Issues Meta (descriptions) | 100 / request | per request | [projects_siteaudit_issues_meta.md](projects_siteaudit_issues_meta.md) |
| Get Page | **1,000 / request** | per request | [projects_siteaudit_page.md](projects_siteaudit_page.md) |
| Get Page ID by URL | 100 / request | per request | [projects_siteaudit_page_list.md](projects_siteaudit_page_list.md) |

> **History cost example:** querying 5 snapshots in one call costs `5 × 10,000 = 50,000 units`. Filter the date range narrowly.

---

## Listing Management API

JSON responses. **No API units are consumed.** Access requires Semrush **Local Pro** or **Business** subscription.

| Endpoint | Cost | Notes | File |
|---|---|---|---|
| Get Categories | Free of API units | — | [local_listing_categories.md](local_listing_categories.md) |
| Get Locations | Free of API units | — | [local_listing_list.md](local_listing_list.md) |
| Get Location | Free of API units | — | [local_listing_get.md](local_listing_get.md) |
| Create Location | Free of API units | **Consumes one Local Pro location limit.** Released if `location_status` becomes `FAILED`. `dryRun=true` bypasses the limit. | [local_listing_create.md](local_listing_create.md) |
| Update Location | Free of API units | — | [local_listing_update.md](local_listing_update.md) |

---

## Map Rank Tracker API

JSON responses. OAuth 2.0 required. **No API units are consumed.** Only `CollectCampaign` spends a separate billing token: **Map Rank Tracker credits**.

> **Credit model.** Credits reset to the plan maximum on the **1st of each month** and **do not roll over**. Check available credits with [GetUserLimits](local_map_rank_limits.md) before triggering a collection.

| Endpoint | Cost | Notes | File |
|---|---|---|---|
| GetCampaigns | Free of API units & credits | — | [local_map_rank_campaigns_list.md](local_map_rank_campaigns_list.md) |
| GetCampaign | Free of API units & credits | — | [local_map_rank_campaign_get.md](local_map_rank_campaign_get.md) |
| CreateCampaign | Free of API units & credits | Creating a campaign does not spend credits — only collecting data does. | [local_map_rank_campaign_create.md](local_map_rank_campaign_create.md) |
| UpdateCampaign | Free of API units & credits | — | [local_map_rank_campaign_update.md](local_map_rank_campaign_update.md) |
| DeleteCampaign | Free of API units & credits | — | [local_map_rank_campaign_delete.md](local_map_rank_campaign_delete.md) |
| **CollectCampaign** | **`grid_points × keywords` credits** | Triggers data collection. **No API units charged.** | [local_map_rank_collect.md](local_map_rank_collect.md) |
| GetKeywordStatuses | Free of API units & credits | — | [local_map_rank_keyword_statuses.md](local_map_rank_keyword_statuses.md) |
| GetHeatmap | Free of API units & credits | — | [local_map_rank_heatmap.md](local_map_rank_heatmap.md) |
| GetMetrics | Free of API units & credits | — | [local_map_rank_metrics.md](local_map_rank_metrics.md) |
| GetTopCompetitors | Free of API units & credits | — | [local_map_rank_top_competitors.md](local_map_rank_top_competitors.md) |
| GetUserLimits | Free of API units & credits | Check this **before** calling `CollectCampaign`. | [local_map_rank_limits.md](local_map_rank_limits.md) |

**Credit cost example:** a campaign with a 9×9 grid (81 points) tracking 20 keywords costs `81 × 20 = 1,620 credits` per collection.

---

## Most expensive endpoints, at a glance

When you need to be cost-conscious, watch for these:

| # | Endpoint | Worst-case cost | Why |
|---|---|---|---|
| 1 | [Site Audit Snapshots History](projects_siteaudit_history.md) | 10,000 × N snapshots | Multiplies per snapshot returned. |
| 2 | [Site Audit Snapshot](projects_siteaudit_snapshot.md) | 10,000 / request | Fixed but high. |
| 3 | [Position Tracking Landing Pages (Organic/Adwords)](projects_tracking_landing_pages_organic.md) | 1,000 × N landing pages | Per-landing-page multiplier. |
| 4 | [Position Tracking Competitors Discovery (Organic/Adwords)](projects_tracking_competitors_organic.md) | 1,000 × N competitors | Per-competitor multiplier. |
| 5 | [Site Audit Page](projects_siteaudit_page.md) | 1,000 / request | Single page detail. |
| 6 | [Trends Industry Categories](trends_industry_categories.md) | 500 / request | Charged even when empty. |
| 7 | [SEO Domain vs. Domain](seo_domain_vs_domain.md) | 80 / line live, **400 / line historical** | Highest per-line SEO rate. |
| 8 | [SEO Keyword Difficulty](seo_keyword_difficulty.md) | 50 / line | Per-line, no historical discount. |
| 9 | [SEO Domain Ad History](seo_domain_ad_history.md) / [Keyword Ads History](seo_keyword_ads_history.md) | 100 / line | History-only reports — single high tier. |
| 10 | [SEO PLA Copies / PLA Competitors](seo_domain_pla_copies.md) | 60 / line live, **300 / line historical** | Most expensive PLA reports. |

---

## Cost optimization tips

1. **Cap rows with `display_limit`.** Per-line endpoints charge for what you receive — `&display_limit=10` returns at most 10 rows. See [api_unit_balance.md](api_unit_balance.md#optimize-unit-consumption).
2. **Trim columns with `export_columns`.** It doesn't reduce cost (cost is per line, not per cell), but it shrinks payloads — useful when you're iterating.
3. **Check the balance first.** Per-line SEO/Trends/Projects-API-key endpoints will return a **partial result** when balance runs out, so the response may silently truncate. Always pre-check with the [free balance endpoints](#free--utility-endpoints).
4. **Prefer single-database endpoints when you don't need all databases.** `seo_domain_overview` returns one row; `seo_domain_overview_all` returns one row per database (~170 lines worldwide).
5. **Avoid historical data when live works.** Historical pricing is **5×** on most SEO per-line endpoints — confirm you actually need a back-dated value before passing `display_date`.
6. **Batch keywords with `seo_keyword_overview_batch`.** One request handles up to 100 keywords at 10/line vs. 100 separate calls.
7. **Site Audit: query the right granularity.** `siteaudit_info` (100) and `siteaudit_snapshots` (100) are cheap; `siteaudit_snapshot` (10,000) and `siteaudit_history` (10,000 × N) are expensive — only call them when you need the full snapshot tree.
8. **Position Tracking: count your keywords before adding.** Each keyword added or queried in `position_organic` / `position_adwords` is 100 units. A 500-keyword campaign report costs 50,000 units.
9. **Map Rank Tracker: count your grid.** A 13×13 grid (169 points) with 10 keywords costs `1,690` credits per collection. Larger grids burn the monthly allowance fast.

---

## Cost estimation worked example

Adapted from [api_unit_balance.md](api_unit_balance.md#cost-calculation-example):

**Goal.** Pull Domain Organic Search Keywords for **50 domains**, **500 keywords each**.

| Data type | Per-keyword cost | Keywords | Domains | Total |
|---|---|---|---|---|
| Live (current month) | 10 | 500 | 50 | **250,000** |
| Historical (12 months ago) | 50 | 500 | 50 | **1,250,000** |
| **Grand total** | | | | **1,500,000 units** |

The historical-data surcharge is dominating the cost (~83% of the total). If you only need live data, skip `display_date` and save 1.25M units.

---

## Error responses when out of units

| API | Error |
|---|---|
| SEO API, Trends API, Projects API (API key) | `ERROR 132` |
| Local API, Projects API (OAuth 2.0) | HTTP `403` |

See [api_unit_balance.md](api_unit_balance.md#what-happens-when-you-run-out) for the partial-response semantics.

---

## Related references

- [api_unit_balance.md](api_unit_balance.md) — How to check balance, partial-response policy, query log fields, log export.
- [seo_api_overview.md](seo_api_overview.md) — Full SEO API contract: export columns, filter/sort syntax, error codes, historical-data conventions.
- [trends_api_overview.md](trends_api_overview.md) — Basic vs. Premium plans, data-availability windows, rate limits.
- [projects_api_overview.md](projects_api_overview.md) — API-key vs. OAuth flow, error code map.
- [local_api_overview.md](local_api_overview.md) — Listing Management vs. Map Rank Tracker request/response envelope.
- [faq.md](faq.md) — Unit consumption FAQ.

---

*Pricing is captured from the per-endpoint pages in this repository as of 2026-05. If an endpoint's documentation page shows a different rate, treat the per-endpoint page as authoritative and this file as out-of-date.*
