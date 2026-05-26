# Listing Management API — Overview

The current Listing Management API lets you push location data into Semrush Listing Management in bulk and distribute it across directories. For authorization, base URL conventions, response envelope, and status codes, see the [Local API overview](local_api_overview.md).

## Base URL

```
https://api.semrush.com/apis/v4/local/v1/
```

All requests must include `Authorization: Apikey <YOUR_API_KEY>`.

## Endpoints

- [Create Location](local_listing_create.md) — `POST /locations`
- [Update Location](local_listing_update.md) — `PATCH /locations/:location_id`
- [Get Location](local_listing_get.md) — `GET /locations/:location_id`
- [Get Locations](local_listing_list.md) — `GET /locations`
- [Get Categories](local_listing_categories.md) — `GET /categories`

## Common Behaviors

### `validate_only`

Available on Create and Update. When `true`, the API performs validation only — no data is persisted, and the Pro limit is **not** consumed. Default `false`.

### `update_mask` (PATCH semantics)

The Update Location endpoint follows PATCH semantics. You must supply a non-empty `update_mask` listing every field you intend to change.

- To **set** a field, include it in `update_mask` **and** in the request body.
- To **clear** a field (set it to `null`), include it in `update_mask` and **omit** it from the body.

### Concurrency

The Create Location endpoint does not support concurrent requests. Initiating a new Create while another is still processing returns `429 Too Many Requests`. Create locations sequentially.

### `location_status`

| Status | Meaning |
|---|---|
| `COMPLETED` | Location is ready. All features and data management are accessible. |
| `PROCESSING` | Location is being initialized. Editing is unavailable until processing completes. |
| `FAILED` | Location could not be created. Does not consume user limits — delete and retry. Contact [Semrush Support](https://www.semrush.com/company/contacts/) if the issue persists. |

## Location Schema

Fields shared across Create / Update / Get / Get Locations.

| Field | Type | Constraint | Description |
|---|---|---|---|
| `location_id` | string | response only | Unique identifier for the location. |
| `business_name` | string | max 125 chars | Official public name. |
| `phone_number` | string | international format | E.g. `"+49 351 8629318"`, `"+1 541-754-3010"`. |
| `country` | string | ISO 3166-1 alpha-2 | See [supported countries](#supported-countries-country). |
| `region` | string | required for CA, AU, BR, IN, US | Highest administrative subdivision (state/province/oblast/prefecture). For Spain, use the province (e.g. `"Barcelona"`) rather than the autonomous community. |
| `city` | string | max 64 chars | City or locality name. |
| `zip` | string | required for most countries — see [zip-required list](#supported-countries-zip-required) | Postal or ZIP code. |
| `address_line_1` | string | max 190 chars | Street address with house number and street name. |
| `address_line_2` | string | max 64 chars | Suite, floor, building. |
| `website_url` | string | max 255 chars, must start with `http://` or `https://` | Prefer a location-specific URL over the generic brand site. |
| `description` | string | 10–750 chars | Detailed business description. |
| `business_hours` | object | each day max 2 non-overlapping ranges | See [`business_hours` schema](#business_hours). |
| `special_hours` | array[object] | max 30 entries; requires `business_hours` set | Overrides regular hours. See [`special_hours` schema](#special_hours). |
| `service_area_places` | array[object] | required if `suppress_address=true` | See [`service_area_places` schema](#service_area_places). |
| `category_ids` | array[string] | max 10 | Category IDs from [Get Categories](local_listing_categories.md). |
| `suppress_address` | boolean | — | Hide the physical address from public listings. Requires `service_area_places` to be set. |
| `coordinates` | object | — | See [`coordinates` schema](#coordinates). |
| `featured_message` | string | max 50 chars | Promotional message on the business profile. |
| `featured_message_url` | string | max 255 chars | Call-to-action URL for the featured message. |
| `youtube_video` | string | max 150 chars | YouTube URL. |
| `instagram_username` | string | max 30 chars | Handle, e.g. `semrush`. |
| `twitter_username` | string | max 15 chars | Handle, e.g. `semrush`. |
| `reopen_date` | string | `YYYY-MM-DD`, future date | Only applicable when the location is temporarily closed. |
| `location_status` | string | response only | `COMPLETED`, `PROCESSING`, or `FAILED`. |
| `submit_date` | string | response only, `YYYY-MM-DD[Thh:mm:ss.sss]` | First-submission timestamp. |
| `errors` | array[object] | response only | Asynchronous processing errors and system-level validation failures. |

### `business_hours`

Standard weekly operating hours. Each weekday key holds an array of up to two non-overlapping `{from, to}` ranges (`HH:mm` 24-hour time). An empty array means closed that day.

```json
{
  "monday_hours":    [{ "from": "08:00", "to": "12:00" }, { "from": "14:00", "to": "18:00" }],
  "tuesday_hours":   [{ "from": "08:00", "to": "12:00" }, { "from": "14:00", "to": "18:00" }],
  "wednesday_hours": [{ "from": "08:00", "to": "12:00" }, { "from": "14:00", "to": "18:00" }],
  "thursday_hours":  [{ "from": "08:00", "to": "12:00" }, { "from": "14:00", "to": "18:00" }],
  "friday_hours":    [{ "from": "08:00", "to": "12:00" }, { "from": "14:00", "to": "18:00" }],
  "saturday_hours":  [{ "from": "08:00", "to": "14:00" }],
  "sunday_hours":    []
}
```

### `special_hours`

Exceptions to regular hours (holidays, temporary closures). Max 30 entries. Each entry:

| Field | Type | Description |
|---|---|---|
| `type` | string | `CLOSED`, `OPENED_ALL_DAY`, or `RANGE`. |
| `day` | string | `YYYY-MM-DD`. |
| `times` | array[object] | `{from, to}` ranges. Required for `RANGE`; must be empty for `CLOSED` and `OPENED_ALL_DAY`. |

```json
[
  { "type": "CLOSED",         "day": "2026-05-01", "times": [] },
  { "type": "OPENED_ALL_DAY", "day": "2026-12-24", "times": [] },
  { "type": "RANGE",          "day": "2026-03-11", "times": [{ "from": "14:00", "to": "18:00" }] }
]
```

### `service_area_places`

Areas the business serves at the customer's location.

| Field | Type | Description |
|---|---|---|
| `name` | string | Display name of the place. |
| `place_id` | string | Provider place identifier. |

```json
[
  { "name": "Delta, UT, USA", "place_id": "ChIJQRRb_PG0TIcRwoI8h4xTvTM" }
]
```

### `coordinates`

| Field | Type | Description |
|---|---|---|
| `latitude` | float | Decimal latitude. |
| `longitude` | float | Decimal longitude. |

## Supported Countries (`country`)

The list of supported countries will grow over time.

`US`, `AU`, `FR`, `DE`, `GB`, `CA`, `IN`, `ES`, `IT`, `NL`, `BR`, `AT`, `BE`, `DK`, `FI`, `NO`, `PL`, `SE`, `CH`, `JP`, `MX`, `IL`, `NZ`, `SG`, `ZA`, `TR`, `AE`, `HK`, `ID`, `VN`, `PK`, `CO`, `IE`, `BD`, `MY`, `SA`, `RO`, `CL`, `PH`, `PT`, `NG`, `GR`, `TH`, `AR`, `PE`, `KE`, `HU`, `CZ`, `RS`, `NP`, `LT`, `UA`, `BG`, `EC`, `CY`, `HR`, `EE`, `LV`, `IS`, `SK`, `SI`, `AM`, `AD`, `PY`, `GY`, `EG`, `MV`, `UY`, `SR`, `KH`, `BO`, `LA`, `MT`, `PA`, `PR`, `TN`, `DO`, `MN`, `GU`, `VE`, `ME`, `MP`

## Supported Countries — `zip` Required

The same list as above **except** `AE`, `HK`, `GY`, `SR`, and `BO` — those five accept the country without requiring `zip`.

`US`, `AU`, `FR`, `DE`, `GB`, `CA`, `IN`, `ES`, `IT`, `NL`, `BR`, `AT`, `BE`, `DK`, `FI`, `NO`, `PL`, `SE`, `CH`, `JP`, `MX`, `IL`, `NZ`, `SG`, `ZA`, `TR`, `ID`, `VN`, `PK`, `CO`, `IE`, `BD`, `MY`, `SA`, `RO`, `CL`, `PH`, `PT`, `NG`, `GR`, `TH`, `AR`, `PE`, `KE`, `HU`, `CZ`, `RS`, `NP`, `LT`, `UA`, `BG`, `EC`, `CY`, `HR`, `EE`, `LV`, `IS`, `SK`, `SI`, `AM`, `AD`, `PY`, `EG`, `MV`, `UY`, `KH`, `LA`, `MT`, `PA`, `PR`, `TN`, `DO`, `MN`, `GU`, `VE`, `ME`, `MP`
