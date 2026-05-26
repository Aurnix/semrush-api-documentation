# Projects API — List All Existing Projects

**Price:** 100 API units per request

Returns a list of all projects with their ID, project name, domain name, and tools activated for each project.

## Endpoint

```
GET https://api.semrush.com/management/v1/projects
```

## Parameters

| Parameter | Required | Description |
|---|---|---|
| `key` | Yes | API key from Subscription info > API units. |
| `filter` | No | Filter projects by user permissions. Values: `all` (no filter), `own` (default — only projects owned by the user), `shared` (shared projects only), `corporate` (for corporate subscribers only). |

## Response Fields

| Field | Type | Description |
|---|---|---|
| `project_id` | ID | Project ID. |
| `project_name` | string | Project name. |
| `url` | string | Project domain. |
| `domain_unicode` | string | Project domain encoded in Unicode. |
| `tools` | list | List of project tools activated by the user. |
| `owner_id` | ID | Project owner ID. |
| `permission` | list | Project permissions of the user with the submitted ID key. Possible values: `OWNER`, `READ`, `WRITE`, `CORP_ADMIN_READ`, `CORP_ADMIN_WRITE`. |

## Example Request

```
https://api.semrush.com/management/v1/projects?key=API_KEY
```

## Example Response

```json
[
  {
    "url": "mysite.com",
    "domain_unicode": "mysite.com",
    "tools": [
      {
        "tool": "tracking"
      }
    ],
    "project_id": 643526670283248,
    "project_name": "myproject",
    "owner_id": 123456780,
    "permission": [
      "OWNER"
    ]
  }
]
```

## See Also

- [Get Information About An Existing Project](projects_get.md)
- [Create A New Project](projects_create.md)
- [Update An Existing Project](projects_update.md)
- [Delete An Existing Project](projects_delete.md)
- [Projects API Overview](projects_api_overview.md)
