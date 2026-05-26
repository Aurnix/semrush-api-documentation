I'm building a local library of AI-ingestible Semrush API documentation. The workflow is simple: I manually copy text from Semrush API doc pages and paste them to you, and you convert each one into a clean `.md` file saved to `/Users/josephsherman/api_docs/`.

**What's already done (94 files):**

- **General (5):** authorization.md, quick_start.md, api_unit_balance.md, troubleshooting.md, faq.md
- **Trends API (complete, 20 files):** overview, resources, one tutorial, and one file per endpoint
- **SEO API (complete, 76 files):**
  - Overview: seo_api_overview.md
  - Backlink Analytics (14 files): seo_backlinks_*.md
  - Domain Reports (12 files): seo_domain_organic.md, seo_domain_adwords.md, seo_domain_ads_copies.md, seo_domain_organic_competitors.md, seo_domain_adwords_competitors.md, seo_domain_ad_history.md, seo_domain_vs_domain.md, seo_domain_pla_keywords.md, seo_domain_pla_copies.md, seo_domain_pla_competitors.md, seo_domain_organic_pages.md, seo_domain_organic_subdomains.md
  - Keyword Reports (10 files): seo_keyword_*.md
  - Overview Reports (5 files): seo_domain_overview_all.md, seo_domain_overview.md, seo_domain_overview_history.md, seo_winners_and_losers.md, seo_semrush_rank.md
  - Subdomain Reports (7 files): seo_subdomain_*.md
  - Subfolder Reports (7 files): seo_subfolder_*.md
  - URL Reports (5 files): seo_url_*.md
  - Tutorials (3 files): seo_tutorial_keyword_gaps.md, seo_tutorial_ai_overview_impact.md, seo_tutorial_google_sheets.md

**What's next:** Projects API and Local API.

**Formatting conventions to follow exactly:**

- **Filenames:** snake_case prefixed by API name (e.g., `projects_*`, `local_*`).
- **File structure:** `# Title` → `**Price:**` and (if applicable) `**Price (historical data):**` → short description → `## Endpoint` (with code-fenced `GET https://...`) → `## Parameters` table with `Required` column (Yes/No) → optional `## Deprecated Columns` section with ⚠️ markers → `## Example Request` (code-fenced URL) → `## Example Response` (code-fenced CSV).
- **Cost note** at the top of every endpoint file. Note when historical-data pricing differs (per request vs. per line — they differ).
- **Parameter tables** with Required column. Default and Available values for `export_columns`. List allowed values inline for `display_sort`, `display_positions`, `display_positions_type`, `display_filter` fields.
- **Deprecated columns** marked with ⚠️ in a separate subsection.
- **Historical data cutoff** noted when it differs from default.
- **Response examples** truncated to about 5 rows when raw data is very long.
- **Country code lists** omitted from individual endpoints — link back to `seo_api_overview.md#databases` (the overview has the full table).
- **SEO API responses use semicolons as delimiters** (not commas) by default. If a Semrush example shows commas + quoted columns, preserve it verbatim with a one-line note (this happens on a few Pages/Ads Copies endpoints because they were captured with `export_escape=1`).
- **No `display_sort` parameter on some endpoints** — only include it if the source page lists it. Same rule for `display_filter`, `display_positions`, `display_positions_type`, `display_date`, `display_daily`, `export_decode`.
- **Cross-references:** link to other endpoint docs and back to `seo_api_overview.md` for Columns / Filters / Sortings / Databases.
- **For multi-endpoint pages:** I may paste the entire page in one go — split it into one file per endpoint. Confirm if anything is ambiguous before writing.
- **Source-fidelity quirks observed so far:**
  - Semrush docs occasionally show inconsistent `display_limit` max values within the same endpoint (e.g., `1,000,000` in the param itself but `4,000,000` in the offset note). Preserve both — they're docs bugs.
  - Subdomain Overview (one database) is the only endpoint where Semrush forgot to mark `type`/`key`/`subdomain`/`database` as Required in the source. Mark them Yes anyway since they're clearly required.
- **Memory:** the project memory file at `~/.claude/projects/-Users-josephsherman-api-docs/memory/project_semrush_api_docs.md` tracks the file count and the completed/remaining list. Update it after each batch.

**Workflow:** just paste pages one at a time (or whole multi-endpoint pages — that works fine) and I'll handle the rest.
