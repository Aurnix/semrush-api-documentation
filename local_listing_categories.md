# Listing Management — Get Categories

Returns a paginated list of business categories for a specific country. Use the returned `id` values in the `category_ids` field on [Create Location](local_listing_create.md) and [Update Location](local_listing_update.md).

## Endpoint

```
GET https://api.semrush.com/apis/v4/local/v1/categories
```

## Headers

```
Authorization: Apikey YOUR_API_KEY
```

## Query Parameters

| Parameter | Required | Type | Description |
|---|---|---|---|
| `country` | Yes | string | ISO 3166-1 alpha-2 country code. See [supported countries](local_listing_overview.md#supported-countries-country). |
| `limit` | No | integer | Page size. Default `1000`. Max `1000`. |
| `offset` | No | integer | Starting offset. Default `0`. |

## Response Fields

| Field | Type | Description |
|---|---|---|
| `id` | string | Unique category identifier. |
| `name` | string | Display name. |
| `full_name` | string | Hierarchical path, e.g. `"Books > Comic book store"`. |
| `parent_id` | string / null | Parent category ID. `null` for top-level categories. |

## Example Request

```
curl -L 'https://api.semrush.com/apis/v4/local/v1/categories?country=CZ&limit=1000&offset=1000' \
  -H 'Authorization: Apikey YOUR_API_KEY'
```

## Example Response

> The source response example is truncated after the second entry.

```json
{
  "meta": {
    "success": true,
    "status_code": 200,
    "request_id": "c2ad517a4e341f07b543f0f68477e9fa"
  },
  "data": [
    {
      "id": "46e6afbab7cd408bae8d392184a5627e",
      "name": "Marble supplier",
      "full_name": "Businesses and Services > Supplier > Marble supplier",
      "parent_id": "12898ed82f5849b1abb684887b82b464"
    },
    {
      "id": "836dca5e11c546c49eb8802e9efe2d54",
      "name": "Metal industry suppliers",
      "full_name": "Businesses and Services > Supplier > Metal industry suppliers",
      "parent_id": "12898ed82f5849b1abb684887b82b464"
    }
  ]
}
```

## See Also

- [Create Location](local_listing_create.md)
- [Update Location](local_listing_update.md)
- [Listing Management Overview](local_listing_overview.md)
