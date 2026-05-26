# Listing Management — Update Location

Updates a single location by its ID. Follows PATCH semantics: only fields listed in `update_mask` are touched. See [PATCH semantics](local_listing_overview.md#update_mask-patch-semantics) for the set/clear rules.

## Endpoint

```
PATCH https://api.semrush.com/apis/v4/local/v1/locations/:location_id
```

## Headers

```
Authorization: Apikey YOUR_API_KEY
Content-Type: application/json
```

## Path Parameters

| Parameter | Required | Type | Description |
|---|---|---|---|
| `location_id` | Yes | string | The location ID returned by [Create Location](local_listing_create.md) or [Get Locations](local_listing_list.md). |

## Query Parameters

| Parameter | Required | Type | Description |
|---|---|---|---|
| `update_mask` | Yes | array[string] | Comma-separated list of fields to update. See [allowed fields](#update_mask-allowed-fields). |
| `validate_only` | No | boolean | When `true`, validate without persisting. Default `false`. |

### `update_mask` Allowed Fields

`business_name`, `address_line_1`, `address_line_2`, `city`, `zip`, `phone_number`, `category_ids`, `region`, `featured_message`, `featured_message_url`, `website_url`, `description`, `instagram_username`, `twitter_username`, `business_hours`, `special_hours`, `service_area_places`, `suppress_address`, `coordinates`, `youtube_video`, `reopen_date`

To clear a field, include its name in `update_mask` but omit it from the body. To set a field, include it in both.

## Request Body

Send only the fields you are setting. The body uses the same shape as [Create Location](local_listing_create.md#request-body), with `country` not modifiable here. Field constraints are the same — see the [Location schema](local_listing_overview.md#location-schema).

## Response

Returns the full updated [Location](local_listing_overview.md#location-schema).

## Example Request

```
curl -L -X PATCH \
  'https://api.semrush.com/apis/v4/local/v1/locations/04f447bda9f845d691fb4cc37daba031?update_mask=address_line_1,business_name,address_line_2' \
  -H 'Content-Type: application/json' \
  -H 'Authorization: Apikey YOUR_API_KEY' \
  -d '{
    "business_name": "Updated business name",
    "address_line_1": "Naumburger Str."
  }'
```

> The example above clears `address_line_2` (included in `update_mask` but not in the body), and sets the other two fields.

## Example Response

```json
{
  "meta": {
    "success": true,
    "status_code": 200,
    "request_id": "9d55854e927ecaea7d80707cc8282189"
  },
  "data": {
    "business_name": "Updated business name",
    "phone_number": "+1 222-666-1111",
    "country": "US",
    "region": "CA",
    "city": "New Brettmouth",
    "zip": "08527",
    "address_line_1": "Naumburger Str.",
    "website_url": "www.test.com",
    "description": "Some description here",
    "special_hours": [],
    "service_area_places": [
      { "name": "17763",        "place_id": "DJYLLjkCOgvNiWDFEeiPIhXcAFpKRCJSGjsFdeV" },
      { "name": "North Many",   "place_id": "AJfjhjLYkPiHljnHruSOntPsMLvsNthJqycYbSX" },
      { "name": "West Bradley", "place_id": "nYUkPeFsrTzygxnKapBRoBolALdaBxnqLyVhBRe" }
    ],
    "category_ids": ["42e91d12d5dd45029c709f223545abd5"],
    "suppress_address": false,
    "coordinates": {
      "latitude": -6.761864717379694,
      "longitude": 13.537953520639036
    },
    "instagram_username": "some_user",
    "twitter_username": "some_user",
    "location_id": "04f447bda9f845d691fb4cc37daba031",
    "location_status": "COMPLETED",
    "submit_date": "2026-03-03T11:44:43.19",
    "errors": []
  }
}
```

## See Also

- [Create Location](local_listing_create.md)
- [Get Location](local_listing_get.md)
- [Listing Management Overview](local_listing_overview.md)
