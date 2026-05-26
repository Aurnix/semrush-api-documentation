# Projects API — Create A New Project

**Price:** 100 API units per request

Creates a new project, names it, and assigns a domain.

## Endpoint

```
POST https://api.semrush.com/management/v1/projects?key=API_KEY
```

## Parameters

| Parameter | Required | Description |
|---|---|---|
| `key` | Yes | API key from Subscription info > API units. |
| `url` | Yes | Project domain. Example: `mysite.com` |
| `project_name` | No | Project name. The following symbols are not allowed: `` ~ ` ! # % ' ^ & * = [ ] \ / { } | " : < > ? `` |

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

## Example Request Body

```json
{"project_name":"myproject","url":"mysite.com"}
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
  "project_name": "myproject",
  "owner_id": 123456780,
  "permission": [
    "OWNER"
  ]
}
```

## See Also

- [List All Existing Projects](projects_list.md)
- [Get Information About An Existing Project](projects_get.md)
- [Update An Existing Project](projects_update.md)
- [Delete An Existing Project](projects_delete.md)
- [Projects API Overview](projects_api_overview.md)
