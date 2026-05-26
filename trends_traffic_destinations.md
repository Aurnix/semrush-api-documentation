# Trends API — Traffic Destinations

**Cost:** 1 API unit per request  
**Billing note:** Units are charged even if the response is empty.

Returns a list of websites users visit after leaving a target domain. Useful for understanding audience journeys and downstream behavior.

---

## Endpoint

```
GET https://api.semrush.com/analytics/ta/api/v3/destinations
```

---

## Request Parameters

| Parameter | Required | Description |
|-----------|----------|-------------|
| `key` | Yes | Your API key (from Subscription info → API Units) |
| `target` | Yes | Root domain, subdomain, or subfolder |
| `display_date` | No | Month in `YYYY-MM-01` format. Defaults to previous month. Min: `2017-01-01`. Max: start of previous month. |
| `device_type` | No | `desktop` or `mobile`. Defaults to all devices. |
| `display_limit` | No | Results per request. Default: `1000`. Max: `5000`. |
| `display_offset` | No | Results to skip for pagination. Default: `0`. No maximum. |
| `country` | No | ISO 3166-1 Alpha-2 country code. Defaults to global data. |
| `sort_order` | No | Sort field + direction. Append `_desc` (default) or `_asc`. Options: `traffic`, `traffic_diff`, `traffic_share`. |
| `export_columns` | No | Comma-separated columns to return. Defaults to all columns. |

---

## Export Columns

| Column | Description |
|--------|-------------|
| `target` | The analyzed domain/subdomain/subfolder |
| `to_target` | The destination domain users visited after leaving `target` |
| `display_date` | Month of the data |
| `country` | Country filter used |
| `device_type` | Device type filter used |
| `traffic` | Estimated visits to the destination from `target` |
| `traffic_share` | Share of total traffic going to this destination (decimal) |
| `prev_traffic` | Traffic to this destination in the prior period |
| `categories` | Industry categories of the destination domain |

---

## Request Example

```
https://api.semrush.com/analytics/ta/api/v3/destinations?target=mail.ru&device_type=desktop&display_limit=5&display_offset=0&country=us&export_columns=target,display_date,country,device_type,to_target,traffic_share,traffic&display_date=2020-06-01&key=YOUR_API_KEY
```

## Response Example (CSV)

```
target;display_date;country;device_type;to_target;traffic_share;traffic
mail.ru;2020-06-01;US;desktop;ok.ru;0.14817627;237336
mail.ru;2020-06-01;US;desktop;turkishairlines.com;0.07261596;116310
mail.ru;2020-06-01;US;desktop;airastana.com;0.05397156;86447
mail.ru;2020-06-01;US;desktop;vazhno.ru;0.02943909;47153
mail.ru;2020-06-01;US;desktop;belavia.by;0.0206073;33007
```
