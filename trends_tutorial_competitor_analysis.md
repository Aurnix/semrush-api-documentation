# Trends API Tutorial — Evaluate Performance Against Top 5 Competitors

This tutorial walks through using the Trends API to analyze your top 5 competitors' online performance — traffic, behavior, sources, geography, and audience demographics — and compare against your own domain.

**Total API unit cost for this tutorial: 30 units**

---

## Prerequisites

- Access to the Trends API
- Sufficient Trends API units (30 for all steps below)
- Your API key (from Subscription info → API Units)

---

## Step 1: Compare Traffic Performance

### Step 1.1 — Get Traffic Overview

**Method:** [Traffic Summary](trends_traffic_summary.md)  
**Cost:** 1 unit per line — 6 domains = 6 API units

```
https://api.semrush.com/analytics/ta/api/v3/summary?targets=YOUR_DOMAIN,ebay.com,walmart.com,etsy.com,homedepot.com,target.com&export_columns=target,visits,users,time_on_site,pages_per_visit,bounce_rate&key=YOUR_API_KEY
```

**Parameters to customize:**
- `targets` — your domain plus up to 5 competitors (comma-separated, max 200)
- `display_date` — specific month in `YYYY-MM-01` format; defaults to previous month
- `country` — e.g. `country=us` for US-only data
- `export_columns` — limit to the metrics you need

**Result:** Side-by-side comparison of traffic rank, visits, unique visitors, pages per visit, average visit duration, and bounce rate.

**AI traffic tip:** Add `ai_search` and `ai_assistants` to `export_columns` to track how much traffic each competitor receives from AI-powered search engines (Gemini) and AI assistants (ChatGPT, Copilot).

---

### Step 1.2 (Optional) — Get Daily Traffic Insights

Use this if you want to uncover daily patterns, seasonality, or campaign spikes beyond the monthly snapshot.

**Method:** [Daily Traffic](trends_daily_traffic.md)  
**Cost:** 1 unit per request — 6 domains = 6 API units

```
https://api.semrush.com/analytics/ta/api/v3/summary_by_day?target=ebay.com&key=YOUR_API_KEY
```

Repeat for each competitor domain and your own. **Result:** Day-by-day traffic breakdown per domain.

---

## Step 2: Analyze Traffic Sources, Regions, and Audience

For each method in this step: replace `target=ebay.com` with each competitor's domain and your own, repeat 6 times.

**Cost per method:** 1 unit per request × 6 domains = 6 units  
**Total for all 3 methods in Step 2:** 18 API units

---

### Step 2.1 — Understand Traffic Channels

**Goal:** Identify where competitors get their traffic (direct, referral, search, social) to understand their primary growth strategies.

**Method:** [Traffic Sources](trends_traffic_sources.md)

```
https://api.semrush.com/analytics/ta/api/v3/sources?target=ebay.com&key=YOUR_API_KEY
```

**Result:** Channel-by-channel breakdown to spot organic vs. paid leaders and benchmark acquisition strategies.

---

### Step 2.2 — Spot Regional Players

**Goal:** Discover where competitor audiences are geographically located.

**Method:** [Geo Distribution](trends_geo_distribution.md)

```
https://api.semrush.com/analytics/ta/api/v3/geo?target=ebay.com&key=YOUR_API_KEY
```

**Result:** Country-level traffic breakdown for each domain.

---

### Step 2.3 — Analyze Market Demographics

**Goal:** Understand competitor visitor demographics for improved segmentation and targeting.

**Method:** [Age and Sex Distribution](trends_age_sex_distribution.md)

```
https://api.semrush.com/analytics/ta/api/v3/age_and_sex_distribution?target=ebay.com&key=YOUR_API_KEY
```

**Result:** Demographic breakdown by age and gender — useful for identifying audience overlap and refining ad targeting.

---

## Step 3: Turn Data Into Strategy

With data from Steps 1 and 2:

- **Compare side-by-side** — your metrics vs. each competitor's
- **Identify channel gaps** — where you're over- or under-investing vs. competitors
- **Audience composition** — where your audience diverges from competitors'

Apply findings to: content strategy, paid ad targeting, and regional expansion priorities.

---

## API Unit Summary

| Step | Method | Units |
|------|--------|-------|
| 1.1 | Traffic Summary (6 domains) | 6 |
| 1.2 (optional) | Daily Traffic (6 domains) | 6 |
| 2.1 | Traffic Sources (6 domains) | 6 |
| 2.2 | Geo Distribution (6 domains) | 6 |
| 2.3 | Age and Sex Distribution (6 domains) | 6 |
| **Total** | | **30** |
