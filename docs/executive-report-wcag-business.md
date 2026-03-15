# Executive Report: AI-Powered WCAG Accessibility Audit Business

**Date:** March 15, 2026
**Classification:** GO/NO-GO Decision Document
**Author:** CEO

---

## 1. Executive Summary

**RECOMMENDATION: CONDITIONAL GO.** The data supports launching an AI-powered WCAG accessibility scan business targeting SMBs at $99-$499 per report. The market is real ($2.59B TAM, $364M reachable SAM), the pricing gap is structural ($200-$500 vs. $1,250+ agencies), COGS is near-zero ($0.18/audit), and legal tailwinds are accelerating (ADA lawsuits up 37% YoY, EAA enforcement live, HHS healthcare deadline May 2026). However, this is a GO with non-negotiable conditions: the product must be positioned as an "automated accessibility scan" — never a "full audit" — with transparent disclaimers about the 57% detection ceiling, E&O insurance must be purchased within 30 days of first revenue, and the business must pivot to recurring monitoring revenue within 60 days to avoid the one-time-report treadmill. Without these conditions, the legal and reputational risks are business-ending.

---

## 2. The Business

### What We Sell

We sell professional WCAG accessibility scan reports to small and mid-size businesses. A business owner gives us their website URL. We deliver a branded PDF report that tells them exactly what accessibility problems their site has, why each problem creates legal risk under the ADA or European Accessibility Act, and how their developers should fix each issue — prioritized by severity.

Plain English: we translate robot output into a document a business owner can hand to their lawyer or web developer and say "fix this."

### How AI Does 100% of the Work

The pipeline is fully automated:

1. **Crawl** — Playwright discovers all pages on the client's website via sitemap + link-following
2. **Scan** — axe-core (the industry-standard accessibility engine used by Google, Microsoft, and the BBC) tests every page against WCAG 2.2 AA criteria
3. **Analyze** — Claude API deduplicates findings, writes plain-English explanations, generates code-level fix instructions, and produces a prioritized remediation roadmap
4. **Generate** — Puppeteer renders a professional PDF report with executive summary, issue-by-issue breakdown, priority matrix, and compliance status table
5. **Deliver** — Resend emails the report to the client

Human involvement: zero for report generation. The operator's time goes to sales, quality sampling, and client communication.

### Why Now

Three legal forces are converging simultaneously:

- **ADA lawsuits surged 37% in H1 2025** — 2,014 federal suits filed in six months; 4,500-5,000 projected for the full year. 77% target ecommerce. The majority of defendants have under $25M revenue. These are Main Street businesses, not Fortune 500.
- **European Accessibility Act (EAA) enforcement began June 28, 2025** — Penalties up to EUR 100,000 or 4% of annual revenue. Applies to any business (including US-based) selling to EU consumers. First enforcement actions filed within days of the deadline.
- **HHS healthcare rule imposes WCAG 2.1 AA compliance by May 2026** — Affects every healthcare organization accepting Medicare or Medicaid. Non-compliance jeopardizes federal program eligibility.

Meanwhile, the FTC fined accessiBe $1 million in January 2025 for falsely claiming AI overlays ensure WCAG compliance — destroying trust in the "widget" approach and redirecting demand toward legitimate audit reports. And 94.8% of the top 1 million websites still have detectable WCAG failures (WebAIM Million 2025).

The window is 12-18 months before incumbents launch downmarket "lite" tiers.

---

## 3. Market Opportunity

### TAM / SAM / SOM

| Metric | Value | Basis |
|--------|-------|-------|
| **TAM** | **$2.59B/year** | Global active business websites needing accessibility audits at any price point |
| **SAM** | **$364M/year** | English-speaking SMBs + regulated industries + EU-affected businesses, $500-$1,500/audit |
| **SOM (Year 1)** | **$180K-$540K** | Solo operator, 60-180 clients at $1,500-$3,000 avg |

### ADA Lawsuit Trends

| Year | Total Lawsuits | YoY Change |
|------|---------------|------------|
| 2022 | ~3,787 | — |
| 2023 | ~4,061 | +7.2% |
| 2024 | ~4,052 | -0.2% |
| 2025 (proj.) | ~4,500-5,000 | +12-23% |

- 188 serial plaintiffs drove all 2,014 H1 2025 lawsuits
- Illinois surged 745% (28 to 237 cases); Florida nearly doubled
- 22.6% of H1 2025 lawsuits targeted sites with accessibility overlay widgets installed — overlays are not a legal shield
- For every lawsuit filed, an estimated 100+ demand letters are sent (settled at $5K-$25K each)

### EAA Impact

- 4 million EU SMEs in scope (micro-enterprises exempted)
- US, UK, and AU companies with EU customers must also comply
- First enforcement actions filed within days of the June 28, 2025 deadline
- Creates a net-new demand wave independent of US ADA trends

### Key Data Points

- 94.8% of top 1M websites fail basic WCAG compliance (WebAIM Million 2025)
- Average non-compliant page has 51 distinct accessibility errors
- Digital accessibility market growing at 8.6-9.6% CAGR
- Typical ADA settlement: $25,000-$75,000 plus $15,000-$50,000 in legal fees
- Our audit price: $299. The math sells itself.

---

## 4. Competitive Advantage

### The Pricing Gap We Fill

```
FREE           $200-$500          $1,250+           $15,000+
|                |                   |                  |
axe/WAVE/      ★ OUR ZONE ★      Agency manual      Enterprise
Lighthouse      AI scan +          audits             SaaS platforms
(raw data)      narrative report   (2-6 week          (Siteimprove,
                                   delivery)          Level Access)
```

The market has a structural hole between free tools (which produce raw JSON no business owner can interpret) and agency audits (which start at $1,250 and take 2-6 weeks). We fill it with an AI-narrated professional report delivered in minutes for $199-$499.

### Why Incumbents Can't/Won't Compete Here

- **Agencies won't automate** because it destroys their labor billing model (30% automated + 70% manual methodology)
- **Enterprise SaaS won't sell one-time reports** because it destroys their $15K-$63K/year recurring contract model (Siteimprove avg contract: $28K/year)
- **Overlay vendors are discredited** — FTC fined accessiBe $1M; 22.6% of lawsuits target sites with overlays installed
- **Free tools don't produce deliverables** — axe-core outputs JSON, not a PDF you can hand to a lawyer

This is a structural gap, not an oversight. Incumbents have the technology but the wrong business model incentives to serve this segment.

### Our 1 Direct Competitor

**The Audit Base** (theauditbase.com) — $199 scan report (up to 50 pages), $999 scan + remediation plan. Uses the same stack (axe-core + Playwright). Delivers in 10 minutes. Targets government/healthcare.

**How we differentiate:**
- Richer AI narrative quality (business-language recommendations, not just WCAG codes)
- Free preview scan as lead magnet (they require full payment upfront)
- SMB-friendly positioning (they skew government/bureaucratic)
- Agency partnership channel (white-label option, 25% referral commissions)

**AccessGlance** ($29/report) is a secondary competitor but positioned as a cheap utility, not a professional compliance service.

### The Narration Gap

This is the core thesis: every existing tool produces data. None produce a document a non-technical business owner can act on. The gap is not in scanning — it is in translating findings into plain-English explanations, legal-risk context, prioritized remediation steps, and a professional PDF that can be forwarded to a lawyer, board, or web developer. AI closes this narration gap at near-zero marginal cost.

---

## 5. Unit Economics

### COGS Per Audit

| Cost Item | Basic ($99) | Standard ($299) | Premium ($499/mo) |
|-----------|------------|----------------|-------------------|
| Claude API (Haiku 4.5 Batch) | $0.01 | $0.06 | $0.02/re-run |
| Compute (VPS) | $0.10 | $0.10 | $0.10 |
| PDF generation | $0.00 | $0.00 | $0.00 |
| Email delivery | $0.00 | $0.00 | $0.00 |
| Domain amortized | $0.02 | $0.02 | $0.02 |
| **Total COGS** | **$0.13** | **$0.18** | **$0.14/re-run** |

COGS is near-zero because axe-core is free, Claude Haiku Batch API is extremely cheap for structured output, and PDF generation uses the same Chromium binary as the scanner.

### Pricing Tiers

| Tier | Price | Scope | Role |
|------|-------|-------|------|
| Basic | $99 one-time | Single page, WCAG 2.2 AA scan + AI narrative | Entry point, lead capture |
| Standard | $299 one-time | Full site up to 50 pages, executive summary, remediation roadmap | Core revenue driver |
| Premium | $499/month | Full site + monthly re-audit + delta report + compliance certificate | Recurring revenue engine |

Blended average revenue per customer at target mix (30/40/30): **$299/customer**

### Gross Margin

| Tier | Price | COGS | Gross Margin |
|------|-------|------|-------------|
| Basic | $99 | $0.13 | **99.9%** |
| Standard | $299 | $0.18 | **99.9%** |
| Premium | $499/mo | ~$10.56/mo | **97.8%** |

### CAC and LTV

| Metric | Value |
|--------|-------|
| Cash CAC (blended) | **~$30** |
| LTV (one-time customers) | **$239** |
| LTV (Premium subscribers, 20-month avg lifespan) | **$9,980** |
| Blended LTV (30/40/30 mix) | **$3,161** |
| **LTV:CAC ratio** | **105:1** |
| Payback period | **< 1 month (all tiers)** |

Target: >3:1 LTV:CAC is "good." We are at 105:1. The constraint is not economics — it is sales volume.

### Break-Even Analysis

- Monthly fixed costs at launch: **$42** (VPS $5 + email tool $37)
- Break-even: **0.14 Standard audits/month** — selling 1 audit covers all costs
- Break-even including $50/hr implicit labor cost: **8 Standard audits/month**
- **The business is cash-flow positive from the first sale.**

---

## 6. Customer Acquisition Plan

### Who Buys and Why

**Primary buyer:** Legal/Compliance officer or CTO at a mid-size company (50-500 employees) that has received an ADA demand letter or is preparing an RFP response requiring a WCAG conformance statement.

**Secondary buyer:** Agency owner who sells web services and wants to add accessibility audits as a line item for every client engagement.

**Highest-conversion segments (ranked):**

1. **Ecommerce (50-500 employees)** — 77% of all ADA web lawsuits target ecommerce
2. **Healthcare accepting federal funding** — HHS May 2026 deadline
3. **SaaS selling to government/enterprise** — VPAT required for procurement
4. **Government contractors** — ADA Title II mandate

**Target geographies:** New York (637 H1 lawsuits), Florida (487), California (~400), Illinois (237 — up 745%)

### The Scan-First Outreach Model

This is the key differentiator vs. generic cold email:

1. Build target list by industry + geography + company size
2. Run automated axe-core scan on their homepage + 2-3 key pages (200-500 URLs/hour)
3. Extract top 3-5 critical violations with annotated screenshots
4. Send personalized outreach with their specific findings as proof
5. Offer: full audit + remediation roadmap for $200-$500

This is not a pitch — it is a wake-up call. The prospect's first interaction is a free mini-audit that proves the problem exists. Loss aversion + reciprocity psychology activate simultaneously.

### Channel Strategy

| Channel | Reply Rate | Conversion | Revenue Role |
|---------|-----------|-----------|-------------|
| Cold email with mini-audit proof | 8-15% | 10-20% of replies | Primary volume driver |
| LinkedIn DM (connection + follow-up) | 10-15% | 15-25% of replies | Mid-market/enterprise |
| Agency partnerships (referrals) | N/A (warm) | 40-60% | Highest LTV channel |
| Fiverr/Upwork | Inbound | 20-35% | Credibility building |
| Reddit/forums | 5-10% | 10-20% | Community trust |
| SEO/content | Low (6-12mo) | High long-term | Compounding moat |

### Volume Math and Conversion Projections

**Month 1 (full ramp):**

| Channel | Monthly Outreach | Replies | Paid Conversions | Revenue |
|---------|-----------------|---------|-----------------|---------|
| Cold email (75/day x 22 days) | 1,650 | 132 (8%) | 20 (15%) | $6,000 |
| LinkedIn (15 DMs/day x 22 days) | 330 | 40 (12%) | 8 (20%) | $2,400 |
| Fiverr/Upwork (inbound) | — | — | 3-5 | $900-$1,500 |
| **Month 1 Total** | | | **31-33** | **$9,300-$9,900** |

**Sensitivity analysis:**

| Scenario | Reply Rate | Conversion | Monthly Revenue |
|----------|-----------|-----------|----------------|
| Pessimistic | 4% | 10% | ~$3,500 |
| Base case | 8% | 15% | ~$9,500 |
| Optimistic | 12% | 20% | ~$18,000 |
| With agency channel (Month 3) | 8% + referrals | 15%/40% | ~$14,000-$17,000 |

**Month 6 projection:** $13,465/month ($161,580 ARR run rate) with 15 Premium subscribers providing $7,485 MRR base.

---

## 7. Technical Architecture

### Pipeline: URL to Scan to Analyze to Report to Deliver

```
URL Input → Crawl (Playwright + Crawlee)
         → Scan (axe-core via @axe-core/playwright)
         → Analyze (Claude Haiku 4.5 per-page + Sonnet 4.6 summary)
         → Generate Report (Puppeteer PDF)
         → Deliver (Resend email)
```

**End-to-end for a 20-page site:** approximately 3-5 minutes

### Tools

| Component | Technology | Cost |
|-----------|-----------|------|
| Crawler | Playwright + Crawlee | Free (open source) |
| Scanner | @axe-core/playwright | Free (open source, industry standard) |
| AI Analysis | Claude Haiku 4.5 (per-page) + Sonnet 4.6 (summary) | ~$0.06-$0.12/scan |
| PDF Generation | Puppeteer (reuses Playwright's Chromium) | Free |
| Email Delivery | Resend (100K emails/month free tier) | Free |
| Hosting | Hetzner CX22 VPS (2 vCPU, 4GB RAM) | $5/month |

### MVP Scope

**In scope (sellable minimum):**
1. Single URL input — discover up to 25 pages via sitemap + crawl
2. axe-core scan against all discovered pages
3. Claude analysis — deduplicate, summarize, prioritize
4. Professional PDF report with executive summary + violation list + remediation guide
5. Email delivery via Resend
6. CLI trigger: `node scan.js --url https://example.com --email client@example.com`

**Out of scope for MVP:** Web frontend, payment processing, real-time progress, interactive HTML report, white-label branding, scheduled scans, API access.

### Build Timeline

| Component | Time |
|-----------|------|
| Crawler setup | 1-2 days |
| Scanner integration | 1 day |
| Claude analysis prompts + aggregation | 2-3 days |
| Report HTML template | 2-3 days |
| PDF generation + email delivery | 1 day |
| CLI wiring + error handling | 1 day |
| Testing on real sites + polish | 2-3 days |
| **Total** | **10-14 days** |

### Infrastructure Costs

| Item | Monthly Cost |
|------|-------------|
| Hetzner VPS | $5 |
| Domain | $1 (amortized) |
| Claude API (at 50 scans/month) | $3-$6 |
| Resend | $0 (free tier) |
| **Total** | **~$10/month** |

First paying customer covers 14+ months of infrastructure.

---

## 8. 5-Day Execution Plan

**Total budget: $100**

### Day 1: Build + Prospect ($12 spend)

| Time | Action | Outcome |
|------|--------|---------|
| 8:00-9:45 AM | Set up scanning workflow (axe DevTools, WAVE, Lighthouse) + build report template | MVP toolchain operational |
| 9:45-11:15 AM | Build cold email template + outreach tracking sheet (Google Sheets + Streak CRM) | Sales infrastructure ready |
| 11:15-12:00 PM | Set up Stripe payment links + publish Fiverr gig | Payment collection live |
| 12:00-3:00 PM | Build prospect list: 50 ecommerce businesses in NY, FL, CA, IL | 50 targets identified |
| 3:00-6:00 PM | Scan all 50 sites, find email addresses (Hunter.io), prepare personalized messages | 50 sites scanned, 30 emails found, outreach drafted |

**Budget:** Domain registration $12. **Revenue:** $0 (build day).

### Day 2: Outreach Blitz ($37 spend)

| Time | Action | Outcome |
|------|--------|---------|
| 8:00-9:30 AM | Send 50 cold emails with mini-audit findings + annotated screenshots | 50 personalized emails sent |
| 9:30-10:30 AM | Send 30 LinkedIn DMs with scan screenshots | 30 DMs sent |
| 10:30-12:00 PM | Post Fiverr/Upwork gigs + Reddit value posts (r/ecommerce, r/smallbusiness) | Marketplace presence live |
| 12:00-4:00 PM | Scan 25 more websites, send second batch of 25 emails | 75 total emails sent |
| 4:00-6:00 PM | Monitor responses, reply within 30 minutes, book Calendly calls | 3-5 "interested" replies |

**Budget:** Email tool $25. **Revenue target:** $0-$200 (first replies arriving).

### Day 3: Follow-Up + First Deliveries ($0 spend)

| Time | Action | Outcome |
|------|--------|---------|
| 8:00-9:30 AM | Follow up on Day 2 non-responders (email + LinkedIn) | Second touchpoint on 80 prospects |
| 9:30-12:00 PM | New outreach batch: 50 prospects in different industry/city | 125 total prospects contacted |
| 12:00-3:00 PM | Deliver any paid audits (full scan + report) | First revenue collected |
| 3:00-5:00 PM | Conduct booked discovery calls (screen-share live WAVE scan) | 1-2 deals closed |
| 5:00-6:00 PM | Ask first clients for referrals (20% referral fee) | Referral pipeline seeded |

**Revenue target:** $200-$600

### Day 4: Scale Outreach + Deliver ($0 spend)

| Time | Action | Outcome |
|------|--------|---------|
| 8:00-12:00 PM | Third outreach batch (25 new prospects) + LinkedIn connects | 150 total prospects |
| 12:00-3:00 PM | Deliver outstanding audits | Reports delivered, payments collected |
| 3:00-5:00 PM | Second follow-up on Day 2-3 non-responders (final touch) | Urgency messaging: "closing books this week" |
| 5:00-6:00 PM | Upsell first clients: quarterly re-audit retainer ($97/quarter) | Recurring revenue seeds |

**Revenue target:** $600-$900

### Day 5: Close + Collect ($0 spend)

| Time | Action | Outcome |
|------|--------|---------|
| 8:00-10:30 AM | Phone call blitz to all warm leads who haven't paid | Direct closing pressure |
| 10:30-12:00 PM | Send invoices, follow up 1 hour after sending | Payments collected |
| 12:00-3:00 PM | Complete and deliver remaining audits | All commitments fulfilled |
| 3:00-4:00 PM | Confirm all payments received, chase unpaid invoices by phone | Cash in hand |
| 4:00-5:00 PM | Document learnings: best industry, best subject line, best objection handle | Optimization data for Week 2 |

**Revenue target:** $1,000+ cumulative

### Budget Allocation

| Item | Amount |
|------|--------|
| Domain registration | $12 |
| Email outreach tool (1 month) | $25 |
| Claude API credits | $20 |
| Hetzner VPS (2 months) | $10 |
| Reserve/contingency | $33 |
| **Total** | **$100** |

### Revenue Targets by Day

| Day | Cumulative Target | Minimum | Contingency |
|-----|------------------|---------|-------------|
| Day 1 | $0 | $0 | Extend scanning into evening |
| Day 2 | $0-$200 | $0 | Shift to aggressive LinkedIn |
| Day 3 | $200-$600 | $200 | Add new industry vertical |
| Day 4 | $600-$900 | $400 | Call (don't email) all warm leads |
| Day 5 | $1,000+ | $1,000 | "Closing my books today" urgency |

---

## 9. Risk Matrix

### Top 5 Critical Risks

| # | Risk | Likelihood | Impact | Mitigation |
|---|------|-----------|--------|------------|
| 1 | **57% detection ceiling misrepresented as "full audit"** | High | Fatal | Never call it an "audit." Call it an "Automated Accessibility Scan." Disclose limitation on cover page of every report. Include "Issues automated tools cannot detect" section. |
| 2 | **No cold outreach replies** | High | High | Hyper-personalize every email with actual scan findings + annotated screenshots. Multi-channel (email + LinkedIn + phone). 5-touch sequence over 14 days. Free sample excerpt in first email. |
| 3 | **Cash flow collapse on $100 budget** | High | High | Revenue before spend. First client is the funding round. Free-tier stack until revenue justifies upgrades. First $299 sale covers 14+ months of infrastructure. |
| 4 | **Client gets sued after using our report** | Medium | High | Bulletproof disclaimers on sales page, engagement letter, report cover page, and executive summary. E&O insurance ($500-$1,500/yr) within 30 days of first revenue. LLC formation immediately. Cap liability at amount paid. |
| 5 | **Selling automated reports at human-audit prices** | High | High | Transparent pricing: $99-$499 for automated scan (clearly labeled). Never represent automated work as manual. Include AI disclosure statement in every report. |

### Legal Positioning: Scan vs. Audit

This distinction is non-negotiable:

- **We sell:** "Automated Accessibility Scan Reports" — programmatically detectable issues with AI-generated remediation guidance
- **We do NOT sell:** "WCAG Compliance Audits" or "ADA Compliance Certification"
- **Every report states:** "This automated analysis detects approximately 57% of potential WCAG 2.1 issues. It does not constitute a legal opinion, a complete manual audit, or a guarantee of ADA/Section 508/EAA compliance."
- **Marketing never uses:** "complete," "comprehensive," "guaranteed compliance," or "certified"

Scanning public websites is legal under *hiQ Labs v. LinkedIn* (9th Cir. 2022) and *Van Buren v. United States* (SCOTUS 2021). We access only publicly served HTML/CSS/JS — the same data any browser receives. No authentication bypassed, no private data extracted.

### Quality Management: The 57% Detection Rate

axe-core detects approximately 57% of WCAG issues by volume (Deque's own published figure). False positive rate is below 8% — what it flags is almost always real.

**What it catches:** Color contrast, missing alt text, unlabeled form inputs, empty buttons, heading order violations, ARIA errors, missing skip links, iframe titles.

**What it misses (43%):** Screen reader reading order, cognitive accessibility, focus trap detection, meaningful alt text quality, error recovery flows, timing/animation issues, custom widget behavior.

**How we handle this:**
- Report includes explicit "Limitations" section listing what requires manual review
- "Next Steps" section recommends manual expert audit for complete conformance
- Upsell path to partner manual auditors for full audits ($2,500-$5,000)
- Frame as: "We found 47 issues in 10 minutes. Imagine what a 20-hour manual audit reveals. Here's your starting point."

---

## 10. VC Stress Test — Hardest Questions and Our Answers

### Q1: axe-core catches 57% of issues. You're selling an incomplete product. Isn't that fraud?

**Our answer:** Only if we misrepresent it. We never call it a "full audit" or "WCAG certification." We call it an "automated accessibility scan with remediation guidance" — explicitly scoped to programmatically-detectable issues. The value is real: most businesses have zero awareness of their accessibility issues. Going from 0% to 57% knowledge with prioritized fixes is genuinely valuable. No agency provides a full audit for $300 either — their $1,250 entry products are also limited-scope.

**What we don't know:** Whether clients will be satisfied with 57% coverage once they understand the limitation, or whether this creates a "false security" reputation problem over time.

### Q2: What's the moat? If this works, what stops Siteimprove from offering the same thing at $99?

**Our answer:** There is no technical moat. Zero. The moat is structural incentives: Siteimprove won't sell a $99 report because it destroys their $28K/year enterprise ASP. Deque won't because they sell $40/month developer tools. Agencies won't because it destroys their labor model. We build defensibility through: (a) industry-specific report templates, (b) recurring monitoring subscriptions, (c) agency referral network, (d) proprietary vertical benchmarks ("your site is worse than 73% of restaurants in Florida").

**What we don't know:** How long the structural incentive gap holds. Window estimate: 12-18 months. We must build recurring revenue and client relationships before it closes.

### Q3: Is this a real business or a side hustle that caps at $5K/month?

**Our answer:** The one-time report is the wedge, not the product. The roadmap: (1) one-time reports ($200-$500) prove the market, (2) monthly monitoring ($49-$99/month) creates recurring revenue, (3) remediation partnerships generate referral fees, (4) annual re-certification captures regulatory change cycles, (5) white-label API serves agency channel at scale. 100 monitoring clients at $79/month = $7,900 MRR. This is a real business only if we convert to recurring within 60 days.

**What we don't know:** The actual conversion rate from one-time report buyers to monitoring subscribers. The model assumes 30%, but this is unvalidated.

### Q4: What happens when a client gets sued AFTER using your report?

**Our answer:** This is the nightmare scenario and requires structural protection: (1) bulletproof disclaimers in every report, engagement letter, and sales page — reviewed by an attorney, (2) E&O insurance ($500-$1,500/year) purchased within 30 days of first revenue, (3) product named "scan report" not "audit" or "certification," (4) contractual liability capped at amount paid, (5) LLC to separate personal assets. The report explicitly states it covers only automated-detectable issues and recommends manual review.

**What we don't know:** Whether any disclaimer language would survive a motivated plaintiff's attorney. The precedent for downstream liability from technical scan reports is thin.

### Q5: Your $100 starting budget is a red flag, not a feature.

**Our answer:** The $100 is for proof-of-concept only. Within 30 days of first revenue, we must invest: LLC formation ($50-$200), E&O insurance ($500-$1,500/year), legal review of disclaimers ($500-$1,000), professional email infrastructure ($30-$50/month). Total real startup cost: $1,200-$2,800. The first $1,000 in revenue goes straight back into the business. The $100 buys: domain ($12), email tool ($25), Claude API credits ($20), VPS ($10), and $33 contingency.

**What we don't know:** Whether the first sale comes fast enough to fund the legal protections before exposure accumulates. The uninsured bootstrapping phase is the highest-risk window.

---

## 11. GO/NO-GO Decision

### Scorecard Summary

| Criteria | Score (1-10) | Notes |
|----------|-------------|-------|
| AI Autonomy | 9 | 100% automated pipeline; human needed only for sales |
| Demand Proof | 10 | 4,500+ lawsuits/year, EAA enforcement, HHS deadline |
| Price Point | 9 | $99-$499 fills a structural gap between $0 and $1,250+ |
| Speed to Revenue | 8 | 5-day target aggressive but achievable with scan-first outreach |
| Competition Gap | 10 | Narration gap is real; 1 direct competitor at similar price |
| $100 Budget Fit | 10 | Near-zero COGS; free-tier stack covers MVP |
| **TOTAL** | **56/60** | Top-scored candidate across all evaluated businesses |

### Clear Recommendation

**GO — with the following non-negotiable conditions:**

1. **Positioning discipline:** Product is an "Automated Accessibility Scan Report" — never a "full audit," "compliance certification," or "guaranteed ADA compliance." This is enforced in marketing copy, sales scripts, report templates, and disclaimers.

2. **Legal protection within 30 days of first revenue:** LLC formation, E&O insurance, attorney-reviewed disclaimer language. No exceptions. The first $1,200-$2,800 in revenue is reinvested into legal foundations.

3. **Recurring revenue pivot within 60 days:** Launch Premium monitoring tier ($499/month) or the business becomes an unsustainable one-time-report treadmill. Target: 30% of report buyers convert to monitoring.

4. **Transparency about AI and automation:** Every report discloses AI involvement, 57% detection ceiling, and manual testing recommendations. This is not optional — it is what separates us from accessiBe's $1M FTC fine.

### What Must Be True for This to Work

1. Cold outreach with personalized scan findings converts at 1-2%+ (industry data supports 1-5% for evidence-based campaigns)
2. SMB business owners will pay $200-$500 for a professional report they could theoretically generate themselves with free tools (proven by existing agency pricing and The Audit Base at $199)
3. The 12-18 month window before incumbents launch downmarket tiers is sufficient to build client base and recurring revenue
4. The 57% detection rate, honestly disclosed, is "good enough" for SMBs who currently have 0% visibility into their accessibility posture
5. ADA lawsuit volume and EAA enforcement continue or accelerate (all trend data supports this)

### First 3 Actions if GO

1. **Today:** Register domain, set up Hetzner VPS, configure axe-core + Playwright scanning pipeline, build report template with disclaimers
2. **Tomorrow:** Scan 50 target websites in high-lawsuit-risk industries (ecommerce in NY, FL, CA, IL), find email addresses, send first batch of personalized outreach with annotated screenshots
3. **Within 30 days of first revenue:** Form LLC, purchase E&O insurance, get attorney review of disclaimers — then launch Premium monitoring tier

---

*This report synthesizes findings from 9 research documents covering market sizing, competitive analysis, customer acquisition, unit economics, technical architecture, go-to-market playbook, risk analysis, VC stress testing, and cross-track scoring. All projections are based on cited sources with dates. The recommendation accounts for both the substantial opportunity and the material risks of operating in a compliance-adjacent market with an automated product.*
