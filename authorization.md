# Authorization

Semrush API supports two authorization methods depending on which API you use.

## Methods Overview

| Method | Used For |
|--------|----------|
| API key | SEO API, Projects API (API key), Trends API, Listing Management API |
| OAuth 2.0 | Projects API (OAuth 2.0), Map Rank Tracker API, deprecated Listing Management API |

---

## API Key

Include your API key in every request as the `key` query parameter:

```
https://api.semrush.com/?key=<YOUR_API_KEY>&type=...
```

> Your API key gives access to your API units balance — do not share it publicly.

**Exception:** The Listing Management API passes the API key in the request header instead of as a query parameter:

```
Authorization: Apikey <YOUR_API_KEY>
```

---

## OAuth 2.0

The Projects (OAuth 2.0), Map Rank Tracker API, and deprecated Listing Management API use OAuth 2.0. Pass your access token in the HTTP request header:

```
Authorization: Bearer <TOKEN>
```

Two grant flows are supported:

- **Device Authorization Grant flow** (RFC 8628) — recommended
- **Semrush Auth flow**

---

### Device Authorization Grant Flow (Recommended)

This flow lets you sign in with your own Semrush account so your app can access Semrush API data on behalf of your end-users — without requiring those end-users to have Semrush accounts. No need to contact Semrush support to get credentials.

#### Step 1: Request Device Authorization

```
POST https://oauth.semrush.com/dag/device/code
```

Include an optional `scope=<scope>` parameter if the API requires scopes.

**Response fields:**

| Field | Description |
|-------|-------------|
| `device_code` | Used by your app to poll the token endpoint |
| `user_code` | Short code shown to you for sign-in |
| `verification_uri` | Semrush sign-in page to approve API access |
| `expires_in` | Seconds until device/user codes expire (not the access token lifetime) |
| `interval` | Recommended polling interval in seconds |

**Response example:**

```json
{
  "device_code": "XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
  "user_code": "YYYYYYYYYYY",
  "verification_uri": "https://oauth.semrush.com/dag/auth/verify_code?code=ZZZZZZZZZZZ",
  "expires_in": 300,
  "interval": 5
}
```

#### Step 2: Authenticate with Your Semrush Account

This step is performed by you (the developer), not your end-users.

1. Open the `verification_uri` URL in a browser.
2. Sign in with your Semrush account credentials.
3. Approve the API access request for your application.
4. Semrush authorizes your application and associates the approval with your `device_code`.

#### Step 3: Request Device Access Token

While you complete Step 2, your application polls the token endpoint at the recommended interval until authorization completes, the `device_code` expires, or an error occurs.

```
POST https://oauth.semrush.com/dag/device/token
```

**Required parameters:**

| Parameter | Value |
|-----------|-------|
| `grant_type` | `urn:ietf:params:oauth:grant-type:device_code` |
| `device_code` | Device verification code from Step 1 |

**Request example:**

```shell
curl https://oauth.semrush.com/dag/device/token \
  -d device_code=7ee7a929306d4075b9c4020e584fe4508862f26605e37c131eb6efe2f83b6dd0 \
  -d grant_type=urn:ietf:params:oauth:grant-type:device_code
```

**Success response:**

```json
{
  "access_token": "e3wLk3PtqyVPHM7Ele61OhuZFWtKCFK4O1HQslzh",
  "token_type": "Bearer",
  "expires_in": 604800,
  "refresh_token": "YWza6vpqkW628wtMldRsQNalEu9k33Vg75PQiXGi"
}
```

**Token handling:**

| Field | Notes |
|-------|-------|
| `access_token` | Use to call the Semrush API; expires in 7 days |
| `refresh_token` | Use to get new access tokens; valid for 30 days, refreshed alongside the bearer token |

Store the `refresh_token` securely. Refresh the access token before it expires.

#### Error Response

If authorization fails or is incomplete, the token endpoint returns an error per [RFC 6749 §5.2](https://datatracker.ietf.org/doc/html/rfc6749/#section-5.2):

```json
{
  "error": "<code>",
  "error_description": "<optional human-readable detail>"
}
```

---

### Semrush Auth Flow

#### Step 1: Get Code

1. Contact [Semrush Tech Support](https://www.semrush.com/kb/support/) to obtain your `client_id` and `client_secret`.
2. Open the following URL in a browser (replace `YOUR_CLIENT_ID`):
   ```
   https://oauth.semrush.com/oauth2/authorize?client_id=YOUR_CLIENT_ID&redirect_uri=%2Foauth2%2Fsuccess&response_type=code&scope=user.id
   ```
3. Log in to Semrush and click **Approve**. You'll be redirected to a URL like:
   ```
   https://oauth.semrush.com/oauth2/success?code=UTyWR6YQAPUbtLIX9jWM4OifmK1ODVWDOVUt8hlk
   ```
4. Copy the `code` parameter value from the URL.

#### Step 2: Get Access Token

Make a POST request with `Content-Type: application/x-www-form-urlencoded` (not JSON):

```shell
curl -L 'https://oauth.semrush.com/oauth2/access_token' \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  -d 'client_id=YOUR_CLIENT_ID' \
  -d 'client_secret=YOUR_CLIENT_SECRET' \
  -d 'grant_type=authorization_code' \
  -d 'code=YOUR_CODE' \
  -d 'redirect_uri=%2Foauth2%2Fsuccess'
```

**Response:**

```json
{
  "access_token": "wz1q0IpUBLLX7fqBKJI4pUoKBLZghAKp1VmBuJy5",
  "token_type": "Bearer",
  "expires_in": 604800,
  "refresh_token": "KTL5iInbFLIhm428FIKtHXO1ZX7ZUKNJTBoD9jk3"
}
```

#### Refreshing the Access Token

When the `access_token` expires, use the `refresh_token` to get a new one:

```shell
curl -X POST \
  -d "client_id=YOUR_CLIENT_ID&client_secret=YOUR_CLIENT_SECRET&grant_type=refresh_token&refresh_token=KTL5iInbFLIhm428FIKtHXO1ZX7ZUKNJTBoD9jk3" \
  https://oauth.semrush.com/oauth2/access_token
```

**Response:**

```json
{
  "access_token": "u8pPo6fo2NV70QCy7USWd3iT34CenBiT8RSuEEGn",
  "token_type": "Bearer",
  "expires_in": 604800,
  "refresh_token": "s99qrRuqbUdFRnum3R1HC9dTEJMOMs0IU1hJSi7W"
}
```
