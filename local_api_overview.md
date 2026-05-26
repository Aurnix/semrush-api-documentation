# Local API — Overview

The Local API is split into two product APIs:

- **Listing Management API** — push location data from your tools into Semrush Listing Management and distribute it across directories in bulk.
- **Map Rank Tracker API** — access campaign, keyword, competitor, heatmap, and ranking data for Map Rank Tracker.

The previous Listing Management API is deprecated and will be removed; new integrations should use the current Listing Management API.

## Access

| API | Plan / requirement |
|---|---|
| **Listing Management API** | Semrush Local Pro and Business plans. No API units required. The Create Location endpoint additionally requires an available Local Pro limit. |
| **Map Rank Tracker API** | All Semrush users. No API units required. |

## Authorization

| API | Method | Header |
|---|---|---|
| **Listing Management API** (current) | API key | `Authorization: Apikey <YOUR_API_KEY>` |
| **Listing Management API** (deprecated) | OAuth 2.0 | `Authorization: Bearer <TOKEN>` |
| **Map Rank Tracker API** | OAuth 2.0 | `Authorization: Bearer <TOKEN>` |

Get your API key in Subscription info → API Units. For OAuth 2.0, see [Authorization](authorization.md).

## API Response Format

Every response body is a JSON object containing a top-level `meta` object plus either a `data` object or an `error` object — never both.

### `meta`

| Key | Type | Required | Description |
|---|---|---|---|
| `success` | boolean | Yes | Request status. |
| `status_code` | integer | Yes | HTTP status code. |
| `request_id` | string | No | Unique ID of the request. |

### Success Response Example

```json
{
  "meta": {
    "success": true,
    "status_code": 200,
    "request_id": "IAD-as5656as776"
  },
  "data": [
    { "id": "590e", "kind": "dog", "name": "Penny" },
    { "id": "a45f", "kind": "cat", "name": "Tommy" }
  ]
}
```

### `error`

| Key | Type | Required | Description |
|---|---|---|---|
| `code` | integer | Yes | Error code. |
| `message` | string | Yes | Error message. |
| `details` | array | No | Error details. |

### Error Response Example

```json
{
  "meta": {
    "success": false,
    "status_code": 400,
    "request_id": "IAD-123ade456"
  },
  "error": {
    "code": 120200,
    "message": "This was bad",
    "details": [
      {
        "message": {
          "field_violations": [
            {
              "field": "user_id",
              "description": "user_id must be a number"
            }
          ]
        }
      }
    ]
  }
}
```

## Status Codes

The Local API returns a standard HTTP status code with every response.

| Code | Description | Recommended action |
|---|---|---|
| `2XX OK` | Request processed successfully. | No action required. |
| `400 Bad Request` | Request was incorrect or incomplete. | Check the request body for typos and missing parameters. Inspect `error.details` if present. |
| `401 Unauthorized` | Authentication credentials were incorrect or missing. | Confirm the access token is still valid. |
| `403 Forbidden` | Restriction or permission issue. | Contact the Semrush Support Team. |
| `404 Not Found` | Target resource was incorrect or has been moved. | Confirm the resource exists and is specified correctly. |
| `409 Conflict` | Conflict with the current state of the resource. | Retry later or check resource state (e.g. confirm a project doesn't already exist). |
| `429 Too Many Requests` | Too many requests from the user. | Retry later. |
| `499 Client Closed Request` | The user disconnected before receiving a response. | Check your network connection and retry. |
| `550 Internal Server Error` | Server-side error. | Retry later. |
| `551 Not Implemented` | Request method not supported. | Check the API reference for available methods. |
| `553 Service Unavailable` | Maintenance or overload. | Retry later. |
| `554 Gateway Timeout` | Gateway or proxy timeout. | Retry later. |

## Error Responses

### Listing Management API (current)

Errors follow the [standard response format](#api-response-format) with an `error` object in place of `data`.

**Not Found**

```json
{
  "meta": {
    "success": false,
    "status_code": 404,
    "request_id": "7595d5c768a976ab0b120749173cf803"
  },
  "error": {
    "code": 404,
    "message": "Not Found"
  }
}
```

**Invalid Request**

```json
{
  "meta": {
    "success": false,
    "status_code": 400,
    "request_id": "6995af5ce87c1831c78c22a5456f646f"
  },
  "error": {
    "code": 400,
    "message": "Invalid request.",
    "details": [
      {
        "message": "Phone number is not specified.",
        "error_status": "PHONE_NOT_SPECIFIED"
      }
    ]
  }
}
```

### Listing Management API (deprecated)

Returns the standard status codes — **except** the `UpdateLocations` method, which always returns HTTP `200`. Per-location errors are described inside the response body so successfully updated locations are still committed. To avoid this behavior, update locations one at a time with `UpdateLocation`.

Deprecated error responses do **not** follow the standard response format.

**Duplicated location IDs**

```json
{
  "error": {
    "code": "BAD_REQUEST",
    "message": "Invalid state of resource.",
    "details": [
      {
        "code": "LOCATIONS_ARE_NOT_UNIQUE",
        "message": "The locations are not unique. There are several locations with this ID: 6fb03fd6c3a943a489df2c7060218911."
      }
    ]
  },
  "requestId": "api-flb-ec33fa653e6734980500d561b6aa3d32"
}
```

**Location not found**

```json
{
  "error": {
    "code": "RESOURCE_NOT_FOUND",
    "message": "Resource not found.",
    "details": [
      {
        "code": "LOCATION_NOT_FOUND",
        "message": "Location is not found."
      }
    ]
  },
  "requestId": "api-flb-fb27c729b51e658d4a4984716df00a77"
}
```

**Incorrect data format**

```json
{
  "error": {
    "code": "VALIDATION_ERROR",
    "message": "Invalid data provided.",
    "details": [
      {
        "code": "TIMES_NOT_ALLOWED",
        "message": "Operation hours shouldn't be set.",
        "field": "holidayHours.times",
        "index": "0"
      },
      {
        "code": "TIMES_TOO_MANY_RANGES",
        "message": "Only three time ranges can be set.",
        "field": "holidayHours.times",
        "index": "1"
      }
    ]
  },
  "requestId": "api-flb-fb27c729b51e658d4a4984716df00a77"
}
```

### Map Rank Tracker API

Follows the [standard response format](#api-response-format).
