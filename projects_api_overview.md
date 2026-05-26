# Projects API — Overview

## About

The Projects API includes several endpoint groups:

- **Projects API (API key)** — get information about your folders (formerly called projects) and manage them. Endpoints: [List](projects_list.md), [Get](projects_get.md), [Create](projects_create.md), [Update](projects_update.md), [Delete](projects_delete.md).
- **Projects API (OAuth 2.0)** — same operations as above, using OAuth 2.0 authorization. Endpoints: [ProjectsList](projects_oauth_list.md), [GetProject](projects_oauth_get.md), [CreateProject](projects_oauth_create.md), [UpdateProject](projects_oauth_update.md), [RemoveProject](projects_oauth_delete.md).
- **[Position Tracking API](projects_position_tracking.md)** — monitor keyword rankings, visibility, and competitors' performance across search engines and locations. Provides access to ranking data for specific keywords, devices, and regions.
- **[Site Audit API](projects_site_audit.md)** — automatically crawl websites, identify technical SEO issues, and retrieve structured reports about site health and performance. Run new audits, monitor ongoing crawl progress, and access detailed reports on errors, warnings, and notices.

## Get Access

To use the Projects API, you must have the **SEO Business subscription** and available API units.

## Authorization

Different Projects API endpoints require different authorization methods:

- **Projects (API key)**, **Position Tracking**, and **Site Audit** APIs require an [API key](authorization.md).
- **Projects (OAuth 2.0)** uses OAuth 2.0 authorization.

## Response Format

All endpoints in the Projects API return responses in **JSON format**.

| Result  | Code     |
|---------|----------|
| Success | HTTP 200 |
| Error   | HTTP 400 |

## Error Messages

The Projects (API key), Position Tracking, and Site Audit APIs return error messages in the following format:

```json
{
  "code": "{ERROR_CODE}",
  "message": "{ERROR_MESSAGE}"
}
```

| Field           | Type    | Description                       |
|-----------------|---------|-----------------------------------|
| `ERROR_CODE`    | integer | Machine-parseable codes.          |
| `ERROR_MESSAGE` | string  | Descriptive error text.           |

In addition to a descriptive error text, error messages contain machine-parsable codes. While the text for an error message may change, the codes will stay the same.

### Error Codes

| Code | Error Message                                                                              | Recommended Action                                                                                                                |
|------|--------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------|
| 70   | API key hash failure                                                                       | Double-check that your API key is correct and valid.                                                                              |
| 120  | Wrong key-ID pair                                                                          | Check that the API key is correct. You can find your key in the Subscription info section.                                        |
| 121  | Wrong format or empty hash                                                                 | Check that the API key is correct. You can find your key in the Subscription info section.                                        |
| 122  | Wrong format or empty key                                                                  | Check that the API key is correct. You can find your key in the Subscription info section.                                        |
| 130  | API disabled                                                                               | Upgrade your subscription plan to get access to the API.                                                                          |
| 131  | Limit exceeded                                                                             | The API request limit for the requested report has been reached. Contact the Semrush Support Team.                                |
| 132  | API units balance is zero                                                                  | You have used all your API units. To continue using the API, recharge your API unit balance or upgrade your subscription.         |
| 134  | Total limit exceeded                                                                       | The total API request limit has been reached. Contact the Semrush Support Team.                                                   |
| 511  | Unknown error                                                                              | Contact the Semrush Support Team and provide them with your API request.                                                          |
| 512  | Can't find project with project_id {ID}                                                    | Check that the project ID is correct.                                                                                             |
| 513  | Invalid 'tool_id'                                                                          | Check that the tool ID is correct.                                                                                                |
| 515  | Campaign already exists                                                                    | A campaign with the same parameters already exists. Create a new one.                                                             |
| 519  | Missing mandatory URL parameter                                                            | Check that you have added all the required parameters in the request URL.                                                         |
| 520  | Invalid tag name                                                                           | Check that the tag name is correct.                                                                                               |
| 521  | Projects limit exceed, projects created: {projects_count}, user limit are {projects_limit} | You have reached the limit of projects for your account. To create a new project, delete an existing one.                         |
| 522  | Keywords limit exceed, keywords limit {keywords_limit} already tracked keywords {keywords_count} | You have reached the limit of keywords for your account. To add new keywords, buy more keywords or remove some of the existing ones. |

The **Projects API (OAuth 2.0)** uses HTTP status codes, like the Local API.

## Project and Campaign IDs

To make requests using the Projects, Position Tracking, and Site Audit API methods, you need to get your project and campaign IDs.

### Get Your Project ID

1. Navigate to the main [Projects](https://www.semrush.com/) page and select the required project.
2. Check the page URL in your browser's address bar — it'll look like: `https://www.semrush.com/projects/6647718`
3. The number after `projects` is your project ID. In this example, it's `6647718`. Copy and save it for future requests.

### Get Your Campaign ID

1. Open your campaign using the Position Tracking tool.
2. Check the page URL — it'll look like: `https://www.semrush.com/tracking/landscape/6647718_272401.html?domain_1=wikipedia.org`
3. The number before the underscore is the project ID (in this example, `6647718`). The full number including the underscore is the campaign ID (in this example, `6647718_272401`). Copy these numbers and save them for future requests.

### Get Multiple Project and Campaign IDs

- Use the **List All Existing Projects** request from the [Projects API](projects_projects.md) to return a list of all your projects, including their IDs and basic information.
- To find the IDs for multiple campaigns within a project, use the **Get a list of campaigns** request from the [Position Tracking API](projects_position_tracking.md), specifying the project ID you need.
