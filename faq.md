# FAQ

---

## Where do I find my API key?

Your API key is assigned after subscribing to Semrush. Find it at: **Subscription info → API Units**.

### Can I update my API key?

No — you cannot change it yourself. If you suspect your key is compromised, contact Semrush Tech Support and they will update it for you.

---

## What can I use the Semrush API for?

Common use cases include optimizing SEO/PPC ROI, market strategy analysis, and competitive research. See the Semrush API use cases documentation to identify the right API type and methods for your needs.

---

## Standard API vs. Trends API

| | Standard API (SEO + Projects) | Trends API |
|---|---|---|
| **Focus** | Tactical SEO and PPC data | Strategic, market-level insights |
| **Data type** | Rankings, backlinks, keywords, site audits | Real user behavior (clickstream) |
| **Best for** | In-depth site optimization | Market analysis and benchmarking |
| **Includes** | Traffic trends, competitor movement, audience overlap | ✓ |

These APIs require separate subscriptions and API unit packages.

---

## Can the API measure AI traffic?

Yes, in two ways:

- **Trends API** (Traffic Summary, Industry Categories): Includes traffic from AI-powered search engines and assistants (ChatGPT, Gemini, Copilot). Useful for benchmarking AI-driven traffic against competitors.
- **Standard API** (SEO + Projects APIs): Track AI visibility features like Google's AI Overview and Bing's Ask AI / AI Chat.

---

## How is unit consumption calculated?

Semrush API charges units in one of two ways:

| Model | Description |
|-------|-------------|
| Per request | Fixed cost regardless of response size |
| Per line of data | Cost scales with the number of rows returned |

Unit costs are listed on each method's documentation page.

> Requests to the **Listing Management API** and **Map Rank Tracker API** do not consume API units.

---

## How do I check my unit balance and usage?

- **Free API call**: Returns your current remaining balance (see [api_unit_balance.md](api_unit_balance.md))
- **Query Log** (Semrush UI): Shows units consumed per query
- **Subscription info → API Units**: Shows your total remaining balance

---

## What support is available for API development?

- Full API documentation with method references and a Quick Start guide
- Contact Semrush Tech Support for troubleshooting help or custom API call assistance

---

## What countries does the API cover?

Coverage depends on the tool and report. Refer to the Stats documentation and check the information for the corresponding Semrush tools and reports.

---

## Why do API results differ from the Semrush UI?

Most discrepancies come from mismatched filters, scope, or time ranges. Common causes:

- Filters active in the UI but not in the API call (or vice versa)
- UI showing subfolder-level data while the API only supports root domain
- Different date ranges or cached vs. fresh data
- Pagination limits truncating results
- Naming differences between UI tools and API endpoints

See [troubleshooting.md](troubleshooting.md) for full details.

---

## Does the API have rate or usage limits?

Yes — rate and usage limits vary by API. See the API usage restrictions documentation for specifics.

---

## Will Semrush notify me about API changes?

- **Major changes**: Advance notice will be provided.
- **Minor changes**: Reflected in the API documentation.
- For specific inquiries, contact Semrush Tech Support or your account representative.

---

## How do I connect a CMS to the Listing Management API?

To integrate a CMS, CRM, or store locator with Semrush Listing Management:

1. Authenticate via OAuth.
2. Retrieve your existing location IDs via the API.
3. Send updates (name, address, hours, phone number) whenever your data changes.

Follow the Listing Management API tutorial for step-by-step instructions.
