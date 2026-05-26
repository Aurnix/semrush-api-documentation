# SEO API Tutorial — Analyze Keyword Gaps Among Competitors

This tutorial uses the [Domain vs. Domain](seo_domain_vs_domain.md) report to compare your domain against two competitors and surface **untapped keywords** — keywords they rank for that you don't. It's a content-gap workflow for finding new SEO opportunities.

**Total API unit cost for this tutorial: 800 units** (80 units per line × 10 top keywords)

---

## Prerequisites

- Access to Standard API
- Sufficient API units (800 for this tutorial)
- Your API key (from Subscription info → API Units)

A testing tool like Postman is helpful — but note that test requests still consume API units.

---

## Step 1: Specify Keyword Type and Domains

Scenario: analyzing `mybrand.com` against two competitors, `competitor1.com` and `competitor2.com`.

Untapped-keyword formula:

```
*|or|competitor1.com|+|or|competitor2.com|-|or|mybrand.com
```

Breakdown:

| Segment | Meaning |
|---|---|
| `*` | Wildcard — start with all keywords |
| `\|or\|competitor1.com` | Add organic keyword pool for competitor 1 |
| `\|+\|or\|competitor2.com` | Add organic keyword pool for competitor 2 |
| `\|-\|or\|mybrand.com` | Exclude keywords you already rank for |

This string must be URL-encoded and passed as the `domains` parameter.

### URL-encoded form

```
domains=%2A%7Cor%7Ccompetitor1.com%7C%2B%7Cor%7Ccompetitor2.com%7C%2D%7Cor%7Cmybrand.com
```

| Character | Encoded |
|---|---|
| `*` | `%2A` |
| `\|` | `%7C` |
| `+` | `%2B` |
| `-` | `%2D` |

---

## Step 2: Filter Results

Use `display_filter` to focus the report. Recommended filters for high-value, lower-competition keywords:

| Filter | Meaning |
|---|---|
| Search Volume > 1,000 | Keywords with real traffic potential |
| Keyword Difficulty < 60 | Moderately or less competitive in organic search |
| Competition < 0.6 | Lower paid competition (often easier organic targets) |

Filter string:

```
+|Nq|Gt|1000|+|Kd|Lt|60|+|Co|Lt|0.6
```

Breakdown — each clause is `<sign>|<field>|<operation>|<value>`:

- `+|Nq|Gt|1000` — include rows where Search Volume > 1000
- `+|Kd|Lt|60` — include rows where Keyword Difficulty < 60
- `+|Co|Lt|0.6` — include rows where Competition < 0.6

### URL-encoded form

```
display_filter=%2B%7CNq%7CGt%7C1000%7C%2B%7CKd%7CLt%7C60%7C%2B%7CCo%7CLt%7C0.6
```

---

## Step 3: Sort Results

Sort by descending search volume:

```
display_sort=nq_desc
```

See [Sortings](seo_api_overview.md#sortings) for other options.

---

## Step 4: Add Other Request Parameters

| Parameter | Value | Purpose |
|---|---|---|
| `type` | `domain_domains` | Report type |
| `key` | `YOUR_API_KEY` | Your API key |
| `database` | `us` | US database |
| `export_columns` | `Ph,P0,P1,P2,Nq,Kd,Co,Cp` | Columns to extract (optional) |
| `display_limit` | `10` | Top 10 results (optional) |

---

## Final Request

```
https://api.semrush.com/?type=domain_domains&key=YOUR_API_KEY&database=us&domains=%2A%7Cor%7Ccompetitor1.com%7C%2B%7Cor%7Ccompetitor2.com%7C%2D%7Cor%7Cmybrand.com&display_sort=nq_desc&display_filter=%2B%7CNq%7CGt%7C1000%7C%2B%7CKd%7CLt%7C60%7C%2B%7CCo%7CLt%7C0.6&export_columns=Ph,P0,P1,P2,Nq,Kd,Co,Cp&display_limit=10
```

---

## What's Next

The result is a list of high-value, lower-competition keywords your competitors rank for but you don't. From here you can:

- Refine the filter thresholds for your specific SEO goals
- Integrate the report into a content-planning workflow
- Automate the report on a recurring schedule

For broader strategy, explore the other Semrush API reports.
