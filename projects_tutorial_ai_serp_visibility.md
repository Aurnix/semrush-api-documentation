# Projects API Tutorial — Monitor and Optimize Visibility in AI SERP Features

AI-powered SERP features — like Google's AI Overview and Bing's Ask AI or AI Chat — are reshaping the SERP and redefining organic visibility. This tutorial shows how to track your domain's presence in AI-generated answers and monitor your competitors' visibility using the Position Tracking API.

---

## Prerequisites

- Access to Standard API
- A Position Tracking campaign (campaign ID required)
- Sufficient API units
- Your API key (from Subscription info → API Units)

The report reflects results for either Google or Bing, based on the search engine configured for your Position Tracking campaign.

---

## Track Your Presence in AI SERP Features

Use the [Organic positions report](projects_tracking_position_organic.md) on your Position Tracking campaign to check which target keywords are eligible for AI SERP features and feature your domain. This lets you:

- Quantify brand exposure within AI-generated answers.
- Prioritize content optimization for AI-eligible keywords.

---

## Check All Campaign Keywords Included in Google AI Overview

To filter all campaign keywords included in the Google AI Overview results, request the [Organic positions report](projects_tracking_position_organic.md) with `serp_feature_filter=aio`:

```
https://api.semrush.com/reports/v1/projects/{campaignID}/tracking/?type=tracking_position_organic&key=YOUR_API_KEY&action=report&url=*.your-domain.com%2F*&serp_feature_filter=aio
```

---

## Track Your and Your Competitors' Keywords That Rank in Google AI Overview

To analyze how you rank in AI Overview compared to competitors, include multiple domains in the `url` parameter and scope `serp_feature_filter` to a specific domain index:

- `aio,0` — your domain's keywords that rank in AI Overview.
- `aio,1` — your competitor's keywords that rank in AI Overview.

```
https://api.semrush.com/reports/v1/projects/{campaignID}/tracking/?type=tracking_position_organic&key=YOUR_API_KEY&action=report&url=*.your-domain.com%2F*:*.your-competitor-domain.com%2F*&serp_feature_filter=aio,0
```

See the [SERP features reference](projects_tracking_overview.md#serp-features) for the full `serp_feature_filter` syntax.

---

## Check Keywords for Bing AI SERP Features

The same request structure works for Bing-targeted campaigns. Set `serp_feature_filter` to the feature code you want:

| Code | Bing Feature |
|---|---|
| `aai` | Ask AI |
| `aic` | AI chat |
| `aim` | AI summary |
| `ais` | AI stories |

---

## Take Action

- Adjust your content and keyword strategy using Semrush tools such as [Keyword Magic Tool](https://www.semrush.com/analytics/keywordmagic/).
- Regularly review the report to spot new keywords impacted by AI answers.

---

## See Also

- [Organic positions report](projects_tracking_position_organic.md)
- [Position Tracking Overview](projects_tracking_overview.md) — full SERP feature codes
- [SEO API tutorial: Analyze AI Overview Impact](seo_tutorial_ai_overview_impact.md) — complementary domain-level analysis
