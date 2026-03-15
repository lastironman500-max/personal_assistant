# Technical Feasibility: AI-Powered WCAG Accessibility Audit Service

**Date:** 2026-03-15
**Status:** Research & Architecture Design
**Author:** Technical Architect

---

## Executive Summary

Building an AI-powered WCAG accessibility audit service is technically feasible today. The core pipeline — crawl, scan, analyze, report, deliver — can be assembled entirely from mature open-source tools and commodity APIs. The key architectural decision is using axe-core (via `@axe-core/playwright`) as the automated scanner, Claude API for narrative interpretation and prioritization, Puppeteer for PDF generation, and Resend for delivery.

The critical caveat: automated tools detect approximately 57% of WCAG issues by volume. The remaining 43% require human judgment. The product must be positioned as an "automated scan with AI interpretation" rather than a full compliance audit. That positioning is honest, legally defensible, and still genuinely valuable — most clients have never run even an automated scan.

---

## 1. Core Pipeline Design

```
URL Input → Crawl → Scan → Analyze → Generate Report → Deliver
```

### Step 1: Crawler (Playwright + Sitemap)

**Approach:** Two-pronged discovery
1. Fetch and parse `sitemap.xml` (and `sitemap_index.xml` recursively) to get declared URLs
2. Playwright link-following crawl starting from the root URL to catch pages not in the sitemap

**Technology stack:**
- `playwright` (Chromium headless) — handles JavaScript-rendered pages, SPAs, dynamic content
- `crawlee` (Crawlee for JS) — wraps Playwright with a request queue, deduplication, and sitemap support via `SitemapRequestLoader`; avoids writing custom crawler logic
- Page limit cap: enforce a configurable max (e.g., 50 pages for standard tier, 200 for enterprise) to prevent runaway scans

**Implementation notes:**
- Launch a single persistent browser context and reuse it across pages (avoids repeated startup cost)
- Intercept and block image, font, and media requests during crawl to cut load time by 40–60%
- Respect `robots.txt` — required for legal and ethical compliance
- Store discovered URLs in a queue with visited-set deduplication
- Estimated crawl speed: ~2–5 seconds per page on a standard VPS with images blocked; 10 pages takes ~20–50 seconds

**Sitemap handling:**
```
GET /sitemap.xml           → parse URLs
GET /sitemap_index.xml     → fetch each child sitemap
Fallback: /robots.txt      → extract Sitemap: directives
Last resort: BFS link crawl from homepage
```

### Step 2: Scanner (axe-core via @axe-core/playwright)

**Technology:** `@axe-core/playwright` — official integration, injects axe-core engine into each Playwright page

**Scan configuration:**
```
Tags: ["wcag2a", "wcag2aa", "wcag21a", "wcag21aa", "wcag22aa", "best-practice"]
```

**Per-page output:**
- `violations` — confirmed failures (report these)
- `incomplete` — "needs review" items requiring human judgment (flag these)
- `passes` — passing rules (summarize counts)
- `inapplicable` — rules not applicable (ignore)

**What axe-core catches (confirmed violations):**
| Category | Examples | Auto-detectable? |
|---|---|---|
| Color contrast | Text contrast ratios below 4.5:1 (AA) or 3:1 (large text) | Yes |
| Images | Missing or empty `alt` attributes on `<img>` | Yes |
| Forms | `<input>` elements without associated `<label>` | Yes |
| Buttons/links | Empty buttons, ambiguous link text ("click here") | Yes |
| Document structure | Missing `<html lang>`, missing `<title>`, heading order violations | Yes |
| ARIA | Invalid ARIA roles, required ARIA attributes missing, orphaned ARIA labels | Yes |
| Tables | Data tables missing `<th>` or `scope` attributes | Yes |
| Keyboard | Missing focus indicators (detectable via CSS analysis) | Partial |
| Skip links | Missing skip navigation links | Yes |
| Iframes | `<iframe>` missing `title` attribute | Yes |

**What axe-core misses (requires manual review):**
| Category | Why automation fails |
|---|---|
| Screen reader reading order | Requires assistive technology to test actual announcement order |
| Cognitive accessibility (WCAG 2.1 1.3.5, 1.4.10) | Requires understanding of user intent and content meaning |
| Focus trap detection | Requires keyboard navigation simulation in interactive flows |
| Meaningful alt text quality | axe-core confirms alt exists; cannot assess if it's meaningful |
| Error recovery in forms | Requires form submission and error flow testing |
| Timing/animation (WCAG 2.1 2.2, 2.3) | Requires interaction with time-based media |
| WCAG 2.2 Focus Appearance | Visual judgment required |
| WCAG 2.2 Target Size (minimum) | axe-core rule exists but flagged as unreliable |
| Custom widgets | Non-native UI components require manual AT testing |
| PDF/document accessibility | Outside browser DOM |

**Bottom line:** Deque's own research shows axe-core finds ~57% of accessibility issues by volume (not by rule count). False positive rate has dropped below 8% as of 2025, meaning violations flagged are almost always real.

### Step 3: Analyzer (Claude API)

**Purpose:** Transform raw axe-core JSON output into human-readable, actionable findings. This is the AI-differentiated layer that justifies charging for the service.

**Model recommendation:** Claude Haiku 4.5 for per-page analysis passes (cost efficiency); Claude Sonnet 4.6 for executive summary generation (quality)

**Tasks Claude performs:**
1. Deduplicate violations that appear across many pages (e.g., "missing lang attribute" on 47 pages → report as one systemic issue)
2. Prioritize violations by real-world impact on users with disabilities (axe-core's impact levels are `critical`, `serious`, `moderate`, `minor` — Claude contextualizes these)
3. Write plain-English descriptions of each issue type and its user impact
4. Generate specific remediation code examples for each violation type
5. Produce the executive summary: overall compliance posture, top 3 critical issues, recommended remediation order
6. Assess WCAG 2.1 Level A/AA conformance status per criterion

**Prompt design:**
- System prompt: Role definition as accessibility expert, output format specification (structured JSON)
- Per-page prompt: Raw axe violations JSON + page URL + page title
- Summary prompt: Aggregated findings JSON + full site stats

**Token estimation per scan (20-page site):**
- Per-page analysis: ~2,000 input tokens (violations JSON) + ~800 output tokens = 2,800 tokens/page × 20 = 56,000 tokens
- Aggregation + executive summary: ~8,000 input + ~3,000 output = 11,000 tokens
- Total per scan: ~67,000 tokens
- Cost at Haiku 4.5 ($1/$5 per MTok): ~$0.067 input + $0.027 output = **~$0.09 per 20-page scan**
- Cost at Sonnet 4.6 ($3/$15 per MTok): ~$0.20 input + $0.082 output = **~$0.28 per 20-page scan**
- Recommended: Use Haiku 4.5 for per-page passes, Sonnet 4.6 only for final summary = **~$0.12 per 20-page scan**

**Batch API note:** For non-urgent scans, the Batch API offers 50% discount, reducing cost to ~$0.06 per 20-page scan.

### Step 4: Report Generation (Puppeteer)

**Technology decision: Puppeteer over WeasyPrint**

| Factor | Puppeteer | WeasyPrint |
|---|---|---|
| Language | Node.js (same stack) | Python (adds a dependency) |
| CSS support | Full Chrome CSS | Partial CSS support |
| JavaScript rendering | Yes | No |
| Charts/graphs in reports | Yes | Limited |
| Deployment complexity | Chromium binary required | Python runtime required |
| PDF quality | Excellent | Good |
| Tagged PDF / accessibility | Experimental | Partial |
| Memory per PDF generation | 200–500 MB (Chromium) | ~50 MB |

**Verdict:** Puppeteer wins for a Node.js stack. The Chromium binary is already present for Playwright scanning — reuse it. WeasyPrint would require a separate Python runtime and doesn't support JavaScript-rendered report templates.

**Report generation approach:**
- Build an HTML report template with Tailwind CSS (or inline CSS for portability)
- Render via Puppeteer's `page.pdf()` with `printBackground: true`, `format: 'A4'`
- Estimated generation time: 5–15 seconds per report
- Estimated file size: 2–8 MB depending on issue count and charts

**Deployment note for Vercel:** Puppeteer requires a Chromium binary exceeding Vercel's function size limits and the 60-second execution timeout is tight for larger scans. Use a dedicated server (Railway, VPS) instead.

### Step 5: Delivery (Resend)

**Technology:** Resend (preferred over SendGrid)

**Why Resend:**
- Permanent free tier: 100,000 emails/month — more than sufficient for MVP and early growth
- SendGrid eliminated its free tier in 2025 (now 60-day trial only)
- Resend has a clean Node.js SDK, excellent deliverability, and supports email templates

**Delivery flow:**
1. Scan completes → PDF generated → stored to local filesystem or S3-compatible storage
2. Resend sends email with:
   - Plain-text summary (violation count, critical issues, overall score)
   - PDF report attached (or download link if >10 MB)
   - Link to online interactive report (Phase 2 feature)

---

## 2. Tool Evaluation

### axe-core

**Strengths:**
- Industry standard — used by Google, Microsoft, the BBC, and GOV.UK
- Zero false positive philosophy: only flags confirmed violations
- 400,000+ weekly active users of axe DevTools browser extension
- Official `@axe-core/playwright` package maintained by Deque
- Covers WCAG 2.0, 2.1, 2.2 at levels A, AA, and AAA
- ACT (Accessibility Conformance Testing) rules implemented — W3C standardized

**Coverage:** ~57% of WCAG issues by volume (real-world issues found, not just rule count)

**Weaknesses:**
- 43% of issues require manual testing (AT testing, cognitive, timing)
- `incomplete` items require human review — can't be auto-resolved
- WCAG 2.2 `target-size` rule is unreliable (exists but flagged)
- Focus Appearance and Focus Not Obscured require axe DevTools Pro (paid)

### Pa11y

**Comparison to axe-core:**
| Factor | axe-core | Pa11y |
|---|---|---|
| Issue detection rate | ~57% | ~35% (standalone) |
| False positives | Very low (<8%) | Low |
| Incomplete/needs-review items | Yes (surfaced) | No (binary pass/fail only) |
| Underlying engine | axe-core | HTML_CodeSniffer + optional axe |
| Integration complexity | High (programmatic API) | Low (CLI-first) |
| CI/CD fit | Excellent | Excellent (pa11y-ci) |
| Overlap with axe-core | ~70–80% same issues | Some unique catches |

**Key finding from UK DWP testing:** axe-core found 39 issues (27%) and Pa11y found 29 issues (20%) on a benchmark page. Combined they found ~35%, not 47% — meaning overlap is substantial. Running both adds marginal coverage gain but significant complexity and cost.

**Recommendation:** Use axe-core as primary scanner. Optionally add Pa11y as a secondary pass for the unique ~5–8% of issues it catches that axe misses. Pa11y is CLI-friendly and could be added as a post-processing step without architectural changes.

### Lighthouse Accessibility Score

**Relationship to axe-core:** Lighthouse uses axe-core internally but runs only a subset of axe's rules — approximately 30% fewer checks than running axe-core directly.

**Verdict: Redundant, not complementary.** Lighthouse's accessibility score is a useful marketing metric (clients understand it) but technically it provides less coverage than running axe-core directly. Do not use Lighthouse as a primary scanner.

**One valid use:** Include the Lighthouse accessibility score in the report alongside the axe-core results as a familiar benchmark metric for clients. Generate it via `lighthouse` npm package or Chrome's built-in audit, report the score, but base the actual violation findings on axe-core output.

### IBM Equal Access Accessibility Checker

**Strengths:**
- Competitive with axe DevTools in coverage
- Tests WCAG 2.1 Level A, AA, and WAI-ARIA 1.2
- W3C ACT implementations published (verifiable coverage)
- Good for production-deployed page testing

**Weaknesses:**
- Less ecosystem adoption than axe-core
- Fewer integrations with CI/CD tools
- Community smaller than Deque's

**Verdict:** IBM Equal Access is a credible axe-core alternative, not an addition. Its complementary coverage is modest. For a Node.js stack targeting developer clients, axe-core has a stronger ecosystem. IBM Equal Access is worth evaluating for a Phase 2 dual-scanner approach to increase coverage toward 65–70%.

---

## 3. Report Structure Design

### Section 1: Executive Summary (1 page)

```
Overall Compliance Score:        62 / 100
WCAG 2.1 Level AA Status:        NON-CONFORMANT
Pages Scanned:                   24
Total Violations Found:          87
  Critical:                      12
  Serious:                       31
  Moderate:                      28
  Minor:                         16
Needs Manual Review:             14 items

Top 3 Issues Requiring Immediate Action:
1. [Critical] Color contrast failures — affects 18 pages, impacts visually impaired users
2. [Critical] Missing image alt text — affects 9 pages, impacts blind/low-vision users
3. [Serious] Form inputs without labels — affects 4 pages, impacts screen reader users
```

### Section 2: Issue-by-Issue Breakdown

Each violation entry contains:
- **Rule ID** — e.g., `color-contrast` (links to Deque University)
- **WCAG Criterion** — e.g., 1.4.3 Contrast (Minimum)
- **Impact Level** — Critical / Serious / Moderate / Minor
- **User impact** — plain English (e.g., "Users with low vision cannot read this text")
- **Pages affected** — list of URLs where this violation appears
- **Element** — CSS selector + HTML snippet of the failing element
- **How to fix** — specific code-level remediation with before/after example
- **Effort estimate** — Low / Medium / High

### Section 3: Priority Matrix

Four-quadrant matrix: Impact (user harm) vs. Effort (remediation cost)

```
              LOW EFFORT          HIGH EFFORT
HIGH IMPACT   [Fix Now]           [Plan Sprint]
LOW IMPACT    [Quick Wins]        [Backlog]
```

All violations mapped into this matrix. Critical + Low Effort items surfaced as "Fix First" list.

### Section 4: Remediation Guide

Grouped by violation type (not by page). For each type:
- What the rule requires (plain English)
- Why it matters (user story format: "As a blind user, I cannot...")
- Code example: broken HTML
- Code example: fixed HTML
- Testing tip: how to verify the fix manually

### Section 5: Compliance Status

WCAG 2.1 criterion-by-criterion status table:

```
Criterion    Description                    Level  Status
1.1.1        Non-text Content               A      FAIL (9 violations)
1.3.1        Info and Relationships         A      PASS
1.4.3        Contrast (Minimum)             AA     FAIL (18 violations)
1.4.4        Resize Text                    AA     NEEDS REVIEW
2.1.1        Keyboard                       A      NEEDS REVIEW
...
```

Status values: PASS / FAIL / NEEDS REVIEW / NOT TESTED

---

## 4. Infrastructure Needs

### Can This Run on a Laptop?

Yes, for development and low-volume production (1–5 scans/day).

**Laptop constraints:**
- Playwright/Chromium uses 300–800 MB RAM per browser instance
- Concurrent scans will cause memory pressure on <16 GB RAM machines
- PDF generation via Puppeteer adds another 200–500 MB peak
- Long-running scans (100+ pages) may take 10–20 minutes and consume significant CPU

**For production use**, a dedicated server is required for reliability, background job processing, and concurrent scan support.

### Scan Time Estimates

Based on benchmarks: ~2–5 seconds per page (Playwright + axe-core, images blocked, single worker)

| Site Size | Estimated Scan Time | Notes |
|---|---|---|
| 10 pages | 20–50 seconds | Suitable for serverless (with caveats) |
| 50 pages | 2–4 minutes | Requires background job queue |
| 100 pages | 4–8 minutes | Requires long-running worker process |
| 200 pages | 8–16 minutes | Needs dedicated worker, not serverless |

Add 30–60 seconds for Claude API analysis passes and 10–30 seconds for PDF generation.

**Total end-to-end for a 20-page site:** approximately 3–5 minutes

### Claude API Cost per Scan

| Site Size | Tokens (est.) | Haiku 4.5 | Sonnet 4.6 | Hybrid (rec.) |
|---|---|---|---|---|
| 10 pages | ~35K tokens | $0.05 | $0.15 | $0.07 |
| 20 pages | ~67K tokens | $0.09 | $0.28 | $0.12 |
| 50 pages | ~160K tokens | $0.22 | $0.67 | $0.28 |
| 100 pages | ~310K tokens | $0.42 | $1.30 | $0.55 |

**Hybrid strategy:** Use Haiku 4.5 for per-page violation analysis, Sonnet 4.6 only for the executive summary and remediation guide generation. This achieves 80% of Sonnet quality at 40% of the cost.

**Batch API discount:** For async scans (not instant delivery), the Batch API cuts costs by 50%, reducing a 50-page scan to ~$0.14.

### Hosting Options and Costs

| Option | Cost | Suitability | Notes |
|---|---|---|---|
| **Local machine** | $0 | Dev/demo only | Memory constraints, no uptime guarantee |
| **Vercel** | $0–$20/mo | Not recommended | 60-sec function timeout too short for scans; Chromium binary size exceeds limits |
| **Railway Hobby** | $5/mo (includes $5 credit) | MVP | Pay-per-use, auto-sleep; good for low volume |
| **Railway Pro** | ~$20–40/mo | Growth | Persistent workers, no sleep, multiple services |
| **Fly.io** | ~$5–15/mo | MVP alternative | Good for Dockerized Node.js + Playwright |
| **Hetzner VPS (CX22)** | ~$4/mo | Production | 2 vCPU, 4 GB RAM, no auto-scaling; manual ops |
| **DigitalOcean Basic Droplet** | $12/mo | Production | 2 vCPU, 2 GB RAM (4 GB recommended for Playwright) |

**Recommended MVP hosting:** Railway Hobby plan ($5/mo). Supports Node.js workers, Docker containers, background job queues. As volume grows, scale to Railway Pro or migrate to a dedicated VPS.

**RAM requirement:** Minimum 2 GB RAM for single concurrent scan with Playwright + Puppeteer. Recommended: 4 GB for comfort margin.

---

## 5. MVP Scope — Minimum to Deliver First Paid Audit

### MVP Feature Set

The smallest feature set that is sellable:

1. **Single URL input** — accept one domain, discover up to 25 pages via sitemap + crawl
2. **axe-core scan** — run against all discovered pages, collect violations
3. **Claude analysis** — deduplicate findings, write plain-English summaries, prioritize
4. **PDF report** — generate a professional-looking PDF with executive summary + violation list
5. **Email delivery** — send PDF to client's email via Resend
6. **Manual trigger** — no web UI required; operator runs a CLI script with `node scan.js --url https://example.com --email client@example.com`

### What Is Explicitly Out of Scope for MVP

- Web frontend / dashboard
- Payment processing / self-serve ordering
- Real-time progress updates
- Interactive online report (HTML version)
- White-label branding
- Scheduled recurring scans
- Pa11y secondary scanner
- API access for clients

### MVP Technical Stack

```
Node.js 20+
├── crawlee (Playwright crawler)
├── @axe-core/playwright (scanner)
├── @anthropic-ai/sdk (Claude API)
├── puppeteer (PDF generation, reuse Playwright's Chromium)
├── resend (email delivery)
└── CLI entry point: scan.js
```

Single file output: `report-{domain}-{date}.pdf`

### Estimated Build Time

| Component | Estimated Time |
|---|---|
| Crawler (Playwright + Crawlee setup) | 1–2 days |
| Scanner (axe-core integration + data normalization) | 1 day |
| Claude analysis prompts + aggregation logic | 2–3 days |
| Report HTML template | 2–3 days |
| PDF generation (Puppeteer) | 0.5 days |
| Email delivery (Resend) | 0.5 days |
| CLI wiring + error handling | 1 day |
| Testing on 3–5 real client sites + polish | 2–3 days |
| **Total** | **10–14 days (2–3 weeks)** |

### Dependencies and Risks

| Risk | Likelihood | Mitigation |
|---|---|---|
| Client site uses heavy SPA — crawl misses pages | Medium | Add manual URL list as override input |
| Playwright blocked by anti-bot protection (Cloudflare, etc.) | Medium | Use user-agent spoofing; offer manual page list as fallback |
| Claude API rate limits under burst load | Low (MVP volume) | Implement exponential backoff + retry |
| PDF generation memory spikes crash worker | Medium | Set Puppeteer memory limits; generate PDF in isolated subprocess |
| axe-core incomplete items mislead client | Medium | Clear labeling: "Automated scan — 43% of issues require manual review" |
| Report perceived as legal compliance certification | High risk | Explicit disclaimer in report: "This report is a technical scan, not a legal compliance certification" |

---

## 6. Scalability Considerations

### Throughput Analysis

**Single worker, single concurrent scan:**

| Scans per day | Pages/scan avg | Daily scan time | Feasibility |
|---|---|---|---|
| 5 | 20 | ~25 min total | Easy on single VPS |
| 10 | 20 | ~50 min total | Comfortable on single VPS |
| 50 | 20 | ~4 hours total | Needs job queue + multiple workers |
| 100 | 20 | ~8 hours total | Needs 3–4 parallel workers |

### Bottlenecks

1. **Scan time** (primary bottleneck): Playwright + Chromium is single-threaded per browser context. Parallelization requires launching multiple browser instances, each consuming 300–800 MB RAM. At 4 GB RAM, you can safely run 3–4 concurrent scans.

2. **Claude API rate limits** (secondary bottleneck): Tier 1 limits are 50 requests/minute and 40,000 tokens/minute for Haiku. For 10 concurrent scans each making 20 API calls, this could hit limits. Use Batch API for non-urgent scans. Upgrade to Tier 2 ($100 spend) to increase limits.

3. **PDF generation** (minor bottleneck): Puppeteer PDF generation is CPU-intensive. At 15 seconds/report, 10 concurrent reports = 2.5 minutes of CPU. Manageable. For 100/day, offload to a separate worker.

4. **Email delivery** (not a bottleneck): Resend free tier handles 100,000 emails/month with reliable queuing.

### Scaling Architecture

**Phase 1 (MVP, 1–10 scans/day):**
```
CLI script → Sequential scans → Single Chromium instance → Resend delivery
```

**Phase 2 (10–50 scans/day):**
```
Web UI → Job Queue (BullMQ + Redis) → Worker pool (2–3 workers)
         → Each worker: own Chromium instance → S3 PDF storage → Resend
```

**Phase 3 (50–200 scans/day):**
```
API → Queue → Kubernetes workers (auto-scale on queue depth)
     → PDF stored in S3 → CDN download links → Resend
```

### Automation Level Achievable

At MVP:
- Fully automated scan execution
- Fully automated report generation
- Fully automated email delivery
- Manual: customer intake (email/form), manual CLI invocation

At Phase 2 (web frontend + payment):
- Fully automated end-to-end (URL in → PDF report in inbox)
- Human review only for QA sampling (optional, not required)

---

## 7. Architecture Decision Summary

| Decision | Choice | Rationale |
|---|---|---|
| Crawler | Playwright + Crawlee | Handles JS-rendered sites; Crawlee adds queue/dedup |
| Scanner | axe-core (@axe-core/playwright) | Industry standard, zero false positives, best coverage |
| Secondary scanner | Pa11y (Phase 2) | Adds ~5–8% coverage; not worth MVP complexity |
| AI analyzer | Claude Haiku 4.5 + Sonnet 4.6 hybrid | Cost/quality balance; Haiku for per-page, Sonnet for summary |
| PDF generator | Puppeteer | Same Chromium binary as scanner; no extra runtime |
| Email delivery | Resend | Permanent free tier (100K/mo), clean SDK |
| MVP hosting | Railway Hobby ($5/mo) | Lowest-friction production deployment |
| Production hosting | Railway Pro / Hetzner VPS | Full process control, persistent workers |
| Report format | PDF (MVP) + HTML (Phase 2) | PDF is deliverable clients expect; HTML enables interactivity |

---

## 8. Honest Scope of What This Delivers

This system delivers a **Level 1 accessibility scan** — the automated foundation of a full accessibility audit. It is highly valuable to clients who have never done any accessibility testing. It is not a replacement for:

- Manual testing with a keyboard
- Testing with actual screen readers (NVDA, JAWS, VoiceOver)
- User testing with people with disabilities
- Legal compliance certification

The appropriate market positioning is:
- "Automated WCAG scan with AI-prioritized remediation guide"
- Price point: $150–$500 per scan (vs. $1,250–$2,750 for a manual audit, $5,000–$50,000 for a full professional audit)
- Value proposition: Identifies the ~57% of issues that can be found automatically, with Claude-generated remediation guidance that a developer can act on immediately

This makes it a legitimate entry-level offering in the $1.2B accessibility compliance market, with a clear upsell path to manual review add-ons and recurring monitoring subscriptions.

---

*Sources: Deque automated testing coverage research; DWP Accessibility Manual axe-core/Pa11y comparison; Playwright performance benchmarks; Anthropic API pricing documentation; Railway pricing documentation; Resend pricing; market pricing research from accessible.org and testparty.ai*
