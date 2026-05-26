# SEO API — Backlinks Overview

**Price:** 40 API units per request

Returns a summary of backlinks including type, referring domains, and IP addresses for a domain, root domain, or URL.

## Endpoint

```
GET https://api.semrush.com/analytics/v1/
```

## Parameters

| Parameter | Required | Description |
|---|---|---|
| `type` | Yes | Report type. Value: `backlinks_overview` |
| `key` | Yes | API key from Subscription info > API units. |
| `target` | Yes | Root domain, subdomain, or URL to investigate. Example: `example.com`, `www.example.com`, or `http://www.example.com` |
| `target_type` | Yes | Type of target. Values: `root_domain`, `domain` (use for subdomains), `url` |
| `export_columns` | Yes | Comma-separated list of columns to return. Defaults to: `total,domains_num,ips_num,follows_num,nofollows_num,score,trust_score,urls_num,ipclassc_num,texts_num,forms_num,frames_num,images_num` |

## Export Columns

| Column | Description |
|---|---|
| `ascore` | Authority Score — overall domain/URL quality metric based on backlinks, referring domains, organic traffic. |
| `total` | Total backlinks to the analyzed domain/URL. |
| `domains_num` | Total unique referring domains. |
| `urls_num` | Number of referring URLs. |
| `ips_num` | Unique IP addresses hosting referring domains. |
| `ipclassc_num` | Unique Class C IP addresses of referring domains. |
| `follows_num` | Number of follow backlinks. |
| `nofollows_num` | Number of nofollow backlinks. |
| `sponsored_num` | Number of sponsored backlinks. |
| `ugc_num` | Number of User Generated Content backlinks. |
| `texts_num` | Number of text backlinks. |
| `images_num` | Number of image backlinks. |
| `forms_num` | Number of backlinks from forms. |
| `frames_num` | Number of backlinks from `<iframe>` elements. |

## Example Request

```
https://api.semrush.com/analytics/v1/?key=YOUR_API_KEY&type=backlinks_overview&target=searchenginejournal.com&target_type=root_domain&export_columns=ascore,total,domains_num,urls_num,ips_num,ipclassc_num,follows_num,nofollows_num,sponsored_num,ugc_num,texts_num,images_num,forms_num,frames_num
```

## Example Response

Response uses semicolons as delimiters.

```
ascore;total;domains_num;urls_num;ips_num;ipclassc_num;follows_num;nofollows_num;sponsored_num;ugc_num;texts_num;images_num;forms_num;frames_num
74;22063983;49145;13059030;47793;22956;20457307;1606307;258;1475;21784602;278624;437;320
```
