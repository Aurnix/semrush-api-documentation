# SEO API Tutorial — Import Semrush Data into Google Sheets

This tutorial covers two ways to pull Semrush SEO API CSV data into Google Sheets:

1. **Built-in cell formulas** — no code required.
2. **Apps Script** — more control, more secure (API key stays out of the sheet), and supports scheduling.

---

## Prerequisites

- Access to Standard API
- Your Semrush API key (from Subscription info → API Units)
- A Google account

---

## Option 1: Cell Formulas

Use `IMPORTDATA`, `SPLIT`, and `ARRAYFORMULA` to fetch and split the CSV response.

### Basic import (single column with semicolon-delimited rows)

```
=IMPORTDATA("https://api.semrush.com/?type=domain_organic&key=SEMRUSH_API_KEY&export_columns=Ph,Po,Nq,Cp&domain=example.com&database=us&display_limit=10")
```

### Import and split into columns

Semrush SEO API responses use semicolons as delimiters:

```
=ARRAYFORMULA(SPLIT(IMPORTDATA("https://api.semrush.com/?type=domain_organic&key=SEMRUSH_API_KEY&export_columns=Ph,Po,Nq,Cp&domain=example.com&database=us&display_limit=10"), ";"))
```

**Caveat:** The API key sits in plain text inside the formula — visible to anyone who can view the sheet. Use Option 2 if you want it hidden.

---

## Option 2: Apps Script

Apps Script lets you store the API key in Script Properties (hidden from sheet viewers), implement parsing logic, and schedule automatic refreshes.

### Step 1: Store Your API Key

1. Open the Google Sheet.
2. **Extensions → Apps Script** opens the script editor.
3. Click the gear icon for **Project Settings**.
4. Under **Script Properties**, click **Add script property**.
5. Property: `SEMRUSH_API_KEY`. Value: your API key. Save.

### Step 2: Add the Functions

In the Apps Script **Editor**, add and save the functions below.

#### Function 1 — Fetch and parse the data

```javascript
function getSemrushData(domain) {
  var apiKey = PropertiesService.getScriptProperties().getProperty('SEMRUSH_API_KEY');
  var apiUrl = `https://api.semrush.com/?type=domain_organic&key=${apiKey}&export_columns=Ph,Po,Nq,Cp&domain=${domain}&database=us&display_limit=10`;
  var response = UrlFetchApp.fetch(apiUrl);
  var csvData = response.getContentText();
  var rows = Utilities.parseCsv(csvData, ";");
  return rows;
}
```

#### Function 2 — Store the data in a month-named sheet

Creates a fresh sheet named after the current month (e.g., `June 2025`) and writes the data.

```javascript
function fetchAndStoreMonthlyData() {
  var spreadsheet = SpreadsheetApp.getActiveSpreadsheet();
  var domain = 'example.com'; // Replace with your domain
  var rows = getSemrushData(domain);
  var sheetName = Utilities.formatDate(new Date(), Session.getScriptTimeZone(), "MMMM yyyy");
  var sheet = spreadsheet.insertSheet(sheetName);
  rows.forEach(row => sheet.appendRow(row));
}
```

#### Function 3 — Schedule monthly execution

Creates a time-based trigger that runs `fetchAndStoreMonthlyData()` at 9 AM on the 1st of every month, if one doesn't already exist.

```javascript
function createMonthlyTrigger() {
  var exists = ScriptApp.getProjectTriggers().some(t => t.getHandlerFunction() === 'fetchAndStoreMonthlyData');
  if (!exists) {
    ScriptApp.newTrigger('fetchAndStoreMonthlyData')
      .timeBased()
      .everyMonths(1)
      .onMonthDay(1)
      .atHour(9)
      .create();
  }
}
```

### Step 3: Execute

Run `createMonthlyTrigger()` once from the Apps Script Editor to set up the schedule. Grant the requested permissions when prompted.

After that, the script runs automatically on the 1st of each month — a new sheet is created and populated.

### Tips

- For one-off use without a schedule, call `getSemrushData()` directly from a cell:
  ```
  =getSemrushData("example.com")
  ```
- Add error handling (try/catch, response code checks) before relying on this in production.
- Customize the `apiUrl` for any SEO API endpoint — the parsing logic works for any CSV response.

---

## What's Next

Once data is in Google Sheets, you can extend the workflow:

- **Looker Studio** — connect the sheet as a data source for custom dashboards.
- **BigQuery** — push the sheet data into BigQuery for larger datasets and advanced analysis, then connect it to Looker Studio or other visualization tools.
