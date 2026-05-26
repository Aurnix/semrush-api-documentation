# Projects API (OAuth 2.0) — GetProject

Returns information about a single project.

**Authentication:** OAuth 2.0 (not an API key). See [Projects API Overview](projects_api_overview.md#authorization).

## Endpoint

```
GET https://api.semrush.com/apis/v4/projects/v0/:project_id
```

## Parameters

| Parameter | Required | Type | Description |
|---|---|---|---|
| `project_id` | Yes | uint64 | Automatically generated unique identifier for the project. See [how to get your project ID](projects_api_overview.md#get-your-project-id). |

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

## Example Request

```
project_id=643526670283248
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

- [ProjectsList](projects_oauth_list.md)
- [CreateProject](projects_oauth_create.md)
- [UpdateProject](projects_oauth_update.md)
- [RemoveProject](projects_oauth_delete.md)
- [Projects API Overview](projects_api_overview.md)
