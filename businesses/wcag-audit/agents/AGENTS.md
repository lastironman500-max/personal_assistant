# AI Agent Assignments

This business operates as a zero-employee, AI-powered operation. Each agent handles a specific domain of the business. The human operator focuses on sales calls, client communication, quality spot-checks, and strategic decisions.

---

## Agent Overview

```
┌─────────────────────────────────────────────────┐
│                HUMAN OPERATOR                     │
│  Sales calls | Client comms | Quality review     │
│  Strategic decisions | Agency partnerships        │
└──────────────┬────────────────────────────────────┘
               │
    ┌──────────┼──────────┬──────────┬──────────┐
    │          │          │          │          │
    v          v          v          v          v
┌────────┐ ┌────────┐ ┌────────┐ ┌────────┐ ┌────────┐
│SCANNER │ │WRITER  │ │OUTREACH│ │PROSPECT│ │FINANCE │
│ AGENT  │ │ AGENT  │ │ AGENT  │ │ AGENT  │ │ AGENT  │
└────────┘ └────────┘ └────────┘ └────────┘ └────────┘
```

---

## 1. Scanner Agent

**Purpose:** Crawl websites and produce raw accessibility violation data.

### Responsibilities

- Accept a URL and discover all pages (sitemap + link crawl)
- Run axe-core against every discovered page
- Collect violations, incomplete items, and pass/fail counts
- Output structured JSON with all findings
- Capture annotated screenshots of violations (for outreach)

### Technology Stack

| Component | Tool |
|-----------|------|
| Browser automation | Playwright (headless Chromium) |
| Crawler framework | Crawlee (queue, dedup, sitemap support) |
| Accessibility engine | @axe-core/playwright |
| Screenshot capture | Playwright screenshot API |

### LLM Usage

None. The Scanner Agent is purely deterministic — it runs axe-core and outputs structured data. No AI model is needed for this step.

### Inputs

| Input | Format | Source |
|-------|--------|--------|
| Target URL | String | Client order or Prospector Agent |
| Page limit | Number | Determined by tier (5/50/100) |
| Scan config | JSON | WCAG tags to test against |

### Outputs

| Output | Format | Destination |
|--------|--------|-------------|
| Discovered URLs | JSON array | Writer Agent |
| Per-page violations | JSON (axe-core format) | Writer Agent |
| Incomplete items | JSON | Writer Agent |
| Pass/fail summary | JSON | Writer Agent |
| Screenshots | PNG files | Outreach Agent (for evidence) |

### Error Handling

- Site unreachable: retry 2x, then report as unreachable
- Anti-bot protection: flag for manual URL list input
- Page crash: skip page, note in output
- Memory limit: cap concurrent browser tabs at 3

---

## 2. Writer Agent

**Purpose:** Transform raw scan data into a professional, human-readable report.

### Responsibilities

- Deduplicate violations that appear across multiple pages
- Write plain-English descriptions of each issue type
- Explain the user impact (who is affected and how)
- Generate code-level remediation examples (before/after HTML)
- Prioritize issues by severity and user impact
- Produce the executive summary
- Generate the compliance scorecard (WCAG criterion-by-criterion)
- Build the priority matrix (Impact vs. Effort)
- Create the phased remediation roadmap
- Format everything into the report template

### Technology Stack

| Component | Tool |
|-----------|------|
| Per-page analysis | Claude Haiku 4.5 (cost-efficient) |
| Executive summary | Claude Sonnet 4.6 (higher quality) |
| Report template | HTML + Tailwind CSS |
| PDF rendering | Puppeteer (page.pdf()) |

### LLM Configuration

**Per-page analysis prompt (Haiku 4.5):**
- System: "You are a WCAG accessibility expert. Analyze the following axe-core violations for a single web page. For each violation, write a plain-English description, explain the user impact, and provide a specific HTML code fix. Output as structured JSON."
- Input: axe-core violations JSON + page URL + page title
- Output: Structured JSON with enhanced descriptions

**Executive summary prompt (Sonnet 4.6):**
- System: "You are a senior accessibility consultant writing an executive summary for a business owner. Synthesize all findings into a clear risk assessment, top 3 priorities, and phased remediation roadmap. Write for a non-technical audience."
- Input: Aggregated findings JSON + site-wide statistics
- Output: Executive summary text + priority matrix + roadmap

**Batch API:** Use for all non-urgent scans (50% cost reduction).

### Inputs

| Input | Format | Source |
|-------|--------|--------|
| Per-page violations | JSON | Scanner Agent |
| Incomplete items | JSON | Scanner Agent |
| Pass/fail summary | JSON | Scanner Agent |
| Client info | JSON | Order intake |
| Report template | HTML | Templates directory |

### Outputs

| Output | Format | Destination |
|--------|--------|-------------|
| Completed report | PDF (2-8 MB) | Email delivery (Resend) |
| Report data | JSON | Client portal (Phase 2) |

### Quality Controls

- Every report must include the disclaimer text (non-negotiable)
- AI disclosure statement must appear in the report
- 57% detection ceiling must be stated
- Manual testing recommendation must be included
- Spot-check 1 in 5 reports for accuracy (human operator)

---

## 3. Outreach Agent

**Purpose:** Generate personalized cold outreach messages using scan evidence.

### Responsibilities

- Take scan data from the Scanner Agent and compose personalized emails
- Write LinkedIn DM messages with violation evidence
- Customize messaging by industry (ecommerce, healthcare, SaaS)
- Customize messaging by geography (reference state-specific lawsuit data)
- Generate follow-up sequences (Day 3, Day 7)
- Annotate screenshots for visual evidence
- Track which templates and subject lines perform best

### Technology Stack

| Component | Tool |
|-----------|------|
| Message generation | Claude Haiku 4.5 |
| Email sending | Gmail (manual) or Instantly/Lemlist (automated) |
| LinkedIn messaging | Manual (to avoid automation bans) |
| Screenshot annotation | Canva or Playwright overlay |
| Tracking | Google Sheets + Streak CRM |

### LLM Configuration

**Email generation prompt (Haiku 4.5):**
- System: "You are a B2B sales copywriter specializing in accessibility compliance. Write a cold email that leads with specific scan findings from the prospect's website. Reference ADA lawsuit data relevant to their industry and state. Include a clear call to action. Keep under 200 words."
- Input: Prospect info (name, company, industry, state) + top 3 violations + violation counts
- Output: Complete email text with subject line

### Inputs

| Input | Format | Source |
|-------|--------|--------|
| Prospect info | JSON | Prospector Agent |
| Scan violations | JSON | Scanner Agent |
| Screenshots | PNG | Scanner Agent |
| Template library | Markdown | Templates directory |

### Outputs

| Output | Format | Destination |
|--------|--------|-------------|
| Cold emails | Text | Email sending tool |
| LinkedIn DMs | Text | Human operator (manual send) |
| Follow-up emails | Text | Email sending tool |
| Annotated screenshots | PNG | Email attachments |

### Rules

- Never claim to offer a "full audit" or "compliance guarantee"
- Always include specific violations from their site (never generic)
- Always reference industry-specific lawsuit data
- Maximum 3 follow-ups per prospect
- Stop sequence immediately on "not interested" or "unsubscribe"

---

## 4. Prospector Agent

**Purpose:** Identify, qualify, and enrich target companies for outreach.

### Responsibilities

- Search for companies in target industries and geographies
- Find decision-maker contact information (email, LinkedIn)
- Qualify prospects by company size, industry, and web presence
- Prioritize prospects by likelihood of conversion
- Maintain and update the prospect database
- Trigger Scanner Agent for pre-outreach scans

### Technology Stack

| Component | Tool |
|-----------|------|
| Company search | Google search operators, Apollo.io, LinkedIn |
| Email discovery | Hunter.io, Apollo.io |
| Qualification | Claude Haiku 4.5 (assess website for scan-worthiness) |
| Database | Google Sheets (MVP) / CRM (Phase 2) |

### LLM Configuration

**Qualification prompt (Haiku 4.5):**
- System: "You are a sales qualification expert. Given a company's industry, size, geographic location, and website technology stack, score them 1-10 on likelihood of purchasing a WCAG accessibility scan. Consider: ADA lawsuit risk for their industry, regulatory deadlines, company size (50-500 is sweet spot), and web platform (Shopify/WooCommerce = high priority)."
- Input: Company info
- Output: Score (1-10) + reasoning

### Inputs

| Input | Format | Source |
|-------|--------|--------|
| Target criteria | JSON | Business plan (industry, geography, size) |
| Search results | HTML/JSON | Google, Apollo, LinkedIn |
| Scan results | JSON | Scanner Agent (post-scan qualification) |

### Outputs

| Output | Format | Destination |
|--------|--------|-------------|
| Qualified prospect list | CSV/JSON | Outreach Agent |
| Contact info (email, LinkedIn) | CSV | Outreach Agent |
| Prospect scores | JSON | Tracking sheet |
| Scan requests | URL list | Scanner Agent |

### Weekly Targets

| Week | New Prospects Found | Emails Verified | Scans Triggered |
|------|-------------------|----------------|-----------------|
| Week 1 | 50 | 30 | 50 |
| Week 2 | 75 | 50 | 75 |
| Week 3+ | 100 | 75 | 100 |

---

## 5. Finance Agent

**Purpose:** Track all revenue, expenses, and financial metrics.

### Responsibilities

- Log every payment received (amount, client, tier, date)
- Log every expense (amount, category, date)
- Calculate running P&L (daily, weekly, monthly)
- Track unit economics (COGS, CAC, LTV, margins)
- Monitor Compliance subscriber MRR and churn
- Generate financial reports
- Alert when reinvestment milestones are reached
- Track budget vs. actual

### Technology Stack

| Component | Tool |
|-----------|------|
| Data entry | Google Sheets (MVP) |
| Calculations | Google Sheets formulas or Claude Haiku 4.5 |
| Payment tracking | Stripe dashboard API |
| Reporting | Claude Haiku 4.5 (narrative summaries) |

### LLM Configuration

**Financial summary prompt (Haiku 4.5):**
- System: "You are a financial analyst for a small business. Given the revenue and expense data for the period, generate a concise financial summary including: total revenue, total expenses, net profit, gross margin, notable trends, and recommended actions."
- Input: Period data (revenue log, expense log)
- Output: Financial summary text + KPI dashboard

### Key Metrics Tracked

| Metric | Frequency | Target |
|--------|-----------|--------|
| Revenue (daily/weekly/monthly) | Daily | See projections |
| COGS per scan | Per scan | <$0.20 |
| Gross margin | Monthly | >97% |
| CAC (blended) | Monthly | <$30 |
| LTV:CAC ratio | Monthly | >100:1 |
| Compliance MRR | Monthly | Growing |
| Compliance churn rate | Monthly | <5% |
| Break-even status | Weekly | Exceeded from Day 1 |
| Cash runway | Weekly | >3 months |

### Reinvestment Milestone Alerts

| Revenue Milestone | Alert | Action |
|-------------------|-------|--------|
| $500 cumulative | "Time to form LLC" | Legal protection |
| $1,500 cumulative | "Time for E&O insurance" | Risk mitigation |
| $3,000 cumulative | "Time for attorney review" | Disclaimer validation |
| $5,000 cumulative | "Upgrade prospecting tools" | Sales acceleration |
| $10,000 cumulative | "Build web frontend" | Self-serve ordering |

---

## Agent Interaction Flow

### New Client Order Flow

```
1. Human operator receives inquiry
2. Human confirms order + collects payment
3. Human triggers scan: node scan.js --url <url> --email <email>
4. Scanner Agent → crawls + scans site → outputs violation JSON
5. Writer Agent → analyzes findings → generates PDF report
6. Report delivered to client via Resend
7. Finance Agent → logs revenue
8. Human → follows up with client, asks for referrals
```

### Outreach Flow

```
1. Prospector Agent → finds 50 target companies + emails
2. Scanner Agent → scans all 50 sites (batch)
3. Outreach Agent → generates personalized emails from scan data
4. Human → sends emails (manual for deliverability)
5. Human → handles replies, books calls, closes deals
6. Scanner Agent + Writer Agent → deliver paid reports
7. Finance Agent → logs everything
```

### Monthly Monitoring Flow (Compliance Tier)

```
1. Scheduler triggers monthly re-scan (cron job)
2. Scanner Agent → re-scans all Compliance subscriber sites
3. Writer Agent → generates delta report (what changed since last scan)
4. Report delivered automatically via Resend
5. Finance Agent → logs recurring revenue
```

---

## Phase 2 Agent Enhancements

| Agent | Enhancement | Timeline |
|-------|------------|----------|
| Scanner | Add Pa11y as secondary scanner (+5-8% coverage) | Month 2 |
| Writer | Interactive HTML report version | Month 2 |
| Outreach | A/B testing framework for subject lines | Month 2 |
| Prospector | Automated LinkedIn scraping (with compliance) | Month 3 |
| Finance | Stripe webhook integration for auto-logging | Month 2 |
| **New: Support Agent** | Handle client questions via email templates | Month 3 |
| **New: QA Agent** | Automated spot-check of report accuracy | Month 3 |
