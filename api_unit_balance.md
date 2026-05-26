# API Unit Balance

API units are consumed with each request. If you run out, you can purchase more via the Subscription info page or contact sales.

---

## Check Your Balance

Two ways to check remaining units:

1. **Semrush UI**: Subscription info → API Units tab
2. **API request**: Use the free endpoints below

### Standard API — Check Balance

**Cost:** Free (0 units)

```
GET http://www.semrush.com/users/countapiunits.html
```

| Parameter | Required | Description |
|-----------|----------|-------------|
| `key` | Yes | Your API key |

**Request example:**

```
http://www.semrush.com/users/countapiunits.html?key=YOUR_API_KEY
```

**Response (CSV):**

```
1,000
```

---

### Trends API — Check Balance

**Cost:** Free (0 units)  
**Rate limit:** 10 requests per second (RPS) per account

Returns monthly API unit usage. Response also includes legacy daily and hourly fields kept for backward compatibility — these are no longer used or decremented.

```
GET http://api.semrush.com/analytics/ta/limits/key/
```

| Parameter | Required | Description |
|-----------|----------|-------------|
| `key` | Yes | Your API key (in the URL path) |

**Request example:**

```
http://api.semrush.com/analytics/ta/limits/key/API_KEY
```

---

## How API Units Are Consumed

Unit cost varies by report type and data volume:

| Pricing Model | Example |
|---------------|---------|
| Per line of data returned | Domain reports |
| Fixed cost per request | Backlinks overview |

> Requests to **Listing Management** and **Map Rank Tracker** endpoints do not consume API units.

**Historical data** costs more than regular data. See the SEO API overview for details.

---

## Check Price Per Request

Unit cost for each report is listed in its documentation. The total cost is calculated based on the number of lines in the response.

---

## Optimize Unit Consumption

1. **Use `display_limit`** — Caps the number of rows returned. Example: `&display_limit=10` returns only the top 10 results.
2. **Estimate cost before requesting** — Calculate expected unit consumption to avoid surprises.

### Cost Calculation Example

Scenario: Domain Organic Search Keywords report for 50 domains, 500 keywords each.

| Data Type | Cost Per Keyword | Keywords | Domains | Total Units |
|-----------|-----------------|----------|---------|-------------|
| Regular (current month) | 10 units | 500 | 50 | 250,000 |
| Historical (12 months ago) | 50 units | 500 | 50 | 1,250,000 |
| **Total** | | | | **1,500,000** |

---

## What Happens When You Run Out

### Errors

| API | Error |
|-----|-------|
| SEO API, Trends API, Projects API (API key) | `ERROR 132` |
| Local API, Projects API (OAuth 2.0) | HTTP `403` |

**403 error response format:**

```json
{
  "error": {
    "code": 403,
    "message": "...",
    "description": "..."
  }
}
```

### Partial Responses

For per-line reports in the SEO API, Trends API, and Projects API (API key): if you have insufficient units for the full result set, the API returns as many lines as your balance allows rather than failing entirely. Always check your balance beforehand to avoid incomplete data.

---

## API Query Log

Review recent API requests and unit consumption at: **My Profile → Query log → API Queries**

> Only covers SEO API and Projects API (API key). Trends API, Local API, and Projects API (OAuth 2.0) logs are not included. Contact Semrush Customer Support to review Trends API logs.

### Log Fields

| Field | Description |
|-------|-------------|
| Query | Domain, subdomain, subfolder, URL, or keyword queried |
| Time | When the request was sent |
| User IP address | IP that initiated the request |
| DB | Database selected (when applicable) |
| Report type | Specific API report requested |
| Historical | Whether historical data was requested |
| Requested rows | Number of rows queried |
| Offset | `display_offset` value used |
| Report cost | API units spent for data returned |
| API units | Balance remaining after that request |

### Exporting the Log

Export as CSV using the **Export** button in the API Queries report. Options:

- All available records (up to 50,000)
- First N rows: 100, 500, 1,000, 10,000, 30,000, or 50,000

For logs exceeding 50,000 entries, contact Semrush Customer Support.
