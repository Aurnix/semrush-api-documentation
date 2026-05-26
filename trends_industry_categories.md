# Trends API — Industry Categories

**Cost:** 500 API units per request  
**Billing note:** Units are charged even if the response is empty.

Returns a list of all domains within a specified industry category, along with traffic metrics and audience demographics for each domain.

---

## Endpoint

```
GET https://api.semrush.com/analytics/ta/api/v3/categories
```

---

## Request Parameters

| Parameter | Required | Description |
|-----------|----------|-------------|
| `key` | Yes | Your API key (from Subscription info → API Units) |
| `category` | Yes | Category name from the list of 110 available categories (e.g. `human_resources`). See Industry Categories reference for all values. |
| `display_date` | No | Month in `YYYY-MM-01` format. Defaults to previous month. Min: `2017-01-01`. Max: start of current month. |
| `country` | No | ISO 3166-1 Alpha-2 country code. Defaults to global data. |
| `display_limit` | No | Number of results to return. Max: `5000`. Use with `display_offset` for pagination. |
| `display_offset` | No | Number of results to skip before returning data. Max: `10000`. Use with `display_limit` for pagination. |
| `export_columns` | No | Comma-separated columns to return. Defaults to all columns. |

---

## Export Columns

### Traffic

| Column | Description |
|--------|-------------|
| `domain_name` | Domain |
| `total_traffic` | Total visits |
| `direct_traffic` | Direct traffic |
| `referral_traffic` | Referral traffic |
| `search_organic_traffic` | Organic search traffic |
| `search_paid_traffic` | Paid search traffic |
| `social_organic_traffic` | Organic social traffic |
| `social_paid_traffic` | Paid social traffic |
| `email_traffic` | Email traffic |
| `display_ad_traffic` | Display ad traffic |
| `ai_assistants_traffic` | Traffic from AI assistants (e.g. ChatGPT, Copilot) |
| `ai_search_traffic` | Traffic from AI search engines (e.g. Gemini) |

### Social Platforms

| Column | Description |
|--------|-------------|
| `facebook_traffic` | Traffic from Facebook |
| `youtube_traffic` | Traffic from YouTube |
| `pinterest_traffic` | Traffic from Pinterest |
| `instagram_traffic` | Traffic from Instagram |
| `twitter_traffic` | Traffic from Twitter/X |
| `linkedin_traffic` | Traffic from LinkedIn |
| `vk_traffic` | Traffic from VK |
| `reddit_traffic` | Traffic from Reddit |

### Engagement & Conversion

| Column | Description |
|--------|-------------|
| `conversion_rate` | Purchase conversion rate |
| `unique_visitors` | Unique visitors |
| `users_captured` | Users captured |
| `hits` | Total hits |
| `sum_time_on_site` | Total time on site |
| `bounce_rate` | Bounce rate |
| `bounced_visits` | Number of bounced visits |
| `report_date` | Date of the data |
| `country_code` | Country filter used |

### Demographics — Gender & Age

| Column | Description |
|--------|-------------|
| `male` | Share of male visitors |
| `female` | Share of female visitors |
| `age_18_24` | Share aged 18–24 |
| `age_25_34` | Share aged 25–34 |
| `age_35_44` | Share aged 35–44 |
| `age_45_54` | Share aged 45–54 |
| `age_55_64` | Share aged 55–64 |
| `age_65_plus` | Share aged 65+ |
| `male_18_24` … `male_65_plus` | Male share by age band |
| `female_18_24` … `female_65_plus` | Female share by age band |

### Socioeconomic

| Column | Description |
|--------|-------------|
| `edu_level_compulsory_school` | Share with compulsory school education |
| `edu_level_none_completed` | Share with no completed education |
| `edu_level_post_graduate_education` | Share with post-graduate education |
| `edu_level_university` | Share with university education |
| `high_income` | Share with high income |
| `middle_income` | Share with middle income |
| `low_income` | Share with low income |
| `household_size_1` … `household_size_10plus` | Share by household size |
| `occupation_fulltimework` | Share employed full-time |
| `occupation_homemaker` | Share homemakers |
| `occupation_parttimework` | Share employed part-time |
| `occupation_studies` | Share in studies |
| `occupation_unemployed` | Share unemployed |
| `occupation_ownbusiness` | Share owning a business |
| `occupation_retired` | Share retired |
| `occupation_leaveofabsence` | Share on leave of absence |
| `occupation_parentalleave` | Share on parental leave |

---

## Request Example

```
https://api.semrush.com/analytics/ta/api/v3/categories?category=human_resources&country=AD&display_limit=10&display_offset=0&key=YOUR_API_KEY
```

## Response Example (CSV, truncated)

```
domain_name;total_traffic;direct_traffic;referral_traffic;search_organic_traffic;search_paid_traffic;...;report_date
infojobs.net;3747;3201;0;498;48;...;2025-08-01
cvdesignr.com;1274;1274;0;0;0;...;2025-08-01
indeed.com;1216;495;180;403;138;...;2025-08-01
```

*Full response includes all demographic and socioeconomic columns per domain row.*
