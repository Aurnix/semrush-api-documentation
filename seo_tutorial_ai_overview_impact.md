# SEO API Tutorial — Analyze AI Overview Impact on Your Traffic

AI-powered search features like Google's AI Overview are reducing clicks on traditional organic listings. This tutorial shows two ways to measure that impact using the SEO API: how often AI Overviews appear for your ranking keywords, and how often your domain is included in them.

The AI Overview SERP Feature has code `52`.

---

## Prerequisites

- Access to Standard API
- Sufficient API units
- Your API key (from Subscription info → API Units)

---

## Option 1: Use the Domain Overview Report

Use [Domain Overview (all databases)](seo_domain_overview_all.md) and include the `FK52` and `FP52` columns (SERP feature `52` = AI Overview).

| Column | Meaning |
|---|---|
| `FK52` | Total times AI Overview is triggered by keywords your domain ranks for |
| `FP52` | Total times your domain *actually appears in* the AI Overview |

### Request

```
https://api.semrush.com/?key=YOUR_API_KEY&type=domain_ranks&domain=your-domain.com&database=us&export_columns=Db,Dn,Rk,Ot,FK52,FP52
```

### Interpret the Result

Compare `FP52` against `FK52`:

- **High `FP52`/`FK52` ratio** → strong presence in AI Overview.
- **Low ratio** → potential visibility loss. Your content ranks traditionally but isn't surfaced in AI answers.

---

## Option 2: Use the Domain Organic Search Keywords Report

Use [Domain Organic Search Keywords](seo_domain_organic.md) to retrieve the specific keywords involved.

Include the `Fk` and `Fp` SERP Feature columns:

- `Fk` — all SERP features triggered by a keyword
- `Fp` — SERP features your domain appears in for that keyword

Apply a `display_filter` for SERP feature `52`:

- `display_filter=+|Fk|Eq|52` — keywords that trigger AI Overview (regardless of your visibility)
- `display_filter=+|Fp|Eq|52` — keywords where your domain appears inside AI Overview

URL-encoded: `display_filter=%2B%7CFk%7CEq%7C52` (or `%2B%7CFp%7CEq%7C52`).

Also set `display_positions_type=all` so both organic and SERP Feature positions are returned.

### Retrieve keywords that trigger AI Overview (filter by `Fk`)

```
https://api.semrush.com/?type=domain_organic&key=API_KEY&display_limit=50&export_columns=Ph,Po,Pp,Pd,Nq,Cp,Ur,Tr,Tc,Co,Nr,Td,Fk,Fp&domain=justanswer.com&database=us&display_filter=%2B%7CFk%7CEq%7C52&display_positions_type=all
```

### Retrieve keywords where your domain appears in AI Overview (filter by `Fp`)

```
https://api.semrush.com/?type=domain_organic&key=API_KEY&display_limit=50&export_columns=Ph,Po,Pp,Pd,Nq,Cp,Ur,Tr,Tc,Co,Nr,Td,Fk,Fp&domain=justanswer.com&database=us&display_filter=%2B%7CFp%7CEq%7C52&display_positions_type=all
```

### Interpret the Results

- The first request lists the exact keywords that trigger AI Overview for your domain's ranking footprint.
- The second narrows that list to where your domain actually appears in AI Overview.
- Compare the two — the gap (`Fk` set minus `Fp` set) is the missed-opportunity list: AI Overview is active, your domain isn't included.

---

## Take Action

Focus on content improvements that make your pages AI-friendly. Semrush's [SEO Writing Assistant](https://www.semrush.com/swa/) can help recover lost organic traffic from zero-click searches.
