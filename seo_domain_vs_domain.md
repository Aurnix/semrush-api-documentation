# SEO API — Domain vs. Domain

**Price:** 80 API units per line
**Price (historical data):** 400 API units per line

Compares up to five domains by common keywords, unique keywords, all keywords, or search terms that are unique to the first domain.

## Endpoint

```
GET https://api.semrush.com/
```

## Parameters

| Parameter | Required | Description |
|---|---|---|
| `type` | Yes | Report type. Value: `domain_domains` |
| `key` | Yes | API key from Subscription info > API units. |
| `domains` | Yes | URL-encoded string of domains separated by `\|`, in the format `<sign>\|<type>\|<domain>` per entry. See **Domains parameter format** below. |
| `database` | Yes | Regional database. See [Databases](seo_api_overview.md#databases). |
| `display_limit` | No | Number of results to return. Default and value of `0`: 10,000. Max value: 4,000,000. Max returned per call: 100,000 — use `display_offset` for more. |
| `display_offset` | No | Skip N results before returning. If used, increase `display_limit` by the offset value. `display_limit` must not exceed 4,000,000. |
| `export_escape` | No | If `1`, columns are wrapped in double quotes. |
| `export_decode` | No | If `0`, response is sent URL-encoded. If `1`, response is not encoded. |
| `display_date` | No | Date for the report. Format: `YYYYMM15`. |
| `export_columns` | No | Comma-separated columns. Default: `Ph,P0,P1,P2,P3,P4,Nr,Cp,Nq,Kd,Co,Td`. Available: `Ph,P0,P1,P2,P3,P4,Nr,Cp,Nq,Kd,Co,Td`. See [Columns](seo_api_overview.md#export-columns). |
| `display_sort` | No | Sort column and direction. Values: `p0_asc`, `p0_desc`, `p1_asc`, `p1_desc`, `p2_asc`, `p2_desc`, `p3_asc`, `p3_desc`, `p4_asc`, `p4_desc`, `nq_asc`, `nq_desc`, `co_asc`, `co_desc`, `cp_asc`, `cp_desc`, `nr_asc`, `nr_desc`. |
| `display_filter` | No | Filters. Fields: `Ph,P0,P1,P2,P3,P4,Nq,Cp,Co,Nr,Kd`. See [Filters](seo_api_overview.md#filters). |

## Domains parameter format

Each entry is `<sign>|<type>|<domain>`:

- `<sign>`: `+`, `-`, `*`, or `/`
- `<type>`: `or` for organic keywords, `ad` for paid keywords
- `<domain>`: the domain name

Entries are joined with `|` and the whole string must be URL-encoded.

**Common combinations:**

| Goal | Pattern |
|---|---|
| Shared keywords | `*\|or\|<your>\|*\|or\|<d2>\|*\|or\|<d3>` |
| All keywords | `*\|or\|<your>\|+\|or\|<d2>\|+\|or\|<d3>` |
| Unique to your domain | `*\|or\|<your>\|-\|or\|<d2>\|-\|or\|<d3>` |
| Untapped for your domain | `*\|or\|<d2>\|+\|or\|<d3>\|-\|or\|<your>` |
| Missing for your domain | `*\|or\|<d2>\|*\|or\|<d3>\|-\|or\|<your>` |
| Keywords in only one domain (API only) | `*\|or\|<your>\|/\|or\|<d2>\|/\|or\|<d3>` |

## Example Request

```
https://api.semrush.com/?type=domain_domains&key=YOUR_API_KEY&database=us&display_limit=10&domains=%2A%7Cor%7Cnike.com%7C%2A%7Cor%7Cadidas.com%7C%2A%7Cor%7Creebok.com&export_columns=Ph,P0,P1,P2,Co,Nq,Cp
```

## Example Response

```
Keyword;nike.com;adidas.com;reebok.com;Competition;Search Volume;CPC
shoes;69;33;81;1.00;1500000;0.91
basketball shoes;1;11;14;1.00;368000;0.39
man;30;41;68;0.00;301000;0.22
running;26;31;33;0.01;301000;1.26
shoes for men;44;25;49;1.00;301000;0.71
```
