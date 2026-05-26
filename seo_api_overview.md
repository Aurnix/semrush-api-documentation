# SEO API — Overview

## About

The SEO API covers the following product groups:

- Domain Analytics
- Organic Research
- Advertising Research
- Keyword Gap Analysis
- Keyword Analytics
- Backlink Analytics

## Authentication

Authentication is via API key assigned at subscription. Find it at **Subscription info > API units**. Never share your key publicly — replace it with a placeholder like `key=<key>` in examples.

## Response Format

All SEO API report endpoints return **CSV format** responses.

---

## Export Columns

Use the `export_columns` parameter to specify which columns to include. The table below maps request parameter codes to CSV response column names.

| Request Param | Response Column | Description | Used In |
|---|---|---|---|
| `Ab` | `Adwords Block` | SERP placement of ad (top, side, bottom). | Domain Paid Search Keywords, Subdomain Paid Search Keywords, Subfolder Paid Search Keywords |
| `Ac` | `Adwords Cost` | Estimated monthly budget spent buying keywords in Google Ads. | Competitors in Paid Search, PLA Competitors, Keyword Ads History, Domain Overview (all/one/history), Winners and Losers, Semrush Rank, Subdomain Overview (all/one/history), Subfolder Overview (all/one/history), URL Overview (all/one/history) |
| `Ad` | `Adwords Keywords` | Keywords a website is buying in Google Ads. | Competitors in Organic Search, Competitors in Paid Search, PLA Competitors, Keyword Ads History, Domain Overview (all/one/history), Winners and Losers, Semrush Rank, Subdomain Overview (all/one/history), Subfolder Overview (all/one/history), URL Overview (all/one/history) |
| `Am` | `Adwords Keywords Difference` | Changes in number of paid keywords. | Winners and Losers |
| `At` | `Adwords Traffic` | Traffic from paid search results. | Competitors in Paid Search, PLA Competitors, Keyword Ads History, Domain Overview (all/one/history), Winners and Losers, Semrush Rank, Subdomain Overview (all/one/history), Subfolder Overview (all/one/history), URL Overview (all/one/history) |
| `Bm` | `Adwords Traffic Difference` | Changes in paid traffic. | Winners and Losers |
| `Cm` | `Adwords Cost Difference` | Changes in paid traffic price. | Winners and Losers |
| `Co` | `Competition` | Competitive density of advertisers for a term. Values: `0–1` (1 = highest). | Domain Organic/Paid Search Keywords, Domain vs. Domain, Keyword Overview (all/one), Batch Keyword Overview, Related Keywords, Broad Match Keyword, Phrase Questions, Subdomain/Subfolder Organic/Paid Search Keywords, URL organic/paid search keywords |
| `Cp` | `CPC` | Average USD cost per click in Google Ads. | Domain Organic/Paid Search Keywords, Domain Ad History, Domain vs. Domain, Keyword Overview (all/one), Batch Keyword Overview, Related Keywords, Broad Match Keyword, Phrase Questions, Subdomain/Subfolder Organic/Paid Search Keywords, URL organic/paid search keywords |
| `Cr` | `Competitor Relevance` | Competition level based on shared vs. total keyword counts. | Competitors in Organic Search, Competitors in Paid Search, PLA Competitors |
| `Cv` | `Coverage` | % of months in last 12 that ads appeared for keyword. Values: `0–100`. | Domain Ad History |
| `Db` | `Database` | Regional database (US, UK, Italy, etc.). | Keyword Overview (all databases), Domain/Subdomain/Subfolder/URL Overview (all databases) |
| `Dn` | `Domain` | Domain name. | Competitors in Organic/Paid Search, PLA Competitors, Organic/Paid Results, Keyword Ads History, Domain/Subdomain/Subfolder/URL Overview (all/one) |
| `Ds` | `Description` | Ad text. | Domain Paid Search Keywords, Ads Copies, Domain Ad History, Keyword Ads History, Subdomain/Subfolder Paid Search Keywords, URL paid search keywords |
| `Dt` | `Date` | Current date. | Domain Ad History, Keyword Overview (all databases), Keyword Ads History, Domain/Subdomain/Subfolder Overview (all/history), URL Overview (all/history) |
| `Fk` | `Keywords SERP Features` | All SERP features triggered by a keyword. | Domain Organic Search Keywords, Organic Results, Related Keywords, Broad Match Keyword, Subdomain/Subfolder Organic Search Keywords, URL organic search keywords |
| `Fp` | `SERP Features` | SERP features where the domain appears for a keyword. | Domain Organic Search Keywords, Organic Results, Subdomain/Subfolder Organic Search Keywords, URL organic search keywords |
| `Fl` ⚠️ | `SERP Features` | **Deprecated.** Use `Fk` or `Fp` instead. | Organic Results |
| `FKn` | SERP feature name | Count of SERP features triggered by keywords ranked for. Use `FK1,FK2..FKn` where n is the SERP feature code. | Domain/Subdomain/Subfolder/URL Overview (all/one/history) |
| `FPn` | SERP feature name | Count of SERP features the domain ranks in. Use `FP1,FP2..FPn` where n is the SERP feature code. | Domain/Subdomain/Subfolder/URL Overview (all/one/history) |
| `Ip` | `ip` | IP address. | Referring Domains, Referring IPs |
| `In` | `Intents` | Keyword intent. Values: `0` Commercial, `1` Informational, `2` Navigational, `3` Transactional. | Domain Organic Search Keywords, Keyword Overview (all/one), Batch Keyword Overview, Related Keywords, Broad Match Keyword, Phrase Questions, Subdomain/Subfolder Organic Search Keywords, URL organic search keywords |
| `Ipu` | `Intent Unknown Positions` | Total positions with unknown intent. | Domain Organic Pages, Domain/Subdomain/Subfolder Overview (one/history), Subdomain/Subfolder Organic Pages, URL Overview (one) |
| `Ip0` | `Intent Commercial Positions` | Total positions with Commercial intent. | Domain Organic Pages, Domain/Subdomain/Subfolder Overview (one/history), Subdomain/Subfolder Organic Pages, URL Overview (one) |
| `Ip1` | `Intent Informational Positions` | Total positions with Informational intent. | Same as `Ip0` |
| `Ip2` | `Intent Navigational Positions` | Total positions with Navigational intent. | Same as `Ip0` |
| `Ip3` | `Intent Transactional Positions` | Total positions with Transactional intent. | Same as `Ip0` |
| `Itu` | `Intent Unknown Traffic` | Total traffic with unknown intent. | Domain Organic Pages, Domain/Subdomain/Subfolder Overview (one/history), Subdomain/Subfolder Organic Pages, URL Overview (one) |
| `It0` | `Intent Commercial Traffic` | Total traffic with Commercial intent. | Same as `Itu` |
| `It1` | `Intent Informational Traffic` | Total traffic with Informational intent. | Same as `Itu` |
| `It2` | `Intent Navigational Traffic` | Total traffic with Navigational intent. | Same as `Itu` |
| `It3` | `Intent Transactional Traffic` | Total traffic with Transactional intent. | Same as `Itu` |
| `Icu` | `Intent Unknown Traffic Cost` | Total cost of traffic with unknown intent. | Domain/Subdomain/Subfolder/URL Overview (one/history) |
| `Ic0` | `Intent Commercial Traffic Cost` | Total cost of traffic with Commercial intent. | Same as `Icu` |
| `Ic1` | `Intent Informational Traffic Cost` | Total cost of traffic with Informational intent. | Same as `Icu` |
| `Ic2` | `Intent Navigational Traffic Cost` | Total cost of traffic with Navigational intent. | Same as `Icu` |
| `Ic3` | `Intent Transactional Traffic Cost` | Total cost of traffic with Transactional intent. | Same as `Icu` |
| `Kd` | `Keyword Difficulty Index` | Difficulty to rank for a keyword. Values: `0–100` (higher = harder). | Domain Organic Search Keywords, Domain vs. Domain, Keyword Overview (all/one), Batch Keyword Overview, Related Keywords, Broad Match Keyword, Phrase Questions, Keyword Difficulty, Subdomain/Subfolder Organic Search Keywords, URL organic search keywords |
| `Np` | `Common Keywords` | Keywords both domains rank for in Google top 100. | Competitors in Organic Search, Competitors in Paid Search, PLA Competitors |
| `Nq` | `Search Volume` | Average monthly searches over last 12 months. | Domain Organic/Paid Search Keywords, Domain Ad History, Domain vs. Domain, Domain PLA Search Keywords, Keyword Overview (all/one), Batch Keyword Overview, Related Keywords, Broad Match Keyword, Phrase Questions, Subdomain/Subfolder Organic/Paid Search Keywords, URL organic/paid search keywords |
| `Nr` | `Number of Results` | Total organic results for keyword at last data collection. | Domain Organic/Paid Search Keywords, Domain vs. Domain, Keyword Overview (all/one), Batch Keyword Overview, Related Keywords, Broad Match Keyword, Phrase Questions, Subdomain/Subfolder Organic/Paid Search Keywords, URL organic/paid search keywords |
| `Oc` | `Organic Cost` | Estimated price of organic keywords in Google Ads. | Competitors in Organic Search, Domain/Subdomain/Subfolder/URL Overview (all/one/history), Winners and Losers, Semrush Rank |
| `Oe` | `Organic Positions Improved` | Keywords domain still ranks for top 100 but moved up. | Domain Overview (one/history) |
| `Oi` | `Organic Positions Declined` | Keywords that decreased in ranking but remain top 100. | Domain Overview (one/history) |
| `Ol` | `Organic Positions Lost` | Keywords domain was ranking for top 100 but no longer. | Domain Overview (one/history) |
| `Om` | `Organic Keywords Difference` | Changes in number of organic keywords. | Winners and Losers |
| `On` | `Organic Positions New` | New top-100 organic keywords in chosen time period. | Domain Overview (one/history) |
| `Or` | `Organic Keywords` | Keywords bringing users via Google top 100 organic. | Competitors in Organic/Paid Search, PLA Competitors, Domain/Subdomain/Subfolder/URL Overview (all/one/history), Winners and Losers, Semrush Rank |
| `Ot` | `Organic Traffic` | Traffic via Google top 100 organic results. | Competitors in Organic Search, Domain/Subdomain/Subfolder/URL Overview (all/one/history), Winners and Losers, Semrush Rank |
| `P0` | `Domain` | Position of 1st queried domain for keyword. Values: `0–100` (0 = not ranked). | Domain vs. Domain |
| `P1` | `Domain` | Position of 2nd queried domain. | Domain vs. Domain |
| `P2` | `Domain` | Position of 3rd queried domain. | Domain vs. Domain |
| `P3` | `Domain` | Position of 4th queried domain. | Domain vs. Domain |
| `P4` | `Domain` | Position of 5th queried domain. | Domain vs. Domain |
| `Pc` | `Number of Keywords` | Number of keywords. | Ads Copies, PLA Copies, Domain Organic Pages, Domain Organic Subdomains, Subdomain/Subfolder Organic Pages |
| `Pd` | `Position Difference` | Difference between previous and current position for a keyword. | Domain/Subdomain/Subfolder Organic/Paid Search Keywords |
| `Ph` | `Keyword` | Keyword bringing users via Google top 100 organic. | Domain Organic/Paid Search Keywords, Ads Copies, Domain Ad History, Domain vs. Domain, Domain PLA Search Keywords, Keyword Overview (all/one), Batch Keyword Overview, Related Keywords, Broad Match Keyword, Phrase Questions, Keyword Difficulty, Subdomain/Subfolder Organic/Paid Search Keywords, URL organic/paid search keywords |
| `Po` | `Position` | Position for keyword in Google top 100. Values: `0–100` (0 = not ranked). | Domain Organic/Paid Search Keywords, Domain Ad History, Domain PLA Search Keywords, Organic Results, Keyword Ads History, Subdomain/Subfolder Organic/Paid Search Keywords, URL organic/paid search keywords |
| `Pp` | `Previous Position` | Previous position for keyword in Google top 100. Values: `0–100`. | Domain/Subdomain/Subfolder Organic/Paid Search Keywords, Domain PLA Search Keywords, URL organic search keywords |
| `Pr` | `Product Price` | Price of promoted product. | Domain PLA Search Keywords, PLA Copies |
| `Pt` | `Position type` | Regular organic position or specific SERP Feature type. | Domain Organic Search Keywords, Organic Results, Subdomain/Subfolder Organic Search Keywords, URL organic search keywords |
| `Rk` | `Rank` | Semrush popularity rating based on organic traffic from Google top 100. | Domain/URL Overview (all/one/history), Winners and Losers, Semrush Rank |
| `Rr` | `Related Relevance` | Relevance of result keyword to seed keyword. | Related Keywords |
| `Sc` | `SERP Features Traffic Cost` | Estimated PPC cost for keywords where domain ranks in SERP Features. | Competitors in Organic Search, Domain/Subdomain/Subfolder/URL Overview (all/one/history), Winners and Losers, Semrush Rank |
| `Scm` | `SERP Features Traffic Cost Difference` | Changes in organic traffic cost from SERP Feature positions. | Winners and Losers |
| `Sh` | `PLA keywords` | Number of keywords used for product listing ads. | PLA Competitors, Domain/Subdomain/Subfolder/URL Overview (all databases) |
| `Sn` | `Shop Name` | Shop name. | Domain PLA Search Keywords |
| `Sv` | `PLA uniques` | Number of unique product listing ads. | Domain/Subdomain/Subfolder/URL Overview (all databases) |
| `Sr` | `SERP Features Positions` | Number of keywords where domain ranks in SERP Features. | Competitors in Organic Search, Domain Organic Pages, Domain Organic Subdomains, Domain/Subdomain/Subfolder/URL Overview (all/one/history), Winners and Losers, Semrush Rank, Subdomain/Subfolder Organic Pages |
| `Srb` | `SERP Features Positions Branded` | Number of branded keywords where domain ranks in SERP Features. | Domain/Subdomain/Subfolder/URL Overview (all/one/history) |
| `Srl` | `SERP Features Positions Lost` | Keywords domain was ranking for in SERP Features but no longer. | Domain/Subdomain/Subfolder/URL Overview (all/one) |
| `Srm` | `SERP Features Positions Difference` | Changes in keywords with SERP Feature positions. | Winners and Losers |
| `Srn` | `SERP Features Positions New` | New SERP Feature keyword rankings in chosen time period. | Domain/Subdomain/Subfolder/URL Overview (all/one/history) |
| `St` | `SERP Features Traffic` | Estimated organic traffic from SERP Feature positions. | Competitors in Organic Search, Domain Organic Pages, Domain Organic Subdomains, Domain/Subdomain/Subfolder/URL Overview (all/one/history), Winners and Losers, Semrush Rank, Subdomain/Subfolder Organic Pages |
| `Stb` | `SERP Features Traffic Branded` | Estimated organic traffic from SERP Feature positions on branded keywords. | Domain/Subdomain/Subfolder/URL Overview (all/one/history) |
| `Stm` | `SERP Features Traffic Difference` | Changes in traffic from SERP Feature positions. | Winners and Losers |
| `Tc` | `Traffic Cost (%)` | % of domain's total traffic cost attributed to a keyword. | Domain/Subdomain/Subfolder Organic/Paid Search Keywords, URL organic/paid search keywords |
| `Tg` | `Traffic` | Estimated organic traffic for domain/keyword over period. | Domain/Subdomain/Subfolder Organic/Paid Search Keywords, Domain/Subdomain/Subfolder Organic Pages, Domain Organic Subdomains, URL organic/paid search keywords |
| `Td` | `Trends` | Searcher interest in keyword over last 12 months. | Domain/Subdomain/Subfolder Organic/Paid Search Keywords, Domain vs. Domain, Keyword Overview (one), Batch Keyword Overview, Related Keywords, Broad Match Keyword, Phrase Questions, URL organic/paid search keywords |
| `Tm` | `Organic Traffic Difference` | Changes in organic traffic. | Winners and Losers |
| `Tr` | `Traffic (%)` | Share of traffic driven by a keyword for specified period. | Domain/Subdomain/Subfolder Organic/Paid Search Keywords, Domain Ad History, Domain/Subdomain/Subfolder Organic Pages, Domain Organic Subdomains, URL organic/paid search keywords |
| `Ts` | `Timestamp` | UNIX timestamp. | Domain/Subdomain/Subfolder Organic/Paid Search Keywords, Ads Copies, Domain PLA Search Keywords, PLA Copies, URL organic/paid search keywords |
| `Tt` | `Title` | Ad title. | Domain Paid Search Keywords, Ads Copies, Domain Ad History, Domain PLA Search Keywords, PLA Copies, Keyword Ads History, Subdomain/Subfolder Paid Search Keywords, URL paid search keywords |
| `Um` | `Organic Cost Difference` | Changes in organic traffic cost. | Winners and Losers |
| `Un` | `Ad id` | Ad ID. | Domain Paid Search Keywords, Ads Copies, PLA Copies, Subdomain/Subfolder Paid Search Keywords |
| `Ur` | `Url` | URL of the target page. | Domain/Subdomain/Subfolder Organic/Paid Search Keywords, Ads Copies, Domain Ad History, Domain PLA Search Keywords, PLA Copies, Domain/Subdomain/Subfolder Organic Pages, Domain Organic Subdomains, Organic/Paid Results, Keyword Ads History |
| `Vu` | `Visible Url` | Visible URL (displayed in ad). | Domain Paid Search Keywords, Ads Copies, Domain Ad History, Paid Results, Keyword Ads History, Subdomain/Subfolder Paid Search Keywords |
| `Xn` | `X0,X1..X9,XA` | Organic Position Distribution by rank bucket. Use `X0,X1..X9,XA` where: `0`=1–3, `1`=4–10, `2`=11–20, `3`=21–30, `4`=31–40, `5`=41–50, `6`=51–60, `7`=61–70, `8`=71–80, `9`=81–90, `A`=91–100 | Domain/Subdomain/Subfolder/URL Overview (one/history) |

### Backlink Columns

| Request Param | Response Column | Description | Used In |
|---|---|---|---|
| `anchor` | `anchor` | Clickable backlink text. | Backlinks, Anchors |
| `ascore` | `ascore` | Authority Score (quality metric based on backlinks, referring domains, organic traffic). | Backlinks Overview, Competitors, Batch Comparison |
| `backlinks_lost_num` | `backlinks_lost_num` | Lost backlinks over a period. | Historical Data (Backlinks) |
| `backlinks_new_num` | `backlinks_new_num` | New backlinks acquired over a period. | Historical Data (Backlinks) |
| `backlinks_num` | `backlinks_num` | Number of backlinks to a domain. | Referring Domains, Referring IPs, TLD Distribution, Referring Domains by Country, Anchors, Indexed Pages, Competitors, Comparison by Referring Domains, Batch Comparison, Historical Data |
| `category_name` | `category_name` | Category name (1–3 levels separated by `/`). Example: `/Internet & Telecom/Web Services/Web Design & Development` | Categories Profile, Categories |
| `common_refdomains` | `common_refdomains` | Referring domains linking to both the analyzed and competing domain. | Competitors |
| `country` | `country` | Country of referring domains. | Referring Domains by Country |
| `date` | `date` | Unix timestamp of data collection date. | Historical Data (Backlinks) |
| `domain` | `domain` | Domain name. | Referring Domains, Comparison by Referring Domains |
| `domain_ascore` | `domain_ascore` | Domain Authority Score. | Referring Domains, Comparison by Referring Domains |
| `domain_score` | `domain_score` | Same as `domain_ascore`. | Referring Domains, Comparison by Referring Domains |
| `domain_trust_score` | `domain_trust_score` | Domain trustworthiness metric. | Referring Domains |
| `domains_lost_num` | `domains_lost_num` | Referring domains lost over a period. | Historical Data (Backlinks) |
| `domains_new_num` | `domains_new_num` | New referring domains over a period. | Historical Data (Backlinks) |
| `domains_num` | `domains_num` | Total domains linking to a given domain. | Backlinks Overview, Referring IPs, TLD Distribution, Referring Domains by Country, Anchors, Indexed Pages, Competitors, Batch Comparison, Historical Data |
| `external_num` | `external_num` | Source page links pointing to other websites. | Backlinks, Indexed Pages |
| `first_seen` | `first_seen` | Timestamp when Semrush first noticed the backlink. | Backlinks, Referring Domains, Referring IPs, Anchors |
| `follows_num` | `follows_num` | Number of follow backlinks. | Backlinks Overview, Batch Comparison |
| `form` | `form` | Whether link is from a form. Values: `true`, `false`. | Backlinks |
| `forms_num` | `forms_num` | Number of backlinks from forms. | Backlinks Overview, Batch Comparison |
| `frame` | `frame` | Whether link is from inside `<iframe>`. Values: `true`, `false`. | Backlinks |
| `frames_num` | `frames_num` | Number of backlinks from `<iframe>`. | Backlinks Overview, Batch Comparison |
| `image` | `image` | Whether link is from an image. Values: `true`, `false`. | Backlinks |
| `images_num` | `images_num` | Number of backlinks from images. | Backlinks Overview, Batch Comparison |
| `image_alt` | `image_alt` | Alt text of backlink image. | Backlinks |
| `image_url` | `image_url` | URL of the image backlink's location. | Backlinks |
| `internal_num` | `internal_num` | Source page links pointing to the same website. | Backlinks, Indexed Pages |
| `ip` | `ip` | IP address associated with a domain. | Referring Domains, Referring IPs |
| `ipclassc_num` | `ipclassc_num` | Unique Class C IP addresses of referring domains. | Backlinks Overview |
| `ips_num` | `ips_num` | Unique IP addresses hosting referring domains. | Backlinks Overview, Batch Comparison |
| `last_seen` | `last_seen` | Timestamp when Semrush last noticed the backlink. | Backlinks, Referring Domains, Referring IPs, Anchors, Indexed Pages |
| `lostlink` | `lostlink` | Whether the link is lost. Values: `true`, `false`. | Backlinks |
| `matches_num` | `matches_num` | Analyzed domains that have backlinks from the indicated domain. | Comparison by Referring Domains |
| `neighbour` | `neighbour` | Domain with similar backlink profile. | Competitors |
| `newlink` | `newlink` | Whether the link is new. Values: `true`, `false`. | Backlinks |
| `nofollow` | `nofollow` | Whether the link is nofollow. Values: `true`, `false`. | Backlinks |
| `nofollows_num` | `nofollows_num` | Number of nofollow backlinks. | Backlinks Overview, Batch Comparison |
| `page_ascore` | `page_ascore` | Page Authority Score (based on backlinks, referring domains, organic traffic). | Backlinks |
| `page_score` | `page_score` | Same as `page_ascore`. | Backlinks |
| `rating` | `rating` | Confidence that domain belongs to a category. Values: `0–1`. | Categories Profile, Categories |
| `redirect_url` | `redirect_url` | Last URL in a redirect chain. | Backlinks |
| `response_code` | `response_code` | Server response code. | Backlinks, Indexed Pages |
| `score` | `score` | Authority Score of queried domain on historical date. | Historical Data (Backlinks) |
| `similarity` | `similarity` | Similarity metric based on common referring domains. | Competitors |
| `sitewide` | `sitewide` | Whether link appears on multiple pages of a website. Values: `true`, `false`. | Backlinks |
| `source_title` | `source_title` | Title of the source page. | Backlinks, Indexed Pages |
| `source_size` | `source_size` | Size of source page in bytes. | Backlinks |
| `source_url` | `source_url` | URL of the source page. | Backlinks, Indexed Pages |
| `sponsored_num` | `sponsored_num` | Number of sponsored backlinks. | Backlinks Overview |
| `target` | `target` | Root domain, subdomain, or URL being investigated. | Batch Comparison |
| `target_title` | `target_title` | Title of the target page. | Backlinks |
| `target_type` | `target_type` | Type of requested target. Values: `root_domain`, `domain`, `url`. | Batch Comparison |
| `target_url` | `target_url` | URL of the target page. | Backlinks |
| `texts_num` | `texts_num` | Number of text backlinks. | Backlinks Overview, Batch Comparison |
| `total` | `total` | Total backlinks leading to analyzed domain/URL. | Backlinks Overview |
| `trust_score` | `trust_score` | Domain trustworthiness metric. | Backlinks Overview |
| `ugc_num` | `ugc_num` | Number of User Generated Content backlinks. | Backlinks Overview |
| `urls_num` | `urls_num` | Number of referring URLs. | Backlinks Overview |
| `zone` | `zone` | Domain TLD. | TLD Distribution |

### Tips

- Column names cannot be changed.
- Column order can be changed.
- Additional columns can be added.
- Semrush will notify users before removing old columns.

---

## Databases

Regional databases come in three types:
- **Desktop**: Two-letter code (e.g., `us`)
- **Mobile**: Two-letter code with `mobile-` prefix (e.g., `mobile-us`)
- **Extended**: Two-letter code with `-ext` suffix (e.g., `il-ext`)

Mobile and extended databases are not available for Keyword reports.

| Code | Region | Research Types | Google Domain |
|---|---|---|---|
| `us` | United States | Organic, Adwords, PLA, Keywords | google.com |
| `uk` | United Kingdom | Organic, Adwords, PLA, Keywords | google.co.uk |
| `ca` | Canada | Organic, Adwords, PLA, Keywords | google.ca |
| `ru` | Russia | Organic, Adwords, PLA, Keywords | google.ru |
| `de` | Germany | Organic, Adwords, PLA, Keywords | google.de |
| `fr` | France | Organic, Adwords, PLA, Keywords | google.fr |
| `es` | Spain | Organic, Adwords, PLA, Keywords | google.es |
| `it` | Italy | Organic, Adwords, PLA, Keywords | google.it |
| `br` | Brazil | Organic, Adwords, PLA, Keywords | google.com.br |
| `au` | Australia | Organic, Adwords, PLA, Keywords | google.com.au |
| `ar` | Argentina | Organic, Adwords, PLA, Keywords | google.com.ar |
| `be` | Belgium | Organic, Adwords, PLA, Keywords | google.be |
| `ch` | Switzerland | Organic, Adwords, PLA, Keywords | google.ch |
| `dk` | Denmark | Organic, Adwords, PLA, Keywords | google.dk |
| `fi` | Finland | Organic, Adwords, Keywords | google.fi |
| `hk` | Hong Kong | Organic, Adwords, PLA, Keywords | google.com.hk |
| `ie` | Ireland | Organic, Adwords, PLA, Keywords | google.ie |
| `il` | Israel | Organic, Adwords, Keywords | google.co.il |
| `mx` | Mexico | Organic, Adwords, PLA, Keywords | google.com.mx |
| `nl` | Netherlands | Organic, Adwords, PLA, Keywords | google.nl |
| `no` | Norway | Organic, Adwords, PLA, Keywords | google.no |
| `pl` | Poland | Organic, Adwords, PLA, Keywords | google.pl |
| `se` | Sweden | Organic, Adwords, PLA, Keywords | google.se |
| `sg` | Singapore | Organic, Adwords, PLA, Keywords | google.com.sg |
| `tr` | Turkey | Organic, Adwords, PLA, Keywords | google.com.tr |
| `jp` | Japan | Organic, Adwords, PLA, Keywords | google.co.jp |
| `in` | India | Organic, Adwords, PLA, Keywords | google.co.in |
| `hu` | Hungary | Organic, Adwords, Keywords | google.hu |
| `at` | Austria | Organic, Adwords, PLA, Keywords | google.at |
| `nz` | New Zealand | Organic, Adwords, PLA, Keywords | google.co.nz |
| `cl` | Chile | Organic, Adwords, PLA, Keywords | google.cl |
| `co` | Colombia | Organic, Adwords, PLA, Keywords | google.com.co |
| `cz` | Czech Republic | Organic, Adwords, PLA, Keywords | google.cz |
| `id` | Indonesia | Organic, Adwords, PLA, Keywords | google.co.id |
| `my` | Malaysia | Organic, Adwords, PLA, Keywords | google.com.my |
| `ph` | Philippines | Organic, Adwords, PLA, Keywords | google.com.ph |
| `pt` | Portugal | Organic, Adwords, PLA, Keywords | google.pt |
| `za` | South Africa | Organic, Adwords, PLA, Keywords | google.co.za |
| `ae` | United Arab Emirates | Organic, Adwords, PLA, Keywords | google.ae |
| `af` | Afghanistan | Organic, Adwords, Keywords | google.com.af |
| `al` | Albania | Organic, Adwords, Keywords | google.al |
| `dz` | Algeria | Organic, Adwords, Keywords | google.dz |
| `ao` | Angola | Organic, Adwords, Keywords | google.co.ao |
| `am` | Armenia | Organic, Adwords, Keywords | google.am |
| `az` | Azerbaijan | Organic, Adwords, Keywords | google.az |
| `bh` | Bahrain | Organic, Adwords, Keywords | google.com.bh |
| `bd` | Bangladesh | Organic, Adwords, Keywords | google.com.bd |
| `by` | Belarus | Organic, Adwords, Keywords | google.by |
| `bz` | Belize | Organic, Adwords, Keywords | google.com.bz |
| `bo` | Bolivia | Organic, Adwords, Keywords | google.com.bo |
| `ba` | Bosnia and Herzegovina | Organic, Adwords, Keywords | google.ba |
| `bw` | Botswana | Organic, Adwords, Keywords | google.co.bw |
| `bn` | Brunei | Organic, Adwords, Keywords | google.com.bn |
| `bg` | Bulgaria | Organic, Adwords, Keywords | google.bg |
| `cv` | Cabo Verde | Organic, Adwords, Keywords | google.cv |
| `kh` | Cambodia | Organic, Adwords, Keywords | google.com.kh |
| `cm` | Cameroon | Organic, Adwords, Keywords | google.cm |
| `cr` | Costa Rica | Organic, Adwords, Keywords | google.co.cr |
| `hr` | Croatia | Organic, Adwords, Keywords | google.hr |
| `cy` | Cyprus | Organic, Adwords, Keywords | google.com.cy |
| `cd` | Congo | Organic, Adwords, Keywords | google.cd |
| `do` | Dominican Republic | Organic, Adwords, Keywords | google.com.do |
| `ec` | Ecuador | Organic, Adwords, Keywords | google.com.ec |
| `eg` | Egypt | Organic, Adwords, Keywords | google.com.eg |
| `sv` | El Salvador | Organic, Adwords, Keywords | google.com.sv |
| `ee` | Estonia | Organic, Adwords, Keywords | google.ee |
| `et` | Ethiopia | Organic, Adwords, Keywords | google.com.et |
| `ge` | Georgia | Organic, Adwords, Keywords | google.ge |
| `gh` | Ghana | Organic, Adwords, Keywords | google.com.gh |
| `gr` | Greece | Organic, Adwords, Keywords | google.gr |
| `gt` | Guatemala | Organic, Adwords, Keywords | google.com.gt |
| `gy` | Guyana | Organic, Adwords, Keywords | google.gy |
| `ht` | Haiti | Organic, Adwords, Keywords | google.ht |
| `hn` | Honduras | Organic, Adwords, Keywords | google.hn |
| `is` | Iceland | Organic, Adwords, Keywords | google.is |
| `jm` | Jamaica | Organic, Adwords, Keywords | google.com.jm |
| `jo` | Jordan | Organic, Adwords, Keywords | google.jo |
| `kz` | Kazakhstan | Organic, Adwords, Keywords | google.kz |
| `kw` | Kuwait | Organic, Adwords, Keywords | google.com.kw |
| `lv` | Latvia | Organic, Adwords, Keywords | google.lv |
| `lb` | Lebanon | Organic, Adwords, Keywords | google.com.lb |
| `lt` | Lithuania | Organic, Adwords, Keywords | google.lt |
| `lu` | Luxembourg | Organic, Adwords, Keywords | google.lu |
| `mg` | Madagascar | Organic, Adwords, Keywords | google.mg |
| `mt` | Malta | Organic, Adwords, Keywords | google.com.mt |
| `mu` | Mauritius | Organic, Adwords, Keywords | google.mu |
| `md` | Moldova | Organic, Adwords, Keywords | google.md |
| `mn` | Mongolia | Organic, Adwords, Keywords | google.mn |
| `me` | Montenegro | Organic, Adwords, Keywords | google.me |
| `ma` | Morocco | Organic, Adwords, Keywords | google.co.ma |
| `mz` | Mozambique | Organic, Adwords, Keywords | google.co.mz |
| `na` | Namibia | Organic, Adwords, Keywords | google.com.na |
| `np` | Nepal | Organic, Adwords, Keywords | google.com.np |
| `ni` | Nicaragua | Organic, Adwords, Keywords | google.com.ni |
| `ng` | Nigeria | Organic, Adwords, Keywords | google.com.ng |
| `om` | Oman | Organic, Adwords, Keywords | google.com.om |
| `py` | Paraguay | Organic, Adwords, Keywords | google.com.py |
| `pe` | Peru | Organic, Adwords, Keywords | google.com.pe |
| `ro` | Romania | Organic, Adwords, Keywords | google.ro |
| `sa` | Saudi Arabia | Organic, Adwords, Keywords | google.com.sa |
| `sn` | Senegal | Organic, Adwords, Keywords | google.sn |
| `rs` | Serbia | Organic, Adwords, Keywords | google.rs |
| `sk` | Slovakia | Organic, Adwords, Keywords | google.sk |
| `si` | Slovenia | Organic, Adwords, Keywords | google.si |
| `kr` | South Korea | Organic, Adwords, Keywords | google.co.kr |
| `lk` | Sri Lanka | Organic, Adwords, Keywords | google.lk |
| `th` | Thailand | Organic, Adwords, Keywords | google.co.th |
| `bs` | Bahamas | Organic, Adwords, Keywords | google.bs |
| `tt` | Trinidad and Tobago | Organic, Adwords, Keywords | google.tt |
| `tn` | Tunisia | Organic, Adwords, Keywords | google.tn |
| `ua` | Ukraine | Organic, Adwords, Keywords | google.com.ua |
| `uy` | Uruguay | Organic, Adwords, Keywords | google.com.uy |
| `ve` | Venezuela | Organic, Adwords, Keywords | google.co.ve |
| `vn` | Vietnam | Organic, Adwords, Keywords | google.com.vn |
| `zm` | Zambia | Organic, Adwords, Keywords | google.co.zm |
| `zw` | Zimbabwe | Organic, Adwords, Keywords | google.co.zw |
| `ly` | Libya | Organic, Adwords, Keywords | google.com.ly |
| `pa` | Panama | Organic, Adwords, Keywords | google.com.pa |
| `pk` | Pakistan | Organic, Adwords, Keywords | google.com.pk |
| `tw` | Taiwan | Organic, Adwords, Keywords | google.com.tw |
| `qa` | Qatar | Organic, Adwords, Keywords | google.com.qa |
| **Mobile databases** | | | |
| `mobile-us` | United States | Organic, Adwords | google.com |
| `mobile-uk` | United Kingdom | Organic, Adwords | google.com |
| `mobile-ca` | Canada | Organic, Adwords | google.ca |
| `mobile-de` | Germany | Organic, Adwords | google.de |
| `mobile-fr` | France | Organic, Adwords | google.fr |
| `mobile-es` | Spain | Organic, Adwords | google.es |
| `mobile-it` | Italy | Organic, Adwords | google.it |
| `mobile-br` | Brazil | Organic, Adwords | google.com.br |
| `mobile-au` | Australia | Organic, Adwords | google.com.au |
| `mobile-dk` | Denmark | Organic, Adwords | google.dk |
| `mobile-mx` | Mexico | Organic, Adwords | google.com.mx |
| `mobile-nl` | Netherlands | Organic, Adwords | google.nl |
| `mobile-se` | Sweden | Organic, Adwords | google.se |
| `mobile-tr` | Turkey | Organic, Adwords | google.com.tr |
| `mobile-in` | India | Organic, Adwords | google.co.in |
| `mobile-id` | Indonesia | Organic, Adwords | google.co.id |
| `mobile-il` | Israel | Organic, Adwords | google.co.il |
| **Extended databases** | | | |
| `il-ext` | Israel Ext | Organic, Adwords | google.co.il |
| `tr-ext` | Turkey Ext | Organic, Adwords, PLA | google.com.tr |
| `dk-ext` | Denmark Ext | Organic, Adwords | google.dk |
| `no-ext` | Norway Ext | Organic, Adwords | google.no |
| `se-ext` | Sweden Ext | Organic, Adwords | google.se |
| `fi-ext` | Finland Ext | Organic, Adwords | google.fi |
| `ch-ext` | Switzerland Ext | Organic, Adwords, PLA | google.ch |
| `mobile-il-ext` | Israel Ext (Mobile) | Organic, Adwords | google.co.il |

---

## Error Messages

| Error | Description | Recommended Action |
|---|---|---|
| `ERROR 40` | `action` parameter missing or empty. | Add the parameter or set its value. |
| `ERROR 41` | `type` parameter missing or empty. | Add the parameter or set its value. |
| `ERROR 42` | `domain` parameter missing or empty. | Add the parameter or set its value. |
| `ERROR 43` | `phrase` parameter missing or empty. | Add the parameter or set its value. |
| `ERROR 44` | `url` parameter missing or empty. | Add the parameter or set its value. |
| `ERROR 46` | `database` parameter missing or empty. | Add the parameter or set its value. |
| `ERROR 48` | Invalid request method. | Use HTTP GET. |
| `ERROR 50` | No results found. | Verify parameters; contact support if correct. |
| `ERROR 110` | API key has incorrect format. | Find correct key at Subscription info. |
| `ERROR 120` | Unknown API key. | Find correct key at Subscription info. |
| `ERROR 130` | Subscription doesn't include API access. | Upgrade subscription plan. |
| `ERROR 131` | Report request limit reached. | Contact Semrush Support. |
| `ERROR 132` | API unit balance is zero. | Recharge balance or upgrade subscription. |
| `ERROR 133` | Database access denied. | Contact Semrush Sales for database access. |
| `ERROR 134` | Total API request limit reached. | Contact Semrush Support. |
| `ERROR 135` | Report unavailable or subscription ended. | Check for alternative report or update subscription. |
| `ERROR 136` | Internal limit error (multiple limits). | Contact Semrush Support. |
| `ERROR 402` | API key incorrect. | Find correct key at Subscription info. |
| `ERROR 402 :: Duplicate domains` | `targets` parameter contains duplicates. | Remove duplicate values. |
| `ERROR 404` | User information not found in database. | Contact Semrush Support. |
| `ERROR 429` | Request rate too high. | Lower request rate per API usage restrictions. |
| `ERROR 500` | Internal error. | Try again later or contact support. |
| `ERROR 605` | `display_offset` equals or exceeds `display_limit`. | Set `display_offset` to a lower value. |
| `ERROR 613` | Too many rows requested. | Lower `display_limit` and/or `display_offset`. |
| `ERROR 10000` | Invalid parameter value. | Specify value per description. |
| `ERROR 10001` | Duplicated parameter. | Remove duplicate from request. |
| `ERROR 10010` | Parameter value out of range. | Specify value per description. |
| `ERROR 10011` | Value below minimum. | Specify value per description. |
| `ERROR 10012` | Value above maximum. | Specify value per description. |
| `ERROR 10013` | Required parameter not specified. | Add the required parameter. |
| `ERROR 10014` | Parameter has duplicate values. | Remove duplicate values. |
| `ERROR 10015` | Parameter incompatible with other values. | Adjust per description. |
| `ERROR 10030` | Too many values for parameter. | Reduce number of values. |
| `ERROR 10031` | Not enough values for parameter. | Add missing values. |
| `ERROR 10040` | `selected_targets` exceeds `targets` excludes segment limit. | Align `selected_targets` with excludes limit. |
| `ERROR 10041` | `selected_targets` domains not all in `targets`. | Use only domains specified in `targets`. |
| `ERROR 10042` | Value is not a domain. | Specify a valid domain. |
| `ERROR 10043` | Invalid date — must be first of month. | Specify first day of month. |
| `ERROR 10044–10045` | Invalid parameter value. | Specify value per description. |

---

## Filters

Add the `display_filter` parameter with a URL-encoded string. Multiple filters are separated by `|` (`%7C`). Max 25 filters per request.

**Single filter format:** `<sign>|<field>|<operation>|<value>`

- `<sign>`: `+` (`%2B`) to include, `-` (`%2D`) to exclude
- `<field>`: See field tables below
- `<operation>`: See Operations section
- `<value>`: Depends on field type

> Note: Some libraries encode `+` incorrectly — ensure it is encoded as `%2B`.

### Example Requests

Filter keywords with search volume under 1000:
```
https://api.semrush.com/?type=phrase_related&key=YOUR_API_KEY&phrase=seo&export_columns=Ph,Nq,Cp,Co,Nr,Td,Rr,Fk&database=us&display_limit=10&display_sort=nq_desc&display_filter=%2B%7CNq%7CLt%7C1000
```

Filter organic keywords with transactional intent ranking below position 5:
```
https://api.semrush.com/?type=domain_organic&key=YOUR_API_KEY&display_limit=10&export_columns=Ph,Po,Pp,Pd,Nq,Cp,Ur,Tr,In,Pp&domain=toyota.com&display_sort=tr_desc&database=us&display_filter=%2B%7CIn%7CEq%7C3%7C%2B%7CPp%7CGt%7C5
```

### Metric Fields (for filters)

| Field | Description |
|---|---|
| `Co` | Competitive density (0–1). |
| `Cp` | Average CPC in USD. |
| `Db` | Regional database. |
| `Hs` | Whether line returns historical data. |
| `Wc` | Word count. |
| `Nq` | Average monthly search volume (last 12 months). |
| `Nr` | Total organic results for keyword. |
| `P0`–`P4` | Position of queried domain 1–5. |
| `Ph` | Keyword (max 300 chars; comma = OR operator). |
| `Po` | Position in Google top 100. |
| `Pp` | Previous position. |
| `Pr` | Price of promoted product. |
| `Qu` | Query. |
| `Rt` | Report type. |
| `Tc` | % of domain's total traffic cost for keyword. |
| `Tr` | Traffic share for keyword. |
| `Ts` | UNIX timestamp. |
| `Tt` | PLA title / product name. |
| `Ur` | Target page URL. |
| `Vu` | Visible URL. |
| `In` | Keyword intent: `0` Commercial, `1` Informational, `2` Navigational, `3` Transactional. |
| `Ipu` | Positions with unknown intent. |
| `Ip0`–`Ip3` | Positions with Commercial/Informational/Navigational/Transactional intent. |

### Text Fields (for filters)

| Field | Description |
|---|---|
| `Ph` | Keyword. |
| `Qu` | Query. |
| `Rt` | Report type. |
| `Ur` | URL in search results. |
| `Vu` | Display URL on ad. |
| `title` | Text ad title. |
| `text` | Text ad body. |
| `ad` | Concatenated title + text + visible URL. |
| `url` | Visible URL, target URL, or domain. |

### Fields with Fixed Values (for filters)

| Field | Description | Possible Values |
|---|---|---|
| `Db` | Regional database. | `us`, `uk`, `mobile-uk`, `ca`, `mobile-ca`, `ru`, `de`, `mobile-de`, `fr`, `mobile-fr`, `es`, `mobile-es`, `it`, `mobile-it`, `br`, `mobile-br`, `au`, `mobile-au`, `bing-us`, `ar`, `be`, `ch`, `dk`, `mobile-dk`, `fi`, `hk`, `ie`, `il`, `mobile-il`, `mx`, `mobile-mx`, `nl`, `mobile-nl`, `no`, `pl`, `se`, `mobile-se`, `sg`, `tr`, `mobile-tr`, `jp`, `in`, `mobile-in`, `hu`, `mobile-us` |
| `Hs` | Historical data line. | `0`, `1` |
| `type` | Backlink type. | `nofollow`, `frame`, `form`, `image` |
| `zone` | Backlink TLD zone. | (TLD string) |
| `Br` | Branded keywords. | `0` Not branded, `1` Branded for other domain, `3` Branded |

### Operations

**For metric fields:**

| Operation | Description |
|---|---|
| `Eq` | Equals |
| `Gt` | Greater than |
| `Lt` | Less than |

**For text fields:**

| Operation | Description |
|---|---|
| `Bw` | Starts with |
| `Ew` | Ends with |
| `Eq` | Exactly matching |
| `Co` | Containing |
| `Wm` | Word matching |

**For fields with fixed values:** Leave the operation blank.

---

## SERP Features

Used with `FKn`/`FPn` columns in the `export_columns` parameter.

| Code | Name | Links to Domain | Description |
|---|---|---|---|
| `0` | Instant answer | No | Direct answer in a gray-bordered box at top of results. |
| `1` | Knowledge panel | Yes | Info block to the right of organic results. |
| `2` | Carousel | No | Horizontally scrollable images at top of results. |
| `3` | Local pack | Yes | Map with three local results for local queries. |
| `4` | Top stories | Yes | Card-style snippet with up to three news results. |
| `5` | Image pack | Yes | Collection of images between organic results. |
| `6` | Sitelinks | Yes | Links to other pages under the main result. |
| `7` | Reviews | Yes | Results with star ratings and review counts. |
| `8` | Tweet | No | Card-style snippet of recent tweets. |
| `9` | Video | Yes | Video results with thumbnail. |
| `10` | Featured video | Yes | Video result at top of all organic results. |
| `11` | Featured Snippet | Yes | Short answer with source link at top of results. |
| `12` | AMP | No | Mobile-friendly pages (not distinguished from other results by Google). |
| `13` | Image | Yes | Image result with thumbnail among organic results. |
| `14` | Ads top | No | Ads at top of first results page. |
| `15` | Ads bottom | No | Ads at bottom of first results page. |
| `16` | Shopping ads | No | Paid shopping results carousel at top of page. |
| `17` | Hotels Pack | No | Hotel results block with prices and ratings. |
| `18` | Jobs search | No | Job listings at top of results page. |
| `19` | Featured images | No | Images at top of SERP (mobile only). |
| `20` | Video Carousel | Yes | Horizontally scrollable videos among results. |
| `21` | People also ask | Yes | Expandable related questions between results. |
| `22` | FAQ | Yes | Expandable FAQ list attached to an organic result. |
| `23` | Flights | No | Flight results from Google Flights. |
| `24` | Find results on | Yes | Block of domains displayed above a map. |
| `25` | Recipes | Yes | Recipe block at top of results. |
| `26` | Related Topics | No | List of related topics. |
| `27` | Twitter carousel | Yes | Carousel of tweets among organic results. |
| `28` | Indented | Yes | Related pages from the highest organic result. |
| `29` | News | Yes | Trending news among organic results. |
| `30` | Address Pack | No | Map with popular places at top of results. |
| `31` | Application | Yes | App from App Store/Play Store (mobile only). |
| `32` | Events | No | Relevant events at top of organic results. |
| `34` | Popular products | No | Carousel of reviewed products for purchase. |
| `35` | Related products | No | Carousel of related products for purchase. |
| `36` | Related searches | No | Related searches among organic results. |
| `37` | See results about | No | More precise queries on right of results page. |
| `38` | Short videos | Yes | Block of vertical videos (mobile only). |
| `39` | Web stories | Yes | Block of vertical stories (mobile only). |
| `40` | Application list | Yes | List of apps among organic results (mobile only). |
| `41` | Buying guide | Yes | Block of questions about product features. |
| `42` | Organic carousel | Yes | Carousel with organic results at top of SERP. |
| `43` | Things to know | Yes | Block of most common related questions. |
| `44` | Datasets | Yes | List of scientific datasets. |
| `45` | Discussions and forums | Yes | Block of related discussions. |
| `46` | Explore brands | Yes | List of related brands. |
| `47` | Questions and answers | Yes | Carousel of related Q&A. |
| `48` | Popular stores | Yes | List of popular related stores. |
| `49` | Refine | No | Related queries with clarifying keywords. |
| `50` | People also search | No | Competitor brands at bottom of SERP. |
| `51` | Ads middle | No | Ads in middle of first results page. |
| `52` | AI overview | Yes | AI-generated answer. |

### Example: SERP Feature Columns in Request

```
https://api.semrush.com/?key=API_KEY&type=domain_ranks&export_columns=Db,Dn,Rk,Or,Ot,Oc,Ad,At,Ac,Sh,Sv,FK1,FP1&domain=apple.com&database=us
```

- `FP1` — count of times the domain ranks within Knowledge panel (code 1)
- `FK1` — total occurrences of Knowledge panel for keywords the domain ranks for, whether or not the domain appears in it

---

## Sortings

Use the `display_sort` parameter with one sorting rule per request.

| Sort Value | Description |
|---|---|
| `am_asc` / `am_desc` | Changes in paid keywords (`Am`) |
| `bm_asc` / `bm_desc` | Changes in paid traffic (`Bm`) |
| `cg_asc` / `cg_desc` | Traffic cost (`Cg`) |
| `cm_asc` / `cm_desc` | Changes in ads traffic price (`Cm`) |
| `co_asc` / `co_desc` | Competition (`Co`) |
| `cp_asc` / `cp_desc` | CPC (`Cp`) |
| `cr_asc` / `cr_desc` | Competition level (`Cr`) |
| `cv_asc` / `cv_desc` | Coverage (`Cv`) |
| `dt_asc` / `dt_desc` | Date of last update (`Ts`) |
| `kd_asc` / `kd_desc` | Keyword difficulty (`Kd`) |
| `np_asc` / `np_desc` | Common keywords (`Np`) |
| `nq_asc` / `nq_desc` | Search volume (`Nq`) |
| `nr_asc` / `nr_desc` | Number of results (`Nr`) |
| `om_asc` / `om_desc` | Changes in organic keywords (`Om`) |
| `p0_asc` / `p0_desc` | Position of 1st domain (`P0`) |
| `p1_asc` / `p1_desc` | Position of 2nd domain (`P1`) |
| `p2_asc` / `p2_desc` | Position of 3rd domain (`P2`) |
| `p3_asc` / `p3_desc` | Position of 4th domain (`P3`) |
| `p4_asc` / `p4_desc` | Position of 5th domain (`P4`) |
| `pc_asc` / `pc_desc` | Number of keywords (`Pc`) |
| `po_asc` / `po_desc` | Position (`Po`) |
| `pr_asc` / `pr_desc` | Price (`Pr`) |
| `scm_asc` / `scm_desc` | Changes in SERP Features organic traffic cost (`Scm`) |
| `srm_asc` / `srm_desc` | Changes in keywords with SERP Feature positions (`Srm`) |
| `stm_asc` / `stm_desc` | Changes in SERP Features traffic (`Stm`) |
| `tc_asc` / `tc_desc` | Traffic cost share (`Tc`) |
| `tg_asc` / `tg_desc` | Traffic (`Tg`) |
| `tm_asc` / `tm_desc` | Changes in organic traffic (`Tm`) |
| `tr_asc` / `tr_desc` | Traffic share (`Tr`) |
| `ts_asc` / `ts_desc` | Timestamp (`Ts`) |
| `um_asc` / `um_desc` | Changes in organic traffic price (`Um`) |
| `last_seen_asc` / `last_seen_desc` | Last-seen date (`last_seen`) |
| `first_seen_asc` / `first_seen_desc` | First-seen date (`first_seen`) |
| `times_seen_asc` / `times_seen_desc` | Number of times seen (`times_seen`) |
| `ads_count_asc` / `ads_count_desc` | Number of display ads (`ads_count`) |

### Sorting Example

Sort Domain Organic Search Keywords by traffic share descending:
```
https://api.semrush.com/?type=domain_organic&key=YOUR_API_KEY&display_filter=%2B%7CPh%7CCo%7Cseo&display_limit=10&export_columns=Ph,Po,Pp,Pd,Nq,Cp,Ur,Tr,Tc,Co,Nr,Td&domain=seobook.com&display_sort=tr_desc&database=us
```

---

## Historical Data

Most analytic reports support historical data. Historical data costs more than current data — for example, Domain Overview (all databases) costs **50 API units/line** for historical vs. **10 API units/line** for current.

Some reports (e.g., Domain Overview (history)) provide only historical data; the listed price already reflects historical rates.
