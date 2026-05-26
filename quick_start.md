# Quick Start

This guide covers getting your API key, constructing an API call, and retrieving and processing data. Examples use the SEO API and the Domain Overview request.

---

## Get API Key

1. Click the account icon at the top right of the Semrush interface.
2. Select **Subscription info** and go to the **API Units** tab.
3. Copy your API key.

Check your API unit balance before making your first request to ensure it's sufficient.

---

## Construct Your API Call

### Request Example (Domain Overview)

```
https://api.semrush.com/?key=API_KEY&type=domain_ranks&export_columns=Db,Dn,Rk,Or,Ot,Oc,Ad,At,Ac,Sh,Sv&domain=apple.com&database=us
```

### Build Steps

1. Start with the base URL: `https://api.semrush.com/`
2. Add `?` to begin query parameters.
3. Add your API key: `key=API_KEY`
4. Separate each parameter with `&`.
5. Add required parameters:
   - Report type: `type=domain_ranks`
   - Domain: `domain=apple.com`
6. Add optional parameters as needed:
   - Database: `database=us`
   - Columns: `export_columns=Db,Dn,Rk,Or,Ot,Oc,Ad,At,Ac,Sh,Sv`

> URL format varies by product. The Trends API has a different request structure — refer to its own docs.

---

## Saving API Units

### display_limit

Certain reports support `display_limit` to cap the number of rows returned.

```
&display_limit=10
```

This limits the response to the top 10 results, reducing API unit consumption.

---

## URL Encoding Special Characters

Parameter values containing special characters must be URL-encoded. Common characters used in Semrush API calls (e.g., in Filters):

| Character | Encoded |
|-----------|---------|
| `#` | `%23` |
| `&` | `%26` |
| `*` | `%2A` |
| `+` | `%2B` |
| `-` | `%2D` |
| `:` | `%3A` |
| `\|` | `%7C` |
| `%` | `%25` |
| `/` | `%2F` |

---

## Test Your API Call

Testing is optional but recommended before integrating. **Note: test calls consume API units.**

Use Postman or cURL to verify:

1. **Authentication** — correct API credentials are included.
2. **Data relevance** — use filters and query parameters to request only what's needed.
3. **Response structure** — confirm the response format and content match expectations.

---

## Retrieve and Process Data

Automate data retrieval with a script that handles API calls, processing, storage, and downstream integration.

### Step 1: Fetch Data

- Handle authentication in every request.
- Respect rate limits.
- Fetch only relevant data using filters.

### Step 2: Handle Errors

Implement error handling with logging and retry logic for failed or incomplete requests.

Each API has its own error format:

| API | Error Docs |
|-----|-----------|
| SEO API | Error messages section in SEO API overview |
| Trends API | Error messages section in Trends API overview |
| Projects API | Error messages section in Projects API overview |
| Local API | Status codes section in Local API overview |

### Step 3: Process the Response

Parse or convert the response into your required format.

### Step 4: Store or Transfer Data

Options for storing Semrush API output:

- **Cloud storage**: Amazon S3, Google Cloud Storage
- **Databases / data warehouses**: BigQuery, Snowflake
- **SFTP servers**

### Step 5: Integrate with BI and CRM Tools

Load processed data into downstream platforms:

- **BI / dashboards**: Power BI, Tableau, Looker Studio
- **CRM**: Salesforce

Third-party connectors (Supermetrics, Workato, Zapier) can simplify these integrations without heavy development.

### Step 6: Automate Recurring Updates

Keep data current with scheduled execution:

- **OS schedulers**: Task Scheduler (Windows), cron (Linux/macOS)
- **Third-party automation tools** to trigger API calls on a schedule
