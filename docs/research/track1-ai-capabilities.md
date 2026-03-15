# Research Track 1: AI Autonomous Capabilities Audit

**Date:** 2026-03-15
**Purpose:** Identify tasks AI (LLMs + tools) can perform 100% autonomously — from input to finished deliverable — with no human review or editing required for delivery.

**Mental model:** The IDOR bug bounty example. AI scans a site, finds a vulnerability, writes a structured report, submits it. Money is paid. No human touched the output before delivery.

---

## Scoring Key

- **Autonomy**: `100%` = AI does everything, no human in loop | `partial` = human needed for QA/review/judgment | `no` = human required
- **Quality bar**: `high` = output is indistinguishable from expert human work | `medium` = good enough, minor flaws acceptable | `low` = functional but imperfect, and that's OK
- **Existing demand**: `yes` = people pay for this today | `maybe` = adjacent demand exists | `no` = unproven

---

## Category 1: Data & Analysis Tasks

### 1.1 SEO Audit Reports

**What AI does:** Crawl a website, extract meta tags, check title lengths, analyze heading structure, find missing alt text, check canonical tags, identify broken internal links, score page speed data via API, compile into a structured PDF/HTML report.

**Tools needed:** Web scraper (Playwright/Puppeteer), Lighthouse API, LLM for narrative, PDF generator.

**Input:** Domain URL + customer email
**Output:** Structured SEO audit report (PDF or HTML) with prioritized recommendations

| Dimension | Score | Notes |
|-----------|-------|-------|
| Autonomy | 100% | No judgment calls needed — rules-based + narrative generation |
| Quality bar | medium | Reports are formulaic; buyers expect structured checklists, not creative insight |
| Existing demand | yes | Fiverr: $15–$150 per audit. Agencies charge $300–$2,000. Freelancers sell these daily. |

**Why it qualifies:** SEO audits follow deterministic rules. AI can check every rule and write the narrative. Buyers buy the checklist + prioritization, not creative insight.

**Risk:** Commoditized. Ahrefs, Semrush already offer automated versions. Differentiation needed.

---

### 1.2 Competitive Intelligence Reports

**What AI does:** Given a target company domain, scrape their website, pull LinkedIn headcount/job postings via APIs, fetch Crunchbase funding data, summarize recent news via search APIs, analyze pricing pages, compile into a structured competitive brief.

**Tools needed:** Search APIs (Serper/Brave), scraper, Crunchbase API, LLM synthesis.

**Input:** Competitor URL or company name
**Output:** 5–10 page competitive brief (pricing, positioning, team size, recent moves, SWOT)

| Dimension | Score | Notes |
|-----------|-------|-------|
| Autonomy | 100% | Data collection + synthesis is fully automatable |
| Quality bar | medium | AI can match junior analyst output; senior analyst nuance missing |
| Existing demand | yes | VC firms, startups, sales teams pay $200–$2,000 per report |

**Why it qualifies:** Competitive briefs are data aggregation + structured narrative — exactly what LLMs excel at with tool use.

---

### 1.3 Lead List Generation + Enrichment

**What AI does:** Given an ICP (ideal customer profile), search LinkedIn/Apollo/Hunter APIs, extract company names, employee names, roles, emails, LinkedIn URLs, company size, funding stage. Deduplicate. Export as CSV.

**Tools needed:** Apollo API, Hunter.io API, LinkedIn scraping (carefully), Clearbit API, LLM for filtering/scoring.

**Input:** ICP description (e.g., "SaaS CTOs at Series A companies in NY, 50–200 employees")
**Output:** Enriched CSV/spreadsheet of 100–500 qualified leads with contact info

| Dimension | Score | Notes |
|-----------|-------|-------|
| Autonomy | 100% | Filtering criteria are rules-based; API calls are automated |
| Quality bar | medium | Data freshness matters; AI can score leads but not verify intent |
| Existing demand | yes | Fiverr: $30–$200 per list. Agencies charge $500–$5,000 per campaign. Apollo/ZoomInfo itself is a $1B+ market. |

**Why it qualifies:** Pure data aggregation + filtering. No creative judgment needed. Buyers just want the spreadsheet.

---

### 1.4 Website Accessibility Audit (WCAG Compliance)

**What AI does:** Run axe-core or WAVE tool programmatically against a URL, capture all WCAG 2.1 violations, categorize by severity (A/AA/AAA), generate remediation recommendations per violation, output structured report.

**Tools needed:** Playwright + axe-core library, LLM for remediation text, PDF/HTML renderer.

**Input:** URL
**Output:** Structured WCAG compliance report with pass/fail status and fix recommendations

| Dimension | Score | Notes |
|-----------|-------|-------|
| Autonomy | 100% | Rule-based scanning; remediation text is templatable/generatable |
| Quality bar | high | axe-core catches ~57% of WCAG issues automatically — well-known and accepted standard |
| Existing demand | yes | ADA compliance lawsuits surging; businesses pay $200–$3,000 for audits |

**Why it qualifies:** The tooling (axe-core) already does the scanning. AI wraps it with professional report formatting and prioritized recommendations. Legally defensible output.

---

### 1.5 Data Cleaning & Normalization

**What AI does:** Accept a dirty CSV/spreadsheet, detect column types, standardize formats (phone numbers, addresses, dates, company names), deduplicate records, flag anomalies, output clean version.

**Tools needed:** Python (pandas), LLM for ambiguous cases, file I/O.

**Input:** Dirty CSV file
**Output:** Clean CSV + change log

| Dimension | Score | Notes |
|-----------|-------|-------|
| Autonomy | 100% | Rules-based + LLM for edge cases |
| Quality bar | medium | 95%+ accuracy achievable; buyers accept small error rates |
| Existing demand | yes | Upwork: constant demand. $50–$500 per dataset. Data quality is a perennial problem. |

---

### 1.6 Financial Statement Extraction (PDF → Structured Data)

**What AI does:** Accept a PDF annual report or earnings release, extract revenue, EBITDA, margins, YoY growth, key metrics, output as structured JSON or spreadsheet.

**Tools needed:** PDF parser, LLM with structured output, validation logic.

**Input:** PDF financial document
**Output:** Structured JSON/CSV with labeled financial metrics

| Dimension | Score | Notes |
|-----------|-------|-------|
| Autonomy | 100% | Extraction + structuring is automatable; validation catches errors |
| Quality bar | high | LLMs are excellent at financial document parsing |
| Existing demand | yes | Analysts, investors, fintech companies pay $20–$200 per document |

---

## Category 2: Content Generation (Low-QA-Required)

### 2.1 Product Description Writing (E-commerce)

**What AI does:** Accept product name, SKU, specs, category. Generate SEO-optimized product description (150–300 words), bullet points, meta title, meta description.

**Tools needed:** LLM, templating, optional: competitor scraping for style matching.

**Input:** Product name + specs (CSV row or JSON)
**Output:** Product description + meta fields, ready to paste into Shopify/WooCommerce

| Dimension | Score | Notes |
|-----------|-------|-------|
| Autonomy | 100% | Template-driven generation; QA only needed for brand voice (which can be prompted) |
| Quality bar | medium | Adequate for mid-market e-commerce; luxury brands may want human review |
| Existing demand | yes | Fiverr sellers earn $5–$50/description. Bulk orders (100+ products) are common. Shopify merchants pay $200–$2,000 for catalog work. |

**Why it qualifies:** E-commerce merchants with 100+ SKUs can't afford to write each description manually. AI batch-generates at $0.02/description. Margin is enormous.

---

### 2.2 Alt Text Generation for Images

**What AI does:** Accept image URLs or files, generate descriptive alt text that passes WCAG 2.1 requirements, output as CSV mapping filename → alt text.

**Tools needed:** Vision model (GPT-4o, Claude), file handler.

**Input:** Batch of images (ZIP or URLs)
**Output:** CSV of image path → alt text

| Dimension | Score | Notes |
|-----------|-------|-------|
| Autonomy | 100% | Vision models handle this reliably |
| Quality bar | high | Functional, accurate descriptions are achievable |
| Existing demand | yes | ADA compliance need + SEO benefit. Agencies charge $1–$5/image. Volume orders of 1,000+ images are common. |

---

### 2.3 Meta Tag Generation (Bulk)

**What AI does:** Accept a list of URLs or page titles + content snippets. Generate SEO meta titles (50–60 chars) and meta descriptions (150–160 chars) for each. Output as CSV ready for import.

**Tools needed:** LLM, optional scraper for existing page content.

**Input:** List of URLs or page content snippets
**Output:** CSV with URL, meta title, meta description columns

| Dimension | Score | Notes |
|-----------|-------|-------|
| Autonomy | 100% | Character count constraints make this rule-checkable |
| Quality bar | medium | Good enough for most sites; editorial choice is minimal |
| Existing demand | yes | Constant demand on Fiverr/Upwork. $50–$500 for 50–500 pages. |

---

### 2.4 Job Description Generation

**What AI does:** Accept a job title, company description, required skills, seniority level. Generate a full job description (500–800 words): summary, responsibilities, requirements, benefits boilerplate.

**Tools needed:** LLM.

**Input:** Job title + brief company context + key requirements
**Output:** Full job description ready to post

| Dimension | Score | Notes |
|-----------|-------|-------|
| Autonomy | 100% | Templated structure; content is formulaic |
| Quality bar | medium | Acceptable for most companies; HR teams often just edit lightly |
| Existing demand | yes | HR teams, recruiters, startups pay $20–$100/description |

---

### 2.5 Real Estate Listing Descriptions

**What AI does:** Accept property specs (bedrooms, bathrooms, sq ft, neighborhood, features, price). Generate compelling 150–300 word listing description for Zillow/MLS/etc.

**Tools needed:** LLM.

**Input:** Property spec sheet (form or CSV)
**Output:** MLS-ready listing description

| Dimension | Score | Notes |
|-----------|-------|-------|
| Autonomy | 100% | Formulaic genre; real estate agents just want the draft |
| Quality bar | medium | Agents may tweak but rarely reject entirely |
| Existing demand | yes | Realtors pay $20–$75/listing. Large brokerages need hundreds monthly. |

---

### 2.6 Google Business Profile Optimization Reports

**What AI does:** Given a GBP listing (scraped or API), analyze completeness, suggest missing categories, generate optimized business description (750 chars), suggest Q&A responses, output as a report + ready-to-paste content.

**Tools needed:** Google Places API, LLM.

**Input:** Business name + location
**Output:** GBP optimization report + ready-to-use content blocks

| Dimension | Score | Notes |
|-----------|-------|-------|
| Autonomy | 100% | Criteria for optimization are well-documented; content generation is straightforward |
| Quality bar | medium | Local SEO buyers just want the checklist and copy |
| Existing demand | yes | Local SEO agencies charge $100–$500 for this. Constant Fiverr demand. |

---

## Category 3: Code & Technical Tasks

### 3.1 Automated Security Scanning + Report

**What AI does:** Run OWASP ZAP or Nuclei against a target URL (with permission), collect findings, map to CVE/OWASP categories, generate prioritized remediation report.

**Tools needed:** Nuclei, OWASP ZAP, LLM for report writing.

**Input:** Domain URL + written scope permission
**Output:** Security scan report (PDF/HTML) with findings, CVSS scores, remediation steps

| Dimension | Score | Notes |
|-----------|-------|-------|
| Autonomy | 100% | Scanning is automated; LLM wraps findings into professional report |
| Quality bar | medium | Automated scanners miss complex logic flaws; but cover common vulns well |
| Existing demand | yes | SMBs pay $200–$2,000 for basic security audits. Compliance-driven demand is huge. |

**Key constraint:** Requires explicit written permission. Scope creep = legal liability. Must be operationalized carefully.

---

### 3.2 Code Review Automation

**What AI does:** Accept a GitHub repo URL or PR diff, analyze code for bugs, security issues, code style violations, performance problems, generate structured code review report with line-by-line feedback.

**Tools needed:** GitHub API, LLM.

**Input:** GitHub repo URL or PR diff
**Output:** Structured code review report (markdown or PDF)

| Dimension | Score | Notes |
|-----------|-------|-------|
| Autonomy | 100% | LLMs are excellent at code review |
| Quality bar | medium | Catches common issues well; misses subtle architectural problems |
| Existing demand | yes | Dev teams, CTOs, bootcamp grads pay $50–$500 for code reviews. "Get your code reviewed" is a known pain. |

---

### 3.3 Test Case Generation (Unit Tests)

**What AI does:** Accept a codebase or function signatures, generate comprehensive unit test suite (pytest, jest, mocha, etc.), covering happy path, edge cases, error cases.

**Tools needed:** LLM, file I/O.

**Input:** Source code file(s) or repo URL
**Output:** Test files ready to run

| Dimension | Score | Notes |
|-----------|-------|-------|
| Autonomy | 100% | LLMs generate syntactically correct tests reliably |
| Quality bar | medium | Tests may need minor fixes; coverage is typically 70–85% good |
| Existing demand | yes | Dev shops pay $100–$500 for test suites. Technical debt cleanup is constant work. |

---

### 3.4 API Documentation Generation

**What AI does:** Accept a codebase or OpenAPI spec, generate comprehensive API documentation (endpoint descriptions, parameter tables, request/response examples, error codes).

**Tools needed:** LLM, code parser.

**Input:** Codebase or OpenAPI YAML/JSON
**Output:** Full API docs (Markdown, HTML, or ready for Notion/Confluence)

| Dimension | Score | Notes |
|-----------|-------|-------|
| Autonomy | 100% | Documentation from code/spec is well within LLM capability |
| Quality bar | high | LLMs produce excellent technical documentation |
| Existing demand | yes | Developers hate writing docs. Agencies charge $200–$2,000 for this. |

---

### 3.5 Dependency Vulnerability Audit

**What AI does:** Accept a package.json / requirements.txt / Gemfile, run against CVE databases (npm audit, safety, bundler-audit), list vulnerable packages with CVE details and upgrade paths.

**Tools needed:** npm audit, pip-audit, OSV API, LLM for remediation narrative.

**Input:** Dependency manifest file
**Output:** Vulnerability report with severity ratings and fix recommendations

| Dimension | Score | Notes |
|-----------|-------|-------|
| Autonomy | 100% | Fully automated; existing tools do the scanning |
| Quality bar | high | Output matches what a security engineer would produce |
| Existing demand | yes | Compliance-driven. DevSecOps teams need this regularly. $50–$500/report. |

---

### 3.6 Code Refactoring (Specific Patterns)

**What AI does:** Accept legacy code, apply specific refactoring patterns (extract function, rename variable, convert callbacks to async/await, migrate from deprecated API), output refactored code with diff.

**Tools needed:** LLM, diff tool.

**Input:** Source code + refactoring instructions
**Output:** Refactored code + change summary

| Dimension | Score | Notes |
|-----------|-------|-------|
| Autonomy | partial | Works well for mechanical refactors; complex logic changes need human review |
| Quality bar | medium | Acceptable for targeted, well-scoped refactors |
| Existing demand | yes | Tech debt cleanup is perennial. Dev shops pay $100–$1,000 for this. |

---

## Category 4: Monitoring & Alerting

### 4.1 Price Monitoring Service

**What AI does:** Periodically scrape target URLs (competitor pricing pages, Amazon, retail sites), detect price changes, send structured alerts (email/Slack/webhook) with change details and trend analysis.

**Tools needed:** Playwright (scraper), scheduler, notification service, LLM for summary.

**Input:** List of URLs to monitor + alert preferences
**Output:** Automated alerts on price changes; weekly summary report

| Dimension | Score | Notes |
|-----------|-------|-------|
| Autonomy | 100% | Detection + alerting is fully automated |
| Quality bar | high | Binary: price changed or not. Clear, objective output. |
| Existing demand | yes | E-commerce businesses, procurement teams pay $50–$500/month. PriceSpider, Wiser exist at enterprise scale. |

---

### 4.2 Brand Mention Monitoring

**What AI does:** Monitor Reddit, Twitter/X (API), news sites, forums for brand/keyword mentions. Aggregate, classify sentiment, flag priority mentions (complaints, competitor comparisons, PR risks), send daily digest.

**Tools needed:** Reddit API, news search APIs, LLM for sentiment/classification.

**Input:** Brand name + keywords + alert preferences
**Output:** Daily digest with classified mentions, sentiment score, priority flags

| Dimension | Score | Notes |
|-----------|-------|-------|
| Autonomy | 100% | Monitoring + classification + digest generation is fully automated |
| Quality bar | medium | Sentiment classification is ~90% accurate; good enough for alerts |
| Existing demand | yes | Mention, Brand24 are SaaS products in this space. SMBs pay $50–$300/month. |

---

### 4.3 Domain Expiry + SSL Certificate Monitoring

**What AI does:** Monitor a list of domains for expiry dates, SSL certificate status, WHOIS changes, DNS changes. Send alerts at 90/60/30/7 day thresholds.

**Tools needed:** WHOIS APIs, SSL check libraries, scheduler, email/Slack notifier.

**Input:** List of domains
**Output:** Automated alerts + monthly health report

| Dimension | Score | Notes |
|-----------|-------|-------|
| Autonomy | 100% | Fully automated; deterministic output |
| Quality bar | high | Binary checklist — either valid or expiring |
| Existing demand | yes | Agencies, IT teams pay $10–$100/month for this. StatusCake, UptimeRobot exist. |

**Note:** Commoditized — established SaaS tools dominate. Only viable as upsell/add-on.

---

### 4.4 Uptime + Performance Monitoring

**What AI does:** Ping URLs at intervals, measure response time, detect downtime, track Core Web Vitals over time, alert on degradation, generate monthly performance trend report.

**Tools needed:** HTTP checker, Lighthouse API, scheduler, notification service.

**Input:** URL list + alert thresholds
**Output:** Uptime logs + performance trend report

| Dimension | Score | Notes |
|-----------|-------|-------|
| Autonomy | 100% | Fully automated |
| Quality bar | high | Objective metrics; well-understood output |
| Existing demand | yes | Extremely commoditized. UptimeRobot, Pingdom. Hard to compete on this alone. |

---

### 4.5 Trademark / Brand Squatting Monitoring

**What AI does:** Monitor new domain registrations, trademark databases (USPTO), app stores for brand name variations. Detect squatting/infringement. Alert legal/brand team.

**Tools needed:** WHOIS bulk feeds, USPTO TSDR API, app store search APIs.

**Input:** Brand names + monitoring preferences
**Output:** Weekly report of potential infringements/squatters

| Dimension | Score | Notes |
|-----------|-------|-------|
| Autonomy | 100% | Detection is rules-based; LLM helps with similarity scoring |
| Quality bar | medium | False positives exist; legal judgment still needed for action |
| Existing demand | yes | Law firms, brand teams pay $200–$2,000/month for monitoring services |

---

## Category 5: Research & Intelligence

### 5.1 Patent Landscape Search

**What AI does:** Given a technology area or invention description, search USPTO/Google Patents APIs, cluster existing patents by topic, identify key holders/competitors, flag potential conflicts, generate structured patent landscape report.

**Tools needed:** Google Patents API, USPTO API, LLM for synthesis.

**Input:** Technology description or keyword set
**Output:** Patent landscape report with key patent holders, clusters, white spaces

| Dimension | Score | Notes |
|-----------|-------|-------|
| Autonomy | 100% | Search + cluster + synthesize is automatable |
| Quality bar | medium | IP attorneys want this level of output as a starting point; they do FTO analysis on top |
| Existing demand | yes | IP attorneys, R&D teams pay $500–$5,000 for landscape searches |

---

### 5.2 Company Due Diligence Reports

**What AI does:** Given a company name, aggregate: incorporation records (if public), Crunchbase data, news mentions, LinkedIn headcount, Glassdoor reviews, court records (PACER), product reviews. Generate structured due diligence brief.

**Tools needed:** Multiple APIs, web scraper, LLM synthesis.

**Input:** Company name + jurisdiction
**Output:** Structured due diligence brief

| Dimension | Score | Notes |
|-----------|-------|-------|
| Autonomy | 100% | Data aggregation + structuring is fully automatable |
| Quality bar | medium | Public data only; AI can't access private financials or do interviews |
| Existing demand | yes | Investors, acquirers, enterprise procurement pay $200–$2,000/report |

---

### 5.3 LinkedIn Profile / Resume Scoring

**What AI does:** Accept a resume (PDF/text) or LinkedIn URL, score against a job description or ideal candidate profile, provide structured gap analysis, generate interview question suggestions.

**Tools needed:** PDF parser, LLM.

**Input:** Resume + job description
**Output:** Structured fit score + gap analysis + recommended questions

| Dimension | Score | Notes |
|-----------|-------|-------|
| Autonomy | 100% | Rubric-based scoring is fully automatable |
| Quality bar | medium | Screening-level quality; final hiring judgment is human |
| Existing demand | yes | HR teams, recruiters pay $10–$100/assessment. HireVue, Greenhouse have similar features. |

---

### 5.4 Grant Opportunity Search

**What AI does:** Given a nonprofit mission/organization description, search federal grants (Grants.gov), state grants, foundation databases. Filter by eligibility criteria. Generate a prioritized list of relevant opportunities with deadlines and fit scores.

**Tools needed:** Grants.gov API, foundation database scraper, LLM for matching.

**Input:** Org description + mission + focus area
**Output:** Prioritized grant opportunity list with eligibility notes and deadlines

| Dimension | Score | Notes |
|-----------|-------|-------|
| Autonomy | 100% | Search + filter + match is fully automatable |
| Quality bar | medium | Finding opportunities is valuable; writing applications still needs humans |
| Existing demand | yes | Nonprofits pay $100–$500 for grant research. Grant consultants charge $50–$150/hour for this exact task. |

---

### 5.5 Regulation & Compliance Summary

**What AI does:** Given a business type + jurisdiction, search relevant regulations (GDPR, CCPA, HIPAA, SOX, etc.), summarize applicable requirements, identify gaps based on a checklist, generate compliance summary report.

**Tools needed:** Regulatory text databases, LLM.

**Input:** Business type + jurisdiction + data handling description
**Output:** Compliance summary report with applicable regulations + gap checklist

| Dimension | Score | Notes |
|-----------|-------|-------|
| Autonomy | 100% | Mapping business type to regulations is well-structured |
| Quality bar | medium | Summary-level only; legal interpretation needs attorney review |
| Existing demand | yes | Startups, SMBs pay $200–$2,000 for compliance assessments. Legal tech is hot. |

**Note:** Must include disclaimer that output is not legal advice.

---

### 5.6 Influencer Research Report

**What AI does:** Given a niche/keyword, search social platforms (YouTube, Instagram, TikTok via APIs), pull follower counts, engagement rates, audience demographics, recent post analysis. Score influencers by fit criteria. Export ranked list.

**Tools needed:** Social media APIs (YouTube Data API, etc.), LLM for scoring.

**Input:** Niche description + campaign criteria
**Output:** Ranked influencer list with stats, sample content analysis, fit scores

| Dimension | Score | Notes |
|-----------|-------|-------|
| Autonomy | 100% | Data collection + scoring is automatable |
| Quality bar | medium | Quantitative metrics are solid; qualitative brand fit still benefits from human review |
| Existing demand | yes | Brands, agencies pay $100–$1,000 for influencer research. AspireIQ, Grin are SaaS tools in this space. |

---

## Category 6: Automation & Integration

### 6.1 File Format Conversion (Bulk)

**What AI does:** Accept files in one format (CSV, JSON, XML, PDF, DOCX, XLS), convert to another format with data mapping, output ready-to-use files.

**Tools needed:** Conversion libraries (pandoc, python-docx, etc.), LLM for ambiguous mappings.

**Input:** Source files + target format specification
**Output:** Converted files

| Dimension | Score | Notes |
|-----------|-------|-------|
| Autonomy | 100% | Deterministic transformation |
| Quality bar | high | Format conversion is binary — it works or it doesn't |
| Existing demand | yes | Constant low-value demand on Fiverr. $10–$100/job. High volume possible. |

---

### 6.2 Zapier/Make Workflow Documentation

**What AI does:** Accept a description of a business workflow or an existing Zapier/Make export, generate structured documentation: flow diagram (Mermaid), step-by-step instructions, troubleshooting guide.

**Tools needed:** LLM, Mermaid renderer.

**Input:** Workflow description or export file
**Output:** Workflow documentation (PDF or Confluence-ready Markdown)

| Dimension | Score | Notes |
|-----------|-------|-------|
| Autonomy | 100% | Documentation generation from structured input is straightforward |
| Quality bar | medium | Good enough for internal ops teams |
| Existing demand | maybe | Indirect demand — ops consultants do this; standalone service is niche |

---

### 6.3 Webhook / API Integration Testing Report

**What AI does:** Accept an API spec (OpenAPI YAML), generate test cases, run them against a live or sandbox endpoint, report pass/fail with response bodies, identify inconsistencies between spec and implementation.

**Tools needed:** LLM (test generation), HTTP client library.

**Input:** OpenAPI spec + base URL
**Output:** API test report with pass/fail per endpoint

| Dimension | Score | Notes |
|-----------|-------|-------|
| Autonomy | 100% | Test generation + execution + reporting is fully automated |
| Quality bar | medium | Covers happy path and common edge cases; complex state machines may be missed |
| Existing demand | yes | QA teams, API providers pay $100–$1,000 for API testing services |

---

### 6.4 Database Schema Documentation

**What AI does:** Accept a SQL schema dump or database connection (read-only), generate comprehensive documentation: table descriptions, column definitions, relationship diagrams (Mermaid ERD), sample queries.

**Tools needed:** SQL parser, LLM, Mermaid renderer.

**Input:** SQL schema file or read-only DB connection string
**Output:** Full database documentation (Markdown or HTML)

| Dimension | Score | Notes |
|-----------|-------|-------|
| Autonomy | 100% | Schema-to-docs is deterministic + LLM augmented |
| Quality bar | high | LLMs produce excellent technical documentation |
| Existing demand | yes | Dev teams, data engineers pay $100–$500 for this. Constant demand when onboarding new engineers. |

---

### 6.5 Batch Image Processing (Resize, Compress, Rename, Tag)

**What AI does:** Accept a folder of images, resize to specified dimensions, compress to target file size, rename per convention, generate AI-powered tags/descriptions, output processed folder + manifest CSV.

**Tools needed:** Pillow/Sharp, vision model, file I/O.

**Input:** Image folder + processing spec
**Output:** Processed images + manifest CSV

| Dimension | Score | Notes |
|-----------|-------|-------|
| Autonomy | 100% | Fully automated; no judgment needed |
| Quality bar | high | Image processing is deterministic |
| Existing demand | yes | E-commerce merchants, photographers pay $50–$500 for bulk image work. |

---

### 6.6 CRM Data Deduplication & Cleanup

**What AI does:** Accept a CRM export (Salesforce, HubSpot), detect duplicate records using fuzzy matching (company name, email, phone), merge/flag duplicates, standardize fields (phone format, country codes, company names), output clean version.

**Tools needed:** Python (recordlinkage, fuzzywuzzy), LLM for ambiguous merges.

**Input:** CRM export CSV
**Output:** Deduplicated + cleaned CRM export + change log

| Dimension | Score | Notes |
|-----------|-------|-------|
| Autonomy | 100% | Deduplication algorithms are well-established; LLM handles edge cases |
| Quality bar | medium | ~95% accuracy; a small number of false merges may occur |
| Existing demand | yes | Sales ops teams constantly need this. $100–$1,000/cleanup job. |

---

## Category 7: High-Signal Opportunities (Cross-Category)

These emerge from combining multiple capabilities above and represent the highest commercial potential for a solo AI operator.

### 7.1 Automated Bug Bounty Scanning

**What AI does:** Run Nuclei + custom scripts against a target scope (provided by bug bounty program), detect known vulnerability classes (XSS, SQLi, SSRF, IDOR, open redirects), generate structured HackerOne/Bugcrowd-compatible report for each finding.

**Tools needed:** Nuclei, custom scripts, LLM for report generation.

**Input:** Scope definition from bug bounty program
**Output:** Vulnerability reports submitted to platform

| Dimension | Score | Notes |
|-----------|-------|-------|
| Autonomy | 100% | Scanning + report generation is automated |
| Quality bar | high | HackerOne/Bugcrowd have clear report format requirements |
| Existing demand | yes | Bug bounty platforms pay $50–$10,000+ per valid finding |

**Why it qualifies:** This is the original mental model. Payment is per valid finding, not per hour. AI can run 24/7 across many programs. Nuclei has 6,000+ templates. High upside per finding.

**Constraint:** Competition from experienced human hunters is high. AI misses chained/logic vulnerabilities. Best for low-hanging fruit at scale.

---

### 7.2 Technical SEO + Content Gap Report (Combined)

**What AI does:** Crawl a site for technical SEO issues (redirects, canonicals, structured data, Core Web Vitals) AND analyze content gaps vs. competitors using keyword research APIs (Ahrefs/Semrush API). Produce a single unified prioritized roadmap report.

**Tools needed:** Scraper, Lighthouse, Ahrefs/Semrush API, LLM synthesis.

**Input:** Domain + 2–3 competitor domains
**Output:** Unified technical + content strategy report (20–40 pages)

| Dimension | Score | Notes |
|-----------|-------|-------|
| Autonomy | 100% | Combined automation of two well-understood tasks |
| Quality bar | medium-high | Better than either alone; matches what boutique agencies produce |
| Existing demand | yes | Agencies charge $1,000–$5,000 for this. Deliverable is clear. |

---

### 7.3 Full Website Audit Package (SEO + Accessibility + Security + Performance)

**What AI does:** Run four parallel audits (SEO, WCAG accessibility, security headers, Core Web Vitals performance), synthesize into a unified prioritized report with executive summary, severity matrix, and fix priority order.

**Tools needed:** SEO scraper, axe-core, security headers checker, Lighthouse, LLM synthesis.

**Input:** Domain URL
**Output:** Comprehensive website audit PDF (executive summary + 4 detailed sections)

| Dimension | Score | Notes |
|-----------|-------|-------|
| Autonomy | 100% | All four audits are automatable; synthesis is LLM-driven |
| Quality bar | medium-high | "All-in-one" framing makes it more sellable than individual audits |
| Existing demand | yes | Agencies charge $500–$5,000 for this type of comprehensive audit |

**Best opportunity among audits.** One deliverable, clear value, higher price point, fully automated.

---

### 7.4 LinkedIn Outreach Personalization at Scale

**What AI does:** Accept a CSV of LinkedIn profiles (or URLs), scrape public profile data (current role, company, recent posts, shared connections), generate 5–10 personalized outreach message variants per prospect using LLM.

**Tools needed:** LinkedIn scraper (with rate limiting), LLM.

**Input:** CSV of LinkedIn profile URLs + campaign context
**Output:** CSV with prospect name, company, personalized message, and 2 follow-up variants

| Dimension | Score | Notes |
|-----------|-------|-------|
| Autonomy | 100% | Scraping + personalization is fully automated |
| Quality bar | medium | Messages are notably better than templates; reply rates improve |
| Existing demand | yes | B2B sales teams pay $200–$2,000 for outreach copy. Lemlist, Lavender exist. |

**Risk:** LinkedIn actively blocks scrapers. Must use proxies and rate limiting.

---

### 7.5 Podcast / Video Transcription + Show Notes + Clips

**What AI does:** Accept an audio/video file, transcribe (Whisper), generate timestamped show notes, identify 5–10 highlight clip suggestions with transcripts, generate SEO-optimized episode description + social media posts.

**Tools needed:** Whisper API, LLM.

**Input:** Audio/video file
**Output:** Transcript + show notes + clip suggestions + SEO description + social posts

| Dimension | Score | Notes |
|-----------|-------|-------|
| Autonomy | 100% | Transcription + content generation is fully automated |
| Quality bar | medium | Transcription is excellent; editorial quality of show notes is good but not premium |
| Existing demand | yes | Podcast agencies charge $50–$200/episode for this. Descript, Castmagic exist as tools. |

---

## Summary Matrix: Top Candidates Ranked

| # | Capability | Autonomy | Quality Bar | Demand | Price Point | Verdict |
|---|-----------|----------|-------------|--------|-------------|---------|
| 1 | Full Website Audit (SEO+A11y+Security+Perf) | 100% | medium-high | yes | $200–$2,000 | **TOP PICK** |
| 2 | Automated Security Scanning + Report | 100% | medium | yes | $200–$2,000 | **TOP PICK** |
| 3 | Lead List Generation + Enrichment | 100% | medium | yes | $100–$2,000 | **HIGH** |
| 4 | Competitive Intelligence Reports | 100% | medium | yes | $200–$2,000 | **HIGH** |
| 5 | Podcast Transcription + Show Notes Package | 100% | medium | yes | $50–$200/ep | **HIGH** |
| 6 | Product Description Writing (Bulk) | 100% | medium | yes | $100–$2,000 | **HIGH** |
| 7 | WCAG Accessibility Audit | 100% | high | yes | $200–$3,000 | **HIGH** |
| 8 | API Documentation Generation | 100% | high | yes | $200–$2,000 | **HIGH** |
| 9 | Bug Bounty Scanning | 100% | high | yes | $50–$10,000+ | **SPECULATIVE** |
| 10 | Patent Landscape Search | 100% | medium | yes | $500–$5,000 | **MEDIUM** |
| 11 | Alt Text Generation (Bulk) | 100% | high | yes | $50–$500 | **MEDIUM** |
| 12 | CRM Data Deduplication | 100% | medium | yes | $100–$1,000 | **MEDIUM** |
| 13 | Data Cleaning / Normalization | 100% | medium | yes | $50–$500 | **MEDIUM** |
| 14 | Financial Statement Extraction | 100% | high | yes | $20–$200/doc | **MEDIUM (volume)** |
| 15 | Dependency Vulnerability Audit | 100% | high | yes | $50–$500 | **MEDIUM** |

---

## Key Findings

### What makes a capability viable for a fully autonomous AI business:

1. **Deterministic output criteria** — the buyer knows what "done" looks like (report with X sections, CSV with Y columns, audit scoring Z items). There is no subjective quality bar that requires human taste.

2. **Tool-augmented, not pure LLM** — the best opportunities combine automated tools (scanners, scrapers, APIs) with LLM for synthesis and narrative. Pure LLM content generation is commoditized. Tool-augmented intelligence is defensible.

3. **Existing buyer category** — the service must map to something buyers already know to purchase. "Website audit" is a known SKU. "AI-generated insights" is not.

4. **Deliverable over the internet** — PDF report, CSV file, Markdown doc. No physical delivery. No meeting required.

5. **Input is trivially collectable** — a domain URL, a CSV, a GitHub link. Low friction for the buyer to engage.

### The autonomy trap to avoid:

Many "AI-assisted" services require human QA before delivery — this breaks the model. The test: *if the AI makes a mistake, does money come back?* For SEO audits and accessibility reports, errors are tolerable and fixable. For code shipped to production, errors are costly. Stick to reports and structured data outputs.

### Best starting point based on this research:

**Full Website Audit (SEO + Accessibility + Security Headers + Performance)** is the top candidate:
- Fully automatable today with existing tools
- Clear deliverable buyers understand
- Price point $200–$2,000 per audit
- Multiple upsell vectors (monitoring, monthly re-audits)
- No legal liability for the output (it's a report, not legal/financial advice)
- Differentiated from generic SEO tools by combining 4 audit types
- Every business with a website is a potential customer

---

*Research conducted: 2026-03-15. Sources: analysis of Fiverr/Upwork marketplace patterns, known tooling landscape, LLM capability benchmarks, and existing SaaS product categories.*
