# Projects API (OAuth 2.0) — CreateProject

Creates a new project, including naming the project and choosing a domain.

**Authentication:** OAuth 2.0 (not an API key). See [Projects API Overview](projects_api_overview.md#authorization).

## Endpoint

```
POST https://api.semrush.com/apis/v4/projects/v0
```

## Parameters

| Parameter | Required | Type | Description |
|---|---|---|---|
| `project_name` | No | string | The name the project will have. Cannot contain the following special symbols: `` ~ ` ! # % ' ^ & * = [ ] \ / | " : < > ? `` |
| `url` | No | string | The domain the project will be set up for. |

## Response Fields

| Field | Type | Description |
|---|---|---|
| `project_id` | uint64 | Automatically generated unique identifier for the project. |
| `project_name` | string | The name of the project. |
| `url` | string | The domain the project is set up for. |
| `tools` | object | List of project tools set up in the project. |
| `owner_id` | uint64 | The user ID number of the project's owner. |
| `permission` | string | The project permissions the user making the API call has. Possible values: `OWNER`, `READ`, `WRITE`, `CORP_ADMIN_READ`, `CORP_ADMIN_WRITE`. |
| `domain_unicode` | string | The domain the project is set up for, in Unicode. |

## Example Request Body

```json
{"project_name":"","url":""}
```

## Example Response

```json
{
  "url": "mysite.com",
  "domain_unicode": "mysite.com",
  "tools": [

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

- [ProjectsList](projects_oauth_list.md)
- [GetProject](projects_oauth_get.md)
- [UpdateProject](projects_oauth_update.md)
- [RemoveProject](projects_oauth_delete.md)
- [Projects API Overview](projects_api_overview.md)
