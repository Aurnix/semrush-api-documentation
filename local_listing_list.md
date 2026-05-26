# Listing Management — Get Locations

Returns a paginated list of all locations.

## Endpoint

```
GET https://api.semrush.com/apis/v4/local/v1/locations
```

## Headers

```
Authorization: Apikey YOUR_API_KEY
```

## Query Parameters

| Parameter | Required | Type | Description |
|---|---|---|---|
| `location_statuses` | No | array[string] | Comma-separated. Filter by status: `COMPLETED`, `PROCESSING`, `FAILED`. Example: `location_statuses=COMPLETED,PROCESSING`. |
| `limit` | No | integer | Page size. Default `50`. Max `50`. |
| `offset` | No | integer | Starting offset. Default `0`. |

## Response

`data` is an array of [Location](local_listing_overview.md#location-schema) objects. Each entry contains the same fields documented for [Get Location](local_listing_get.md).

## Example Request

```
curl -L 'https://api.semrush.com/apis/v4/local/v1/locations?location_statuses=COMPLETED,FAILED&limit=10&offset=10' \
  -H 'Authorization: Apikey YOUR_API_KEY'
```

## Example Response

```json
{
  "meta": {
    "success": true,
    "status_code": 200,
    "request_id": "94ea05c2c3f903450236cd4f36023631"
  },
  "data": [
    {
      "business_name": "Some business name",
      "phone_number": "+1 112-330-1303",
      "country": "US",
      "region": "TX",
      "city": "Austin",
      "zip": "78731",
      "address_line_1": "3305 Northland",
      "special_hours": [],
      "service_area_places": [],
      "category_ids": [
        "c8124a0c01554493a645a58bb1fd9247",
        "ee5ecf6d8dc14797b750e97f75b03e4f",
        "79ece4794d46492f8e936516001abace"
      ],
      "suppress_address": false,
      "coordinates": { "latitude": 30.334286, "longitude": -97.7568222 },
      "featured_message": "Call Today",
      "instagram_username": "some_username",
      "twitter_username": "some_username",
      "location_id": "b326158fb2a24777a76575b1883923e6",
      "location_status": "COMPLETED",
      "submit_date": "2026-02-16T14:38:14.57",
      "errors": []
    },
    {
      "business_name": "Another business name",
      "phone_number": "+357 16 932379",
      "country": "CY",
      "city": "Paphos",
      "zip": "8040",
      "address_line_1": "Apostolou Pavlou Avenue 99",
      "website_url": "https://some-website.com/",
      "description": "Established in 1954, Another Business Name remains a cornerstone of the domestic ball-bearing and gasket distribution industry.",
      "business_hours": {
        "monday_hours":    [{ "from": "09:00", "to": "17:00" }],
        "tuesday_hours":   [],
        "wednesday_hours": [],
        "thursday_hours":  [],
        "friday_hours":    [],
        "saturday_hours":  [],
        "sunday_hours":    []
      },
      "special_hours": [],
      "service_area_places": [],
      "category_ids": ["3e25b0338cf94ad8bd1c7d5a28140b65"],
      "suppress_address": false,
      "coordinates": { "latitude": 34.7851347, "longitude": 32.4174674 },
      "location_id": "15b4a2871cc14dda9fc448aed4060171",
      "location_status": "COMPLETED",
      "submit_date": "2026-02-03T12:03:05.301",
      "errors": []
    }
  ]
}
```

## See Also

- [Get Location](local_listing_get.md)
- [Create Location](local_listing_create.md)
- [Listing Management Overview](local_listing_overview.md)
