# Projects API — Delete An Existing Project

**Price:** 100 API units per request

Deletes a project and all campaigns in the activated tools.

## Endpoint

```
DELETE https://api.semrush.com/management/v1/projects/{id}?key=API_KEY
```

## Parameters

| Parameter | Required | Description |
|---|---|---|
| `key` | Yes | API key from Subscription info > API units. |
| `id` | Yes | Project ID. See [how to get your project ID](projects_api_overview.md#get-your-project-id). |

## Example Request

```
https://api.semrush.com/management/v1/projects/{id}?key=API_KEY
```

## See Also

- [List All Existing Projects](projects_list.md)
- [Get Information About An Existing Project](projects_get.md)
- [Create A New Project](projects_create.md)
- [Update An Existing Project](projects_update.md)
- [Projects API Overview](projects_api_overview.md)
