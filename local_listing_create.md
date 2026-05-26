# Listing Management — Create Location

Creates a new business location.

**Requires** a pre-paid [Local Pro limit](https://www.semrush.com/kb/1611-pricing-and-plans#local-pro-60-month). If the resulting `location_status` is `FAILED`, the Local Pro limit is released.

This endpoint does **not** support concurrent requests. Sending a new request while another is still processing returns `429 Too Many Requests`. Create locations sequentially.

## Endpoint

```
POST https://api.semrush.com/apis/v4/local/v1/locations
```

## Headers

```
Authorization: Apikey YOUR_API_KEY
Content-Type: application/json
```

## Query Parameters

| Parameter | Required | Type | Description |
|---|---|---|---|
| `validate_only` | No | boolean | When `true`, validate without persisting or consuming the Pro limit. Default `false`. |

## Request Body

| Field | Required | Type | Description |
|---|---|---|---|
| `business_name` | Yes | string | Max 125 chars. |
| `phone_number` | Yes | string | International format, e.g. `"+1 541-754-3010"`. |
| `country` | Yes | string | ISO 3166-1 alpha-2. See [supported countries](local_listing_overview.md#supported-countries-country). |
| `region` | Conditional | string | Required for `CA`, `AU`, `BR`, `IN`, `US`. |
| `city` | Yes | string | Max 64 chars. |
| `zip` | Conditional | string | Required for most countries. See [zip-required list](local_listing_overview.md#supported-countries-zip-required). |
| `address_line_1` | Yes | string | Street address. Max 190 chars. |
| `address_line_2` | No | string | Suite/floor/building. Max 64 chars. |
| `website_url` | No | string | Must start with `http://` or `https://`. Max 255 chars. |
| `description` | No | string | 10–750 chars. |
| `business_hours` | No | object | See [`business_hours`](local_listing_overview.md#business_hours). |
| `special_hours` | No | array[object] | Max 30 entries. Requires `business_hours`. See [`special_hours`](local_listing_overview.md#special_hours). |
| `service_area_places` | No | array[object] | See [`service_area_places`](local_listing_overview.md#service_area_places). |
| `category_ids` | Yes | array[string] | Max 10. IDs from [Get Categories](local_listing_categories.md). |
| `suppress_address` | No | boolean | If `true`, hide the physical address. Requires `service_area_places`. |
| `coordinates` | No | object | See [`coordinates`](local_listing_overview.md#coordinates). |
| `featured_message` | No | string | Max 50 chars. |
| `featured_message_url` | No | string | Max 255 chars. |
| `youtube_video` | No | string | Max 150 chars. |
| `instagram_username` | No | string | Max 30 chars. |
| `twitter_username` | No | string | Max 15 chars. |
| `reopen_date` | No | string | `YYYY-MM-DD`, future date. Only when the location is temporarily closed. |

## Response

Returns the full [Location schema](local_listing_overview.md#location-schema). The newly created location starts in `location_status=PROCESSING`.

| Response field | Notes |
|---|---|
| `location_id` | Server-assigned unique identifier. |
| `location_status` | `COMPLETED`, `PROCESSING`, or `FAILED`. See [status meanings](local_listing_overview.md#location_status). |
| `submit_date` | Timestamp of first submission. |
| `errors` | Async processing errors / system-level validation failures. |

## Example Request

```
curl -L 'https://api.semrush.com/apis/v4/local/v1/locations' \
  -H 'Authorization: Apikey YOUR_API_KEY' \
  -H 'Content-Type: application/json' \
  -d '{
    "business_name": "Some business name",
    "phone_number": "+1 435 864 3376",
    "country": "US",
    "region": "UT",
    "city": "Delta",
    "zip": "84624",
    "address_line_1": "Naumburger Str.2",
    "address_line_2": "Second floor",
    "website_url": "www.test.com",
    "description": "Welcome to our Some business name!",
    "category_ids": ["b871306d44c145a0b781ed2cb3b19bf1", "909c2eebd4fb4b338937d8518a3f0d73"],
    "coordinates": { "latitude": 39.35221240176079, "longitude": -112.57777149021301 },
    "featured_message": "Call Today",
    "featured_message_url": "www.test.com",
    "youtube_video": "https://www.youtube.com/watch?v=nYykbUPQ9eo",
    "instagram_username": "some_instagram_username",
    "twitter_username": "some_x_username"
  }'
```

## Example Response

```json
{
  "meta": {
    "success": true,
    "status_code": 200,
    "request_id": "182d587194adf5096d1b6d5b309f164f"
  },
  "data": {
    "business_name": "Some business name",
    "phone_number": "+1 435 864 3376",
    "country": "US",
    "region": "UT",
    "city": "Delta",
    "zip": "84624",
    "address_line_1": "Naumburger Str.2",
    "address_line_2": "Second floor",
    "website_url": "www.test.com",
    "description": "Welcome to our Some business name!",
    "special_hours": [],
    "service_area_places": [],
    "category_ids": [
      "b871306d44c145a0b781ed2cb3b19bf1",
      "909c2eebd4fb4b338937d8518a3f0d73"
    ],
    "suppress_address": false,
    "coordinates": {
      "latitude": 39.35221240176079,
      "longitude": -112.57777149021301
    },
    "featured_message": "Call Today",
    "featured_message_url": "www.test.com",
    "youtube_video": "https://www.youtube.com/watch?v=nYykbUPQ9eo",
    "instagram_username": "some_instagram_username",
    "twitter_username": "some_x_username",
    "location_id": "1d21ceab55d740709311ec9b8a12c01e",
    "location_status": "PROCESSING",
    "submit_date": "2026-03-10T17:03:42.691",
    "errors": []
  }
}
```

## See Also

- [Update Location](local_listing_update.md)
- [Get Location](local_listing_get.md)
- [Get Categories](local_listing_categories.md)
- [Listing Management Overview](local_listing_overview.md)
