# Projects API — Update An Existing Project

**Price:** 100 API units per request

Renames an existing project.

## Endpoint

```
PUT https://api.semrush.com/management/v1/projects?key=API_KEY
```

## Parameters

| Parameter | Required | Description |
|---|---|---|
| `key` | Yes | API key from Subscription info > API units. |
| `project_id` | Yes | Project ID. See [how to get your project ID](projects_api_overview.md#get-your-project-id). |
| `project_name` | Yes | New project name. |

## Response Fields

| Field | Type | Description |
|---|---|---|
| `project_id` | ID | Project ID. |
| `project_name` | string | New project name. |
| `url` | string | Project domain. |
| `domain_unicode` | string | Project domain encoded in Unicode. |
| `tools` | list | List of project tools activated by the user. |
| `owner_id` | ID | Project owner ID. |
| `permission` | list | Project permissions of the user with the submitted ID key. Possible values: `OWNER`, `READ`, `WRITE`, `CORP_ADMIN_READ`, `CORP_ADMIN_WRITE`. |

## Example Request Body

```json
{"project_id":643526670283248, "project_name":"New project name"}
```

## Example Response

```json
{
  "url": "mysite.com",
  "domain_unicode": "mysite.com",
  "tools": [
    {
      "tool": "tracking"
    }
  ],
  "project_id": 643526670283248,
  "project_name": "New project name",
  "owner_id": 123456780,
  "permission": [
    "OWNER"
  ]
}
```

## See Also

- [List All Existing Projects](projects_list.md)
- [Get Information About An Existing Project](projects_get.md)
- [Create A New Project](projects_create.md)
- [Delete An Existing Project](projects_delete.md)
- [Projects API Overview](projects_api_overview.md)
