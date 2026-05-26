# Projects API (OAuth 2.0) — RemoveProject

Deletes a project from your user account.

**Authentication:** OAuth 2.0 (not an API key). See [Projects API Overview](projects_api_overview.md#authorization).

## Endpoint

```
DELETE https://api.semrush.com/apis/v4/projects/v0/:project_id
```

## Parameters

| Parameter | Required | Type | Description |
|---|---|---|---|
| `project_id` | Yes | uint64 | Automatically generated unique identifier for the project. See [how to get your project ID](projects_api_overview.md#get-your-project-id). |

## Response Fields

| Field | Type | Description |
|---|---|---|
| `result` | bool | `true` if the project is successfully deleted; otherwise an error message is returned. |

## Example Request

```
project_id=0
```

## Example Response

```json
{
  "result": true
}
```

## See Also

- [ProjectsList](projects_oauth_list.md)
- [GetProject](projects_oauth_get.md)
- [CreateProject](projects_oauth_create.md)
- [UpdateProject](projects_oauth_update.md)
- [Projects API Overview](projects_api_overview.md)
