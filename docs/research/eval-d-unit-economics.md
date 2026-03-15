# Unit Economics Model: AI-Powered WCAG Accessibility Audit Business

**Date:** 2026-03-15
**Status:** Pre-launch financial model
**Starting capital:** $100

---

## 1. Cost Per Audit (COGS)

### 1.1 Claude API Token Costs

A 20-page WCAG audit report is the most variable cost. Token estimates below are conservative (upper-bound for each line item).

| Component | Input Tokens | Output Tokens | Notes |
|-----------|-------------|--------------|-------|
| System prompt + audit instructions | 2,000 | — | Static, cache-eligible |
| axe-core violations JSON (50 pages) | 12,000 | — | ~240 tokens/page avg |
| Per-page HTML structure summary | 8,000 | — | Compressed representation |
| Remediation report generation | — | 18,000 | ~900 tokens/page of report |
| Executive summary | — | 1,500 | One-time per audit |
| **Total (Standard 50-page audit)** | **22,000** | **19,500** | |
| **Total (Basic 1-page scan)** | **3,000** | **2,500** | |
| **Total (Premium — same as Standard)** | **22,000** | **19,500** | Monitoring re-runs = ~30% of full audit |

**Model choice: Claude Haiku 4.5** (sufficient for structured accessibility analysis; 90% of Sonnet quality at 3x cost savings)

- Input: $1.00 / 1M tokens
- Output: $5.00 / 1M tokens
- **Batch API discount: 50% off** — use for all non-real-time jobs

| Audit Tier | Input Cost | Output Cost | **Total API Cost** |
|------------|-----------|------------|-------------------|
| Basic (1 page) | $0.0015 | $0.0063 | **$0.0078** |
| Standard (50 pages) | $0.0110 | $0.0488 | **$0.0598** |
| Premium re-run (monthly) | $0.0039 | $0.0171 | **$0.0210** |

> With prompt caching on the static system prompt (2,000 tokens), cache reads cost 0.1x, saving ~$0.001/audit — marginal but free to implement.

### 1.2 Compute Costs (Playwright + axe-core)

- Playwright + axe-core: **open source, $0 license cost**
- Runs on VPS: Hetzner CX22 — **€4.51/month (~$5/month)**
  - 2 vCPU, 4 GB RAM, 40 GB NVMe, 20 TB bandwidth
  - Can handle ~500 audits/month comfortably (crawl + scan is I/O-bound)
- Cost allocation per audit at 50 audits/month: $5 / 50 = **$0.10/audit**
- Cost allocation per audit at 200 audits/month: $5 / 200 = **$0.025/audit**

Use **$0.10/audit** as conservative baseline (low-volume months).

### 1.3 PDF Generation

- `weasyprint` or `puppeteer` PDF export: **$0 (open source)**
- Storage: ~2 MB per PDF on Hetzner volume (included in plan)
- Cost: **$0.00**

### 1.4 Email Delivery

- **Resend.com free tier**: 3,000 emails/month, 100/day — sufficient for early stage
- At scale: Resend Pro at $20/month for 50,000 emails = **$0.0004/email**
- Assume 3 emails per audit (confirmation, report delivery, follow-up)
- Cost at scale: 3 × $0.0004 = **$0.0012/audit** (effectively $0 in early stage)

### 1.5 Domain + SSL

- Domain: ~$12/year = **$1.00/month**
- SSL: Let's Encrypt = **$0**
- Amortized per audit at 50 audits/month: **$0.02/audit**

### 1.6 COGS Summary

| Cost Item | Basic ($99) | Standard ($299) | Premium ($499/mo) |
|-----------|------------|----------------|-------------------|
| Claude API (Haiku + Batch) | $0.01 | $0.06 | $0.02/re-run |
| Compute (VPS allocation) | $0.10 | $0.10 | $0.10 |
| PDF generation | $0.00 | $0.00 | $0.00 |
| Email delivery | $0.00 | $0.00 | $0.00 |
| Domain amortized | $0.02 | $0.02 | $0.02 |
| **Total COGS** | **$0.13** | **$0.18** | **$0.14/re-run** |

The COGS is remarkably low because:
1. axe-core does the heavy lifting (free, runs locally)
2. Claude Haiku Batch API is extremely cheap for structured output
3. PDF generation and email are effectively free at this scale

---

## 2. Pricing Strategy

### 2.1 Competitive Landscape

| Provider | Price | Notes |
|----------|-------|-------|
| Large accessibility agencies | $5,000–$15,000 | Manual expert audits, certifications |
| Mid-tier agencies | $1,250–$5,000 | Mixed manual/automated |
| Freelancers (Upwork/Fiverr) | $50–$500 | Mostly automated scans with thin narrative |
| Accessible.org | $100–$250/page | Full manual audit, expensive |
| AccessibilityChecker.org | Freemium + paid | Automated scanner, no narrative |
| accessiBe (monitoring widget) | $490–$3,990/year | Widget overlay, not an audit |
| UserWay (monitoring) | $49–$249/month | Widget + monitoring, not a report |

**Key insight:** The $299–$499 zone is largely unoccupied. Freelancers at $50–$500 deliver thin automated scans. Agencies at $1,250+ deliver expert manual audits. Our product occupies the "automated scan + AI-generated expert narrative + remediation roadmap" middle ground — dramatically more valuable than a raw scanner, dramatically cheaper than an agency.

### 2.2 Price Anchoring Strategy

**Landing page copy:**
> "Accessibility agencies charge $1,250–$5,000 for a WCAG audit. Freelancers charge $50–$500 but hand you a raw CSV. We deliver an agency-quality report with prioritized remediation steps — for $299."

This anchors against $1,250 (the floor of agency pricing), making $299 feel like an 76% discount without discounting from our own price.

### 2.3 Pricing Tiers

| Tier | Price | Scope | Positioning |
|------|-------|-------|-------------|
| **Basic** | $99 one-time | Single page, full WCAG 2.2 AA scan + AI narrative | Entry point, lead capture |
| **Standard** | $299 one-time | Full site up to 50 pages, executive summary, remediation roadmap | Core product |
| **Premium** | $499/month | Full site + monthly re-audit + delta report + compliance certificate | Recurring revenue engine |

**Upsell path:** Basic → Standard (mention during report delivery), Standard → Premium (offer 1st month free to convert).

### 2.4 One-Time vs. Recurring Revenue Mix

Target mix at Month 6:
- 30% Basic ($99) — top-of-funnel, high conversion cold outreach
- 40% Standard ($299) — primary revenue driver
- 30% Premium ($499/mo) — LTV maximizer

At this mix, blended revenue per new customer = (0.30 × $99) + (0.40 × $299) + (0.30 × $499) = **$29.70 + $119.60 + $149.70 = $299/customer**

---

## 3. Unit Economics

### 3.1 Gross Margin Per Audit

| Tier | Price | COGS | **Gross Profit** | **Gross Margin** |
|------|-------|------|-----------------|-----------------|
| Basic | $99 | $0.13 | $98.87 | **99.9%** |
| Standard | $299 | $0.18 | $298.82 | **99.9%** |
| Premium (monthly) | $499 | $0.14 × 4 re-runs + $10 overhead | ~$488 | **97.8%** |

> Note: Premium overhead (~$10/month) includes proportional support time, extra storage for historical reports, and monthly certificate generation. Even with generous overhead, margins remain exceptional.

### 3.2 Customer Acquisition Cost (CAC)

**Channel: Cold email outreach (primary channel for $100 budget)**

Assumptions based on B2B SaaS cold email benchmarks:
- Cold email open rate: 25–35% (personalized outreach)
- Reply rate: 5–10%
- Demo/trial-to-close: 20–30%
- Conversion funnel: 100 emails → 30 opens → 7 replies → 2 customers
- Time cost (your labor, not cash): ~4 hours per 100 emails sent

**Cash CAC:**
- Tools: Apollo.io free tier (50 exports/month) + Hunter.io free tier (25 searches/month)
- Email sending: Instantly.com or Lemlist — **$37/month** for sending infrastructure
- Copywriting, research: your time
- **Cash CAC = $37 / 2 customers per 100 emails = $18.50/customer**

At higher volume with paid prospecting tools:
- Apollo.io Basic: $49/month for 1,000 contacts
- 1,000 emails → 20 customers at 2% conversion
- **Cash CAC = ($37 + $49) / 20 = $4.30/customer**

**Conservative CAC estimate: $20–$50/customer** (accounting for tool costs, occasional LinkedIn ads, referral incentives)

**Blended CAC target: $30**

### 3.3 Lifetime Value (LTV)

**One-time customers (Basic + Standard):**
- Average order value: (($99 + $299) / 2) = $199
- Repeat purchase rate: ~20% buy again within 12 months (compliance re-audit cycle)
- LTV = $199 + (0.20 × $199) = **$239**

**Premium subscribers:**
- Monthly revenue: $499
- Average churn rate: 5%/month (B2B SaaS benchmark for compliance tools — sticky)
- Average lifespan: 1 / 0.05 = **20 months**
- LTV = $499 × 20 = **$9,980**
- Gross profit LTV = $9,980 × 97.8% = **$9,759**

**Blended LTV** (30/40/30 mix, treating Standard as one-time):
- (0.30 × $239) + (0.40 × $239) + (0.30 × $9,980) = $71.70 + $95.60 + $2,994 = **$3,161**

### 3.4 LTV:CAC Ratio

| Scenario | LTV | CAC | **LTV:CAC** | Assessment |
|----------|-----|-----|-------------|------------|
| One-time only (conservative) | $239 | $30 | **8:1** | Excellent (>3:1 is good) |
| Premium subscriber | $9,980 | $30 | **333:1** | Exceptional |
| Blended | $3,161 | $30 | **105:1** | Exceptional |

> Target: >3:1. Anything above 5:1 is considered very healthy for B2B SaaS.

### 3.5 Payback Period

| Tier | Revenue | CAC | **Payback Period** |
|------|---------|-----|--------------------|
| Basic | $99 | $30 | **<1 month** |
| Standard | $299 | $30 | **<1 month** |
| Premium | $499/mo | $30 | **<1 month** (day 1 effectively) |

The payback period is essentially immediate for all tiers — cash is collected upfront and COGS is <$1. This is an extraordinarily cash-efficient business model.

---

## 4. Revenue Projections

### Assumptions

- Solo operator, cold email primary channel
- 2 hours/day on outreach and fulfillment
- Audit delivery is nearly automated (human review: ~15 min/audit)
- Start with Standard tier focus, introduce Premium at Month 2

### 4.1 Week 1 (Setup + First Sales)

| Activity | Outcome |
|----------|---------|
| Set up VPS, toolchain, report template | $0 revenue, ~$5 cost |
| Send 200 cold emails (free tools) | — |
| Close 2–4 Standard audits | 3 × $299 = **$897** |
| **Net Week 1** | **$897 revenue, ~$5 cost = $892 profit** |

> First paying customer covers all infrastructure costs for ~14 months.

### 4.2 Month 1

| Metric | Conservative | Realistic | Optimistic |
|--------|-------------|-----------|------------|
| Cold emails sent | 400 | 600 | 800 |
| Conversion rate | 1.5% | 2% | 3% |
| New customers | 6 | 12 | 24 |
| Tier mix (B/S/P) | 50/50/0 | 30/60/10 | 20/50/30 |
| Revenue | $1,194 | $3,339 | $6,270 |
| COGS | $3 | $6 | $11 |
| **Gross Profit** | **$1,191** | **$3,333** | **$6,259** |
| Fixed costs (VPS + email tools) | $42 | $42 | $42 |
| **Net Profit Month 1** | **$1,149** | **$3,291** | **$6,217** |

### 4.3 Month 3

By Month 3, assuming:
- 5 Premium subscribers from Month 1–2 conversions
- Steady cadence of 15 new customers/month
- Referral traffic beginning

| Metric | Value |
|--------|-------|
| New customers/month | 15 |
| Revenue from new customers | (0.30 × $99 + 0.40 × $299 + 0.30 × $499) × 15 = $299 × 15 = **$4,485** |
| MRR from existing Premium subs (5) | 5 × $499 = **$2,495** |
| **Total Monthly Revenue** | **$6,980** |
| COGS | ~$15 |
| Fixed costs | ~$86 (adding Apollo.io) |
| **Net Profit Month 3** | **$6,879** |
| **MRR** | **$6,980** |

### 4.4 Month 6

By Month 6, assuming:
- 15 Premium subscribers accumulated (5% churn = ~1/month lost, net +2/month)
- 20 new customers/month
- Word-of-mouth + some LinkedIn content driving inbound

| Metric | Value |
|--------|-------|
| New customers/month | 20 |
| Revenue from new customers | $299 × 20 = **$5,980** |
| MRR from Premium subs (15) | 15 × $499 = **$7,485** |
| **Total Monthly Revenue** | **$13,465** |
| COGS | ~$25 |
| Fixed costs | ~$120 (VPS + tools + occasional ads) |
| **Net Profit Month 6** | **$13,320** |
| **ARR run rate** | **$161,580** |

### 4.5 Break-Even Analysis

**Break-even = Fixed costs / Gross margin per unit**

Monthly fixed costs at launch: $42 (VPS $5 + email tool $37)

Break-even in Standard audits: $42 / $298.82 = **0.14 audits/month**

Translation: **selling 1 audit per month covers all costs**. This business breaks even on the very first sale. There is no meaningful burn period.

**Break-even including your time** (optional, if valuing at $50/hr):
- At 2 hrs/day × 22 working days = 44 hrs/month × $50 = $2,200 implicit cost
- Break-even: $2,242 / $298.82 = **8 Standard audits/month to "pay yourself" $50/hr**

---

## 5. Budget Allocation ($100 Starting Fund)

### 5.1 What Costs Money vs. What's Free

| Item | Cost | Notes |
|------|------|-------|
| **Paid** | | |
| Hetzner CX22 VPS | $5/month | Core infrastructure |
| Domain name (1 year) | $12 | One-time |
| Email sending (Instantly.com or Brevo) | $0–$25/month | Free tier sufficient for Month 1 |
| Apollo.io (prospecting) | $0 | Free tier: 50 exports/month |
| **Free** | | |
| Claude API | $0 upfront | Pay-per-use, ~$0.06/audit |
| Playwright + axe-core | $0 | Open source |
| WeasyPrint (PDF) | $0 | Open source |
| Resend.com (email delivery) | $0 | Free: 3,000 emails/month |
| Let's Encrypt SSL | $0 | Automated |
| GitHub (repo + CI) | $0 | Free tier |
| Hunter.io (email finder) | $0 | Free: 25/month |
| LinkedIn (outreach) | $0 | Manual DMs |

### 5.2 Optimal $100 Allocation

| Allocation | Amount | Rationale |
|------------|--------|-----------|
| Domain registration (1 year) | $12 | Non-negotiable, establishes credibility |
| Hetzner VPS (2 months buffer) | $10 | Server for 2 months; revenue covers rest |
| Claude API credits (pre-load) | $20 | ~333 Standard audits worth of buffer |
| Email outreach tool (1 month) | $25 | Lemlist/Instantly starter plan |
| LinkedIn Premium (1 month) | $0 | Skip — manual outreach sufficient at start |
| Reserve / emergency buffer | $33 | Contingency for unexpected costs |
| **Total** | **$100** | |

**Do NOT spend on:**
- Paid ads (too expensive, unproven ROI at this stage)
- Fiverr/Upwork profile boosts (wrong channel)
- Fancy landing page builder (use Carrd at $19/year or free GitHub Pages)

### 5.3 When Do We Become Self-Funding?

**Day 1 of first sale.** The first Standard audit at $299 covers:
- 1.2 months of VPS hosting
- 4,983 additional Standard audits worth of Claude API costs
- 11.96 months of domain registration
- All other tool costs for Month 1

**Self-funding timeline:**
- Week 1: First sale → operations are cash-flow positive indefinitely
- Month 1: Outreach tools paid from revenue; $100 seed money never fully spent
- Month 2: Begin reinvesting into paid prospecting tools from profit

---

## 6. Key Risks and Mitigations

| Risk | Impact | Mitigation |
|------|--------|-----------|
| Claude API price increase | Low (margins are 99.9%) | Switch to Haiku 4.5 Batch; explore open models |
| Cold email deliverability issues | Medium | Warm domains properly; use reply-based engagement |
| Customer disputes ("not a manual audit") | Medium | Clear disclaimers; position as "AI-assisted automated audit" |
| Competition from free tools | Low | Free tools produce raw data, not reports; our value is narrative + roadmap |
| WCAG standard updates (e.g., 2.3) | Low | Update axe-core rules; report template versioned |
| Churn on Premium tier | Medium | Build stickiness via monthly delta reports and compliance certificates |

---

## 7. Summary Scorecard

| Metric | Value |
|--------|-------|
| COGS per Standard audit | **$0.18** |
| Gross margin | **99.9%** |
| CAC (cash) | **~$30** |
| LTV (blended) | **$3,161** |
| LTV:CAC ratio | **105:1** |
| Payback period | **<1 month** |
| Break-even (cash) | **1 audit** |
| Month 1 net profit (realistic) | **$3,291** |
| Month 6 net profit | **$13,320** |
| Month 6 ARR run rate | **$161,580** |
| Starting capital required | **$100** |

**Verdict:** This is one of the most capital-efficient business models possible. Near-zero COGS, immediate payback, and a large underserved market (every website needs WCAG compliance; ADA lawsuits hit 4,000+/year in the US). The primary constraint is outreach volume and sales conversion — not capital or infrastructure.

---

## Sources

- Claude API pricing: [Anthropic Pricing Docs](https://platform.claude.com/docs/en/about-claude/pricing) | [CostGoat Claude API Calculator](https://costgoat.com/pricing/claude-api)
- WCAG audit market pricing: [DigitalA11Y Audit Cost Guide](https://www.digitala11y.com/how-much-does-a-web-accessibility-audit-cost/) | [Accessible.org Pricing](https://accessible.org/pricing/) | [Kris Rivenburgh Cost Guide](https://krisrivenburgh.com/cost-website-accessibility-wcag-2-1-aa-audit-ada-compliance/)
- VPS hosting: [Hetzner Cloud](https://www.hetzner.com/cloud) | [DigitalOcean Pricing](https://www.digitalocean.com/pricing)
- Email delivery: [SendGrid Pricing](https://sendgrid.com/en-us/pricing) | [Mailgun Pricing 2025](https://www.sender.net/reviews/mailgun/pricing/)
- Competitor monitoring tools: [accessiBe Pricing](https://accessibe.com/pricing/accesswidget) | [UserWay Pricing](https://tekpon.com/software/userway/pricing/)
