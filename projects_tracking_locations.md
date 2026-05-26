# Position Tracking — Universal Location Search

**Price:** 100 API units per request

Searches for locations by ID, type (region, city, country, ZIP code, etc.), or name.

If called with no parameters, the request returns top locations ordered by location weight.

## Endpoint

```
GET https://api.semrush.com/position-tracking/management/v1/info/locations?key=YOUR_API_KEY
```

## Parameters

| Parameter | Required | Type | Description |
|---|---|---|---|
| `key` | Yes | string | API key from Subscription info > API units. |
| `location_id` | No | integer | Location ID. |
| `name` | No | string | Location name. |
| `country_code` | No | string | ISO 3166-1 Alpha-2 country code (e.g., `US`, `GB`, `DE`). |
| `type` | No | string | Location type. Values: `autonomous community`, `barrio`, `borough`, `canton`, `city`, `city region`, `country`, `county`, `department`, `district`, `governorate`, `municipality`, `municipality district`, `neighborhood`, `okrug`, `postal code`, `prefecture`, `province`, `quarter`, `region`, `state`, `sub-district`, `sub-ward`, `territory`, `union territory`. |
| `filter_engine` | No | string | Search engine. Values: `google`, `bing`, `baidu`. |

## Response Fields

| Field | Type | Description |
|---|---|---|
| `locations` | array | Array of location objects. |
| `locations[].available_volume_types` | array | Volume types available for this location (e.g., `national`, `regional`, `local`). |
| `locations[].location.id` | integer | Location ID. |
| `locations[].location.name` | string | Display name. |
| `locations[].location.formatted_name` | string | Formatted name. |
| `locations[].location.reversed_name` | string | Reversed-order name. |
| `locations[].location.canonical_name` | string | Canonical name. |
| `locations[].location.parent_id` | integer | Parent location ID. |
| `locations[].location.country_code` | string | ISO Alpha-2 country code. |
| `locations[].location.type` | string | Location type. |
| `locations[].location.languages` | array | Available languages, each with `id`, `hl`, `name`, `is_default`. |
| `locations[].location.weight` | integer | Location weight used for ordering. |

## Example Request

```
https://api.semrush.com/position-tracking/management/v1/info/locations?key=API_KEY&type=postal%20code&country_code=us
```

## Example Response

```json
{
  "locations": [
    {
      "available_volume_types": [
        "national"
      ],
      "location": {
        "id": 2840,
        "name": "United States",
        "formatted_name": "United States",
        "reversed_name": "United States",
        "canonical_name": "United States",
        "parent_id": 0,
        "country_code": "us",
        "type": "country",
        "languages": [
          {
            "id": 0,
            "hl": "en",
            "name": "English",
            "is_default": true
          },
          {
            "id": 0,
            "hl": "es",
            "name": "Spanish",
            "is_default": false
          }
        ],
        "weight": 2774
      }
    }
  ]
}
```

## See Also

- [Create a Position Tracking campaign](projects_tracking_create.md)
- [Position Tracking Overview](projects_tracking_overview.md)
