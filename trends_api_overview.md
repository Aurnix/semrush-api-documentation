# Trends API Overview

The Trends API delivers strategic website traffic and market data powered by real user behavior (clickstream). Unlike the Standard API (tactical SEO/PPC data), the Trends API focuses on market-level insights: benchmarking competitors, evaluating partners, qualifying leads, and identifying investment opportunities.

---

## Key Use Cases

- **Market evaluation**: Assess new markets, competitive landscape, and emerging trends
- **Competitor analysis**: Identify competitor strategies, best practices, and weaknesses
- **Audience understanding**: Access demographics to inform strategy
- **Geographic analysis**: Discover regional trends using site traffic data
- **Lead qualification**: Analyze key metrics tailored to target needs

---

## Integration Targets

- Dashboards: Enterprise portals, CRMs, ERP systems
- Reporting software: Tableau, Power BI
- Spreadsheets: Google Sheets, Microsoft Excel
- Custom in-house analytics systems

---

## Subscription Plans

### Trends Basic API

Broad traffic summaries with website traffic metrics and user behavior data:

- Monthly Visits
- Unique Visits
- Pages Per Visit
- Average Visit Duration
- Mobile vs. Desktop split
- Bounce Rates

### Trends Premium API

Everything in Basic, plus 16 additional data types:

- Daily Traffic
- Weekly Traffic
- Purchase Conversion
- Industry Categories
- Traffic Sources
- Traffic Destinations
- Subdomain Traffic
- Subfolder Traffic
- Geographic Distribution
- Top Pages
- Traffic Rank
- Audience Insights
- Age and Sex Distribution
- Household Size, Income, Education, and Occupation distributions
- Audience Interests
- Social Media Preferences

> Trends Premium API requires contacting the Sales team for a personalized quote.

---

## Getting Started

### Prerequisites

1. Get your API key from **Subscription info → API Units**
2. Check your Trends API unit balance before making requests

### Request Structure

```
https://api.semrush.com/analytics/ta/api/v3/summary?key=YOUR_API_KEY&targets=openai.com&export_columns=target,visits,users&display_date=2024-06-01&country=US
```

**URL breakdown:**

| Part | Description |
|------|-------------|
| `https://api.semrush.com/analytics/ta/api/v3/` | Base endpoint |
| `summary` | Report type |
| `key=YOUR_API_KEY` | Your API key |
| `targets=openai.com` | Domain, subdomain, or folder to analyze |
| `export_columns=target,visits,users` | Specific data columns to return |
| `display_date=2024-06-01` | Date range for data |
| `country=US` | Country filter |

Parameters follow `?` and are separated by `&`.

---

## Response Format

All Trends API endpoints return responses in **CSV format**.

---

## Data Availability

| Data Type | Available From |
|-----------|---------------|
| Traffic data | 2017 |
| Age and Sex audience data | April 2020 |
| Socioeconomic data | April 2022 |

New data is not pushed via notification. Check the Traffic & Market interface to see what's available — API data matches what's shown there.

**Data refresh schedule:**
- Weekly data: Available each week for the prior week
- Monthly data: Full prior month available by the 10th of the current month

---

## Rate Limits

- **10 requests per second (RPS)** per account
- No hourly or daily limits (legacy hourly/daily fields still appear in responses for backward compatibility but are no longer enforced)
- Monthly quota can be increased by purchasing additional API units

---

## Billing

- No free trial available
- Can be purchased without a Semrush subscription via the Traffic & Market page
- Units renew monthly; additional units can be purchased anytime via Subscription info

**Empty response billing exceptions:**

| Method | Charged if empty? |
|--------|------------------|
| Traffic Summary | No |
| Daily Traffic | No |
| Weekly Traffic | No |
| All other Trends API methods | Yes |

---

## FAQ

**Do I need technical expertise?**
No. Building a request requires only constructing a URL with parameters as described above.

**Where are error codes documented?**
In the SEO API error codes and messages section (shared reference).

**How often can I pull data?**
Anytime, as long as you have units. No rate restriction beyond 10 RPS.

**What is the data methodology?**
Raw clickstream data processed through Semrush's proprietary ML algorithm to generate traffic estimates.

**Can I access data from before an algorithm update?**
Semrush stores pre-update data for 3 months after a significant algorithm change. Contact customer support to request it.

**Old Traffic Analytics API:**
If using the legacy Traffic Analytics API, refer to the [Traffic Analytics API PDF documentation](https://static.semrush.com/blog/uploads/files/34/ae/34ae0601e3aeaec30bbda1fd3bad7885/traffic_analytics-api.pdf).
