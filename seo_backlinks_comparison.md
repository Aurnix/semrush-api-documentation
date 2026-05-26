# SEO API — Batch Comparison

**Price:** 40 API units per line

Compares backlink profiles across multiple domains, subdomains, or URLs simultaneously.

## Endpoint

```
GET https://api.semrush.com/analytics/v1/
```

## Parameters

| Parameter | Required | Description |
|---|---|---|
| `type` | Yes | Report type. Value: `backlinks_comparison` |
| `key` | Yes | API key from Subscription info > API units. |
| `targets[]` | Yes | Array of root domains, subdomains, or URLs to compare. Repeat for each target: `targets[]=example.com&targets[]=competitor.com`. Max 200 targets. |
| `target_types[]` | Yes | Array of target types corresponding to each `targets[]` entry. Values: `root_domain`, `domain` (use for subdomains), `url`. Repeat in the same order as `targets[]`. |
| `export_columns` | Yes | Comma-separated columns to return. Defaults to all columns. Values: `target`, `target_type`, `ascore`, `backlinks_num`, `domains_num`, `ips_num`, `follows_num`, `nofollows_num`, `texts_num`, `images_num`, `forms_num`, `frames_num` |

## Export Columns

| Column | Description |
|---|---|
| `target` | The queried root domain, subdomain, or URL. |
| `target_type` | Type of the queried target: `root_domain`, `domain`, or `url`. |
| `ascore` | Authority Score — overall quality metric based on backlinks, referring domains, and organic traffic. |
| `backlinks_num` | Total backlinks to the target. |
| `domains_num` | Total unique referring domains. |
| `ips_num` | Unique IP addresses hosting referring domains. |
| `follows_num` | Number of follow backlinks. |
| `nofollows_num` | Number of nofollow backlinks. |
| `texts_num` | Number of text backlinks. |
| `images_num` | Number of image backlinks. |
| `forms_num` | Number of backlinks from forms. |
| `frames_num` | Number of backlinks from `<iframe>` elements. |

## Example Request

```
https://api.semrush.com/analytics/v1/?key=YOUR_API_KEY&type=backlinks_comparison&targets[]=ebay.com&targets[]=amazon.com&target_types[]=root_domain&target_types[]=root_domain&export_columns=target,target_type,ascore,backlinks_num,domains_num,ips_num,follows_num,nofollows_num,texts_num,images_num,forms_num,frames_num
```

## Example Response

```
target;target_type;ascore;backlinks_num;domains_num;ips_num;follows_num;nofollows_num;texts_num;images_num;forms_num;frames_num
ebay.com;root_domain;94;15248332274;461273;321889;6863043986;8385235217;11753970129;3487503037;6183483;675625
amazon.com;root_domain;94;6258027263;2679680;1012020;3901022285;2355705949;4522715595;1637657601;14954399;82699668
```
