# Projects API (OAuth 2.0) — ProjectsList

Returns a list of all projects.

**Authentication:** OAuth 2.0 (not an API key). See [Projects API Overview](projects_api_overview.md#authorization).

## Endpoint

```
GET https://api.semrush.com/apis/v4/projects/v0
```

## Parameters

None.

## Response Fields

| Field | Type | Description |
|---|---|---|
| `projects` | object | Array of project objects. Each contains `project_id`, `project_name`, `url`, `domain_unicode`, `tools`, `owner_id`, `permission`. See [GetProject](projects_oauth_get.md) for full field definitions. |

## Example Response

```json
{
  "projects": [
    {
      "url": "mysite.com",
      "domain_unicode": "mysite.com",
      "tools": [

      ],
      "project_id": 643526670,
      "project_name": "myproject",
      "owner_id": 123456780,
      "permission": [
        "OWNER"
      ]
    }
  ]
}
```

## See Also

- [GetProject](projects_oauth_get.md)
- [CreateProject](projects_oauth_create.md)
- [UpdateProject](projects_oauth_update.md)
- [RemoveProject](projects_oauth_delete.md)
- [Projects API Overview](projects_api_overview.md)
