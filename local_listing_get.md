# Listing Management — Get Location

Returns a single location by its ID.

## Endpoint

```
GET https://api.semrush.com/apis/v4/local/v1/locations/:location_id
```

## Headers

```
Authorization: Apikey YOUR_API_KEY
```

## Path Parameters

| Parameter | Required | Type | Description |
|---|---|---|---|
| `location_id` | Yes | string | The location ID. |

## Response

Returns the full [Location schema](local_listing_overview.md#location-schema), including `business_hours`, `special_hours`, `service_area_places`, `coordinates`, and the response-only fields `location_status`, `submit_date`, and `errors`.

## Example Request

```
curl -L 'https://api.semrush.com/apis/v4/local/v1/locations/3e8d046f62fe4b73802112e138a78532' \
  -H 'Authorization: Apikey YOUR_API_KEY'
```

## Example Response

```json
{
  "meta": {
    "success": true,
    "status_code": 200,
    "request_id": "fc8e2dd369a9ed46f93ebffd9660afa0"
  },
  "data": {
    "business_name": "Delta Manor Apartments",
    "phone_number": "+1 435 864 3376",
    "country": "US",
    "region": "UT",
    "city": "Delta",
    "zip": "84624",
    "address_line_1": "111 W Main St, Delta, UT 84624, United States",
    "address_line_2": "Second floor",
    "website_url": "www.test.com",
    "description": "Welcome to our Some business name!",
    "business_hours": {
      "monday_hours":    [{ "from": "08:00", "to": "12:00" }, { "from": "14:00", "to": "18:00" }],
      "tuesday_hours":   [{ "from": "08:00", "to": "12:00" }, { "from": "14:00", "to": "18:00" }],
      "wednesday_hours": [{ "from": "08:00", "to": "12:00" }, { "from": "14:00", "to": "18:00" }],
      "thursday_hours":  [{ "from": "08:00", "to": "12:00" }, { "from": "14:00", "to": "18:00" }],
      "friday_hours":    [{ "from": "08:00", "to": "12:00" }, { "from": "14:00", "to": "18:00" }],
      "saturday_hours":  [{ "from": "08:00", "to": "14:00" }],
      "sunday_hours":    []
    },
    "special_hours": [
      { "type": "CLOSED",         "day": "2026-05-01", "times": [] },
      { "type": "OPENED_ALL_DAY", "day": "2026-12-24", "times": [] },
      { "type": "RANGE",          "day": "2026-03-11", "times": [{ "from": "14:00", "to": "18:00" }] }
    ],
    "service_area_places": [
      { "name": "Delta, UT, USA", "place_id": "ChIJQRRb_PG0TIcRwoI8h4xTvTM" },
      { "name": "UT, USA",        "place_id": "ChIJzfkTj8drTIcRP0bXbKVK370" }
    ],
    "category_ids": [
      "b871306d44c145a0b781ed2cb3b19bf1",
      "909c2eebd4fb4b338937d8518a3f0d73"
    ],
    "suppress_address": true,
    "coordinates": {
      "latitude": 39.35221240176079,
      "longitude": -112.57777149021301
    },
    "featured_message": "Call Today",
    "featured_message_url": "www.test.com",
    "youtube_video": "https://www.youtube.com/watch?v=nYykbUPQ9eo",
    "instagram_username": "some_instagram_username",
    "twitter_username": "some_x_username",
    "location_id": "6d6ac5e772284c569c6ca109008b4c4f",
    "location_status": "COMPLETED",
    "submit_date": "2025-08-14T15:57:56.414",
    "errors": []
  }
}
```

## See Also

- [Get Locations](local_listing_list.md)
- [Update Location](local_listing_update.md)
- [Listing Management Overview](local_listing_overview.md)
