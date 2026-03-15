# Eval B: Competitive Landscape — AI-Powered WCAG Accessibility Audit ($200–$500/report)

> Research date: 2026-03-15
> Purpose: Deep competitive analysis for an AI-powered WCAG accessibility audit business selling automated PDF reports at $200–$500 per report. Maps all competitor categories, their pricing, weaknesses, and the gaps our offer fills.

---

## Executive Summary

The accessibility audit market is fragmented into four price tiers with a clear gap in the middle:

| Tier | Who | Price | Weakness |
|---|---|---|---|
| Free tools | axe, WAVE, Lighthouse | $0 | Raw data, not a report |
| Budget freelancers | Fiverr/Upwork India-based | $25–$150 | Slow (3–14 days), inconsistent quality |
| Our target zone | AI-automated report | $200–$500 | **This is the gap** |
| Agency manual audit | Specialty firms | $1,500–$10,000 | Expensive, slow (2–6 weeks) |
| Enterprise SaaS | Siteimprove, Level Access | $15,000–$100,000/yr | SMB-inaccessible, subscription-only |

The market tailwind is significant: ADA Title II rules took effect April 2026 for large government entities and April 2027 for smaller ones, creating a wave of compliance urgency across municipalities, healthcare, and education. Meanwhile, the FTC fined accessiBe $1 million in January 2025 for falsely claiming AI overlays ensure WCAG compliance — this has increased scrutiny and demand for *legitimate* audit reports.

---

## 1. Enterprise Accessibility Tools (Indirect Competitors)

### 1.1 Siteimprove

**What they sell:** Bundled enterprise platform combining accessibility monitoring, SEO, content quality, and analytics. Added an AI Assistant in 2025 that explains issues in plain language and suggests fixes.

**Pricing:**
- Average contract: ~$28,000/year
- Range: $15,000–$63,000/year
- Pricing is custom quote only; no self-serve purchase

**Target market:** Large enterprises and public sector organizations with dedicated digital teams, budget for annual contracts, and multi-site monitoring needs.

**Weaknesses we can exploit:**
- Completely inaccessible price point for SMBs — $28K/year for a small business seeking a one-time compliance check is absurd
- Continuous monitoring focus means they don't sell one-off reports; they want long-term contracts
- Complex onboarding (2–4 week learning curve) — SMBs want answers now, not a platform to learn
- Does not produce a client-ready, stakeholder-facing PDF audit report; outputs are dashboards requiring interpretation

**Strengths we must respect:**
- Deep enterprise integrations (CI/CD, CMS workflows)
- Brand authority and enterprise trust signals
- Continuous monitoring catches regressions over time (we don't offer this)

**Price/value gap we fill:** An SMB that needs to answer "are we WCAG compliant?" doesn't need a $28K platform. They need a $299 PDF they can share with their board or legal team today.

---

### 1.2 Level Access

**What they sell:** Comprehensive accessibility management platform combining automated scanning, expert managed services, training, and legal support. Positioned as the "enterprise gold standard."

**Pricing:**
- Range: $25,000–$100,000+/year
- No public pricing; custom quotes only
- Accelerate Package: 1,000 monitored pages, 100-page scans, unlimited users

**Target market:** Large enterprises, federal contractors, healthcare systems, and financial institutions where accessibility is a legal and compliance priority.

**Weaknesses we can exploit:**
- Sales-led motion with long deal cycles — SMBs cannot navigate enterprise procurement
- No self-serve, no instant purchase, no one-off reports
- Pricing creates a hard floor that eliminates anyone without a dedicated accessibility budget
- Focuses on ongoing compliance management, not one-time audit reports

**Strengths we must respect:**
- Deep human expertise and IAAP-certified auditors
- Legal defensibility of their reports in lawsuits
- Strong brand in regulated industries

**Price/value gap we fill:** Organizations that don't have a $50K/year budget but still face legal exposure from the ADA and EAA. A $499 audit report with executive-level language is a credible starting point.

---

### 1.3 Deque (axe DevTools)

**What they sell:** The industry-standard accessibility testing engine (axe-core, the same library powering WAVE, Lighthouse accessibility checks, and hundreds of other tools). Offers a free browser extension and paid Pro/Enterprise tiers.

**Pricing:**
- Free browser extension: $0
- axe DevTools Extension Pro: $45/month or $500/year per user
- axe DevTools for Web (Bundle): ~$27,000+/year (enterprise)
- Full enterprise suite: custom

**Target market:** Individual developers and QA engineers (free tier); enterprise dev teams needing CI/CD integration and centralized reporting (paid tiers).

**Weaknesses we can exploit:**
- Developer tool, not a business deliverable — outputs require a human to synthesize into a report
- Per-user seat pricing makes it expensive to scale across agencies or client work
- Does not generate stakeholder-ready PDF reports automatically
- Free tier is a browser extension requiring technical knowledge to interpret

**Strengths we must respect:**
- axe-core is the most trusted detection engine (near-zero false positives); we should use it as our underlying scanner
- 70+ automated WCAG checks — the benchmark for automated coverage
- Strong developer community and brand recognition as the "truth source" for WCAG

**Price/value gap we fill:** We use axe-core under the hood but wrap it in an AI narrative layer that transforms raw technical findings into a readable, prioritized, business-ready report.

---

### 1.4 AudioEye

**What they sell:** Hybrid accessibility platform combining automated AI fixes (JavaScript overlay) with human expert review. Has an audit component embedded in the platform.

**Pricing:**
- Basic (Automated): starting ~$49/month
- Self-Managed: mid-tier (estimated $99–$199/month)
- Maximum Protection (Managed): custom pricing
- Annual plans available with ~20% discount

**Target market:** SMBs to mid-market organizations wanting a "set it and forget it" compliance solution, often driven by fear of ADA lawsuits.

**Weaknesses we can exploit:**
- Overlay approach is legally contested — auditors, disability advocates, and courts increasingly reject overlays as compliance evidence
- Ongoing subscription model means clients are paying forever even if their site doesn't change
- The "audit" is bundled into the subscription, not a standalone deliverable — clients can't extract a compliance report to share with a lawyer
- Does not produce WCAG 2.2-level compliance documentation suitable for legal defense

**Strengths we must respect:**
- Strong marketing to SMBs around lawsuit prevention
- Recurring revenue model (not directly comparable — they sell ongoing protection, we sell a snapshot)
- "Done-for-you" messaging resonates with non-technical owners

**Price/value gap we fill:** A business owner who has heard about ADA lawsuits and wants *documentation* of their compliance status, not a recurring widget subscription they don't understand.

---

### 1.5 UserWay

**What they sell:** AI-powered accessibility widget (overlay) providing real-time adjustments (contrast, font size, keyboard navigation aids) plus an audit dashboard.

**Pricing:**
- Small site (up to 100K page views): $49/month / $490/year
- Medium site (up to 1M page views): $149/month / $1,490/year
- Large/Enterprise: custom
- Per-page audit packages: 100 pages = $990/year, 500 pages = $4,490/year

**Target market:** SMBs, e-commerce sites, and agencies seeking affordable compliance coverage. Popular with WordPress and Shopify users.

**Weaknesses we can exploit:**
- Overlay approach faces the same legal criticism as accessiBe — the FTC's $1M fine against accessiBe put every overlay vendor under scrutiny
- Does not produce a formal WCAG audit report; dashboard ≠ audit documentation
- Subscription dependency: if a customer cancels, their compliance "disappears"
- Many customers buy it purely for the widget, unaware of its audit limitations

**Strengths we must respect:**
- Large installed base and strong brand recognition among WordPress agencies
- Entry price ($49/month) is low enough for impulse purchase
- "Widget" approach has broad distribution (WordPress plugin, Shopify app)

**Price/value gap we fill:** UserWay sells protection. We sell documentation. A business with UserWay installed still needs an audit report to prove compliance to a plaintiff's attorney or a government agency.

---

### 1.6 accessiBe

**What they sell:** AI-powered accessibility widget claiming automated WCAG compliance. Fined $1M by the FTC in January 2025 for falsely claiming it makes websites WCAG-compliant.

**Pricing:**
- Plans start at ~$49/month (traffic-based pricing via Similarweb data)
- Annual plans: starting at $490/year
- Higher traffic tiers: up to $349/month

**Target market:** Non-technical SMB owners seeking a low-cost, set-and-forget compliance solution. Heavy reliance on fear-based marketing around ADA lawsuits.

**Weaknesses we can exploit:**
- FTC fine is a massive credibility wound — any competitor can cite it in sales/marketing
- Product is legally discredited as a compliance solution by the FTC consent order
- Many buyers feel deceived; a "real audit report" directly addresses this trust gap
- The FTC order specifically bars accessiBe from claiming automated tools can ensure WCAG compliance — this is a free objection handler for us

**Strengths we must respect:**
- Massive brand awareness in the SMB market through aggressive SEO and affiliate marketing
- Low price point creates high volume
- Strong upsell capability (they also sell audit services and managed services)

**Price/value gap we fill:** AccessiBe's customers are now on notice that their "widget" doesn't prove compliance. They need a real audit report. We are the next logical purchase after an accessiBe buyer gets scared.

---

## 2. Freelancers on Fiverr and Upwork

### 2.1 Fiverr WCAG Audit Market

**Market size:** Fiverr shows approximately 24 curated "WCAG" and "Accessibility" service listings — a relatively thin market, not oversaturated.

**Price range (observed gigs, March 2026):**
| Seller | Starting price | What's included |
|---|---|---|
| kashifaws | $10 | ADA/WCAG code fixes (remediation, not audit) |
| sarmad_alihaide | $25 | WCAG/ADA/VPAT testing |
| ritvik_qa | $35–$40 | WCAG audit + testing |
| vijaysingh447 | $35–$200 | Testing ($35) or full audit + VPAT report ($200) |
| afro14 | $50 | Audit + fix |
| sammyaccess | $200 | White-label audit + remediation |

**Typical delivery time:** 3–7 days for basic audits; 7–14 days for comprehensive reports.

**Quality patterns:**
- Most sellers are India-based; reports are functional but often generic, lacking business-context language
- Reviews tend to be positive for individual helpfulness but clients report needing to ask follow-up questions (report lacks clarity)
- VPAT creation is a premium add-on (typically $100–$200 extra)
- White-label options exist but are rare and command premium pricing

**Weaknesses we can exploit:**
- Human delivery speed: 3–14 day turnaround is a direct vulnerability. We deliver in minutes.
- Inconsistency: quality varies dramatically seller to seller; buyers can't vet before purchase
- No brand, no legal backing, no methodology documentation — reports are difficult to use in legal contexts
- Sellers often do automated scans dressed up as manual audits; buyers can't tell the difference
- No instant purchase flow — requires DM, scoping, back-and-forth

**Strengths we must respect:**
- Very low entry price ($25–$50) creates a price-anchoring problem
- Human "feel" can be reassuring to some buyers
- Sellers can accommodate custom scoping requests

**Price/value gap we fill:** $200–$500 is 4–10x the Fiverr entry price, which means we must clearly communicate the value delta: instant delivery, consistent methodology, legally defensible format, AI-generated business narrative, and no dependency on a single freelancer's availability.

---

### 2.2 Upwork WCAG Specialists

**Price range:**
- India-based certified experts (IAAP, DHS certified): $15–$45/hour
- US-based certified specialists: $75–$150/hour
- Fixed-price audits: $200–$800 for a typical 10–50 page site
- VPAT/ACR reports: $350–$950 standalone; $550 combined with audit

**Quality patterns:**
- Higher credential density than Fiverr (IAAP CPACC, WAS certifications common)
- Government and enterprise clients use Upwork for $5,000–$15,000 multi-month accessibility projects (audits + VPAT + remediation + re-testing)
- Standard deliverable time: 1–3 weeks

**Weaknesses we can exploit:**
- Still slow relative to instant delivery
- Pricing inconsistency — buyer must evaluate multiple proposals before choosing
- Platform friction (posting job, receiving proposals, contracting) adds days of overhead
- Upwork's 20% freelancer fee means quality talent prices up to compensate

**Strengths we must respect:**
- Top-tier experts deliver genuinely comprehensive manual audits with screen reader testing
- VPAT reports produced by certified experts are legally stronger than any automated output
- Enterprise buyers specifically seek human-certified reports for procurement purposes

**Price/value gap we fill:** The $200–$500 SMB who cannot afford a $1,500+ Upwork project and doesn't have time to post a job, evaluate proposals, and wait two weeks.

---

## 3. Agencies and Accessibility Consultants

### 3.1 Market Overview

Manual accessibility audits from specialist agencies represent the premium end of the market and set the quality benchmark.

**Typical pricing:**
| Service | Price range |
|---|---|
| Basic automated scan + report | $500–$1,500 |
| Manual audit (10–20 pages) | $1,500–$3,500 |
| Comprehensive audit (20–50 pages) | $2,500–$7,500 |
| Enterprise-scale audit + VPAT | $5,000–$15,000 |
| Expert audit with AT testing | $7,500–$25,000 |
| Ongoing monitoring retainer | $200–$1,000/month |

**Per-page pricing model (used by Accessible.org and others):**
- $100–$250 per page for full manual review
- $25–$100 per page for lighter/template pages
- VPAT creation: $350–$950 depending on standard (WCAG, Section 508, EN 301 549)
- User testing sessions (assistive technology users): $450–$550/session

**What agencies deliver:**
- IAAP-certified auditor evaluation
- Manual screen reader testing (JAWS, NVDA, VoiceOver, TalkBack)
- Keyboard-only navigation testing
- Cognitive accessibility evaluation
- Detailed findings with screenshots, code examples, WCAG criterion citations
- Executive summary, prioritized remediation roadmap
- VPAT/ACR documentation for procurement compliance
- Legal defensibility — signed off by a named professional

**Typical delivery time:** 2–6 weeks depending on scope.

**Weaknesses we can exploit:**
- Slow: 2–6 week turnaround is a liability when a lawsuit has already been filed or a compliance deadline is imminent
- Expensive entry point: even the cheapest agency audit ($1,500+) is out of reach for a 10-person company
- Report quality varies significantly — many agencies produce reports that are technically correct but incomprehensible to non-technical stakeholders
- No self-serve option — every engagement requires scoping calls, SOW, contracting
- The "30% automated + 70% manual" methodology means their process is labor-intensive and unscalable

**Strengths we must respect:**
- Human testing catches issues automated tools cannot (cognitive accessibility, context-aware alt text evaluation, complex interactive widget behavior)
- Legal defensibility of human-signed reports is higher — courts recognize IAAP-certified expert testimony
- Can provide ongoing retainer relationships and holistic remediation support
- VPAT/ACR documentation is a high-value add we cannot fully replicate automatically

**Price/value gap we fill:** The $200–$500 price point sits below the agency entry floor ($1,500+) while delivering more value than raw tool output. We serve the customer who knows a $10 Fiverr gig isn't sufficient but can't justify a $3,500 agency engagement.

---

## 4. Free Tools (Why They Are Not Real Competitors)

Free tools generate raw technical data; they do not produce client-ready reports. This distinction is critical.

### 4.1 axe DevTools (Free Browser Extension)

**What it does:** Browser extension that scans the current page and flags WCAG violations in the developer console. Results include rule name, impact level, DOM element, and suggested fix.

**What it does NOT do:**
- Does not generate a PDF or shareable document
- Does not provide executive summary or business narrative
- Does not prioritize issues by business impact or legal risk
- Does not aggregate findings across multiple pages
- Requires a developer to run it, interpret it, and turn it into something readable

**Coverage limit:** Catches ~30–40% of WCAG issues (automated detection ceiling); remainder requires manual testing.

**Why it's not a competitor:** It's a development tool, not a business deliverable. A business owner cannot hand an axe DevTools scan to their legal team. We transform axe-core results (plus AI reasoning) into something humans can act on.

---

### 4.2 WAVE (WebAIM)

**What it does:** Free web-based and browser extension tool that visually overlays accessibility issues on a webpage. Excellent for visual learners and quick spot-checks.

**What it does NOT do:**
- No bulk/multi-page scanning in free version
- No exportable report in free tier (paid API required)
- No issue prioritization or business context
- Visual overlay is meaningless outside of a browser session

**Coverage limit:** Comparable to axe (~30–40% of WCAG issues).

**Why it's not a competitor:** WAVE is a spot-check tool for developers. Non-technical users cannot extract value from it without assistance.

---

### 4.3 Google Lighthouse (Accessibility Score)

**What it does:** Built into Chrome DevTools. Scores a single page's accessibility on a 0–100 scale and lists failing audits.

**What it does NOT do:**
- Score is misleading — a "100" does not mean WCAG compliant; it means the automated checks passed
- Does not run the full axe rule set (axe DevTools free is more comprehensive)
- No multi-page analysis
- No business narrative, no remediation roadmap
- Score is easily gamed (adding an aria-label to one button raises the score disproportionately)

**Coverage limit:** Most limited of the three (~20–30% of WCAG issues); optimized for performance scoring, not accessibility depth.

**Why it's not a competitor:** Lighthouse's accessibility score is frequently misused as a compliance claim. Our report can explicitly address the gap between a high Lighthouse score and actual WCAG conformance — this is itself a sales message.

---

## 5. AI-Powered Newcomers (Direct Competitors)

### 5.1 AccessGlance

**URL:** accessglance.com

**What they sell:** Free instant scan + $29 paid PDF report. The paid report includes complete WCAG 2.2 AA violation analysis with AI-assisted severity ratings, business summaries, technical guidance, code examples, and implementation guidance (Top 10 Common Fixes).

**Positioning:** "For small businesses, agencies, and enterprise teams."

**Pricing:**
- Free: Instant scan, AI compliance score (0–100), no registration
- Paid: $29 per report (one-time)

**Weaknesses we can exploit:**
- $29 price point is low — positions them as a cheap utility, not a professional compliance service
- At $29, buyers likely question the depth and defensibility of the report
- "Top 10 Common Fixes" language implies a template, not a site-specific audit
- No human review layer or certification — purely automated
- Limited to single-page or limited crawl scope (unclear from pricing)

**Strengths we must respect:**
- Self-serve, instant, no registration required — frictionless buying experience
- Free tier acts as a powerful lead magnet and trial driver
- $29 creates a reference price that we must justify surpassing

**Price/value gap we fill:** $200–$500 vs. their $29 requires us to clearly articulate: more pages covered, deeper narrative analysis, legally defensible methodology documentation, executive-level language, VPAT-adjacent structure. We are the "professional report" to their "quick scan."

---

### 5.2 The Audit Base

**URL:** theauditbase.com

**What they sell:** Automated WCAG 2.1 AA accessibility auditing service using axe-core + Playwright. Produces a PDF report within 10 minutes of payment.

**Pricing:**
- $199: Scan Report (up to 50 pages)
- $999: Scan + Remediation Plan (up to 1,000 pages)

**What the report includes:**
- Executive summary in plain language
- Compliance score (0–100)
- Violations by severity (Critical/Serious/Moderate/Minor)
- WCAG criterion codes for each issue
- Remediation roadmap with effort estimates
- Methodology documentation for legal defensibility

**Target market:** State/local government (ADA Title II), healthcare, higher education, federal contractors.

**Weaknesses we can exploit:**
- Purely automated — catches only ~30–40% of WCAG issues; advanced issues (screen reader behavior, cognitive accessibility, complex interactive components) are missed
- No human review or certification — limiting legal defensibility for high-stakes buyers
- $199 tier limited to automated scan output; remediation plan at $999 may be upsell-heavy
- Government-focused messaging may feel cold and bureaucratic to SMB buyers
- No free trial or preview — full commitment required

**Strengths we must respect:**
- Direct competitor at very similar price point ($199 vs. our $200–$500)
- Fast delivery (10 minutes) sets the expectation we must meet or beat
- Methodology documentation for legal defensibility is a smart differentiator
- Stripe payment, no account required — zero-friction purchase

**Price/value gap we fill:** The Audit Base is our closest direct competitor. Our differentiation must be: richer AI narrative quality, clearer business-language recommendations (not just WCAG codes), optional human-review add-on, stronger brand trust signals, and possibly a free preview scan.

---

### 5.3 Accesstive

**URL:** accesstive.com

**What they sell:** Real-time AI accessibility auditing tool that identifies and fixes issues. Focused on developers and agencies; offers live monitoring, not just one-off reports.

**Pricing:** Unclear — free trial available; premium pricing not publicly disclosed.

**Target market:** Developers, marketers, legal/compliance teams, agencies.

**Weaknesses we can exploit:**
- Pricing opacity is a conversion killer for SMBs who want to know the cost upfront
- Developer-centric positioning alienates non-technical business owners
- "Real-time monitoring" implies ongoing subscription vs. a one-time deliverable
- No clear PDF audit report product — primarily a monitoring/alerting tool

**Strengths we must respect:**
- Real-time detection is technically superior for developers catching issues in-sprint
- Multi-standard coverage (WCAG, ADA, Section 508, global standards)

---

### 5.4 Workik AI Accessibility Audit Tool

**What they sell:** Free AI tool generating WCAG-compliant reports using Puppeteer and Axe Core. Positioned as a developer utility.

**Pricing:** Free

**Weaknesses we can exploit:**
- Free = no business model around deliverable quality; report depth is limited
- Developer-only positioning (requires technical setup)
- No PDF/shareable report format for stakeholders

**Why they're not a real threat:** Free tools compete on price, not quality. Buyers of professional reports self-select out of free tools.

---

## 6. Competitive Positioning Map

```
                     HIGH PRICE
                          |
     Level Access         |        Agency Manual Audits
     ($25K–$100K/yr)      |        ($1,500–$10,000/project)
                          |
     Siteimprove          |
     ($15K–$63K/yr)       |
                          |
- - - - - - - - - - - - -+- - - - - - - - - - - - - - - -
   AUTOMATED              |                    HUMAN
                          |
     AudioEye/UserWay     |        Upwork Certified Experts
     ($49–$349/mo)        |        ($200–$800 fixed price)
                          |
     The Audit Base ★     |        Fiverr Gigs
     ($199–$999/report)   |        ($25–$200/gig)
                          |
     AccessGlance         |
     ($29/report)         |
                          |
  axe/WAVE/Lighthouse     |
     (Free tools)         |
                          |
                     LOW PRICE
```

**Our target zone:** $200–$500/report, automated delivery, positioned just above The Audit Base with superior AI narrative quality and SMB-friendly business language.

---

## 7. Key Market Insights

### 7.1 The 30–40% Automation Ceiling Is a Feature, Not a Bug

Every competitor using purely automated tools (including us) catches only 30–40% of WCAG issues. This is widely documented. Rather than hiding this, we should lead with it — and use it to frame what our report does and does not claim. This is how we avoid the accessiBe trap (FTC fine for overclaiming). Our positioning: "The most complete automated audit report available — clear documentation of what we found and a roadmap for what requires human review."

### 7.2 The FTC accessiBe Fine Is a Market Opening

The January 2025 FTC fine created significant distrust of "AI equals compliance" claims among SMB buyers. This is an opportunity: a report that is transparent about methodology, honest about its automated limitations, and formatted for legal defensibility stands apart from every overlay vendor in the market.

### 7.3 ADA Title II 2026–2027 Creates Immediate Demand

April 2026 deadline for large government entities (50,000+ population) and April 2027 for smaller municipalities creates a buying wave. Government entities, school districts, and healthcare providers all need documented WCAG audits on tight timelines. Our instant delivery model is purpose-built for this urgency window.

### 7.4 Report Format Is an Underserved Differentiator

Multiple research sources confirm that existing reports — even from good agencies — suffer from: vague issue descriptions, missing business context, poor prioritization, and no executive summary that a non-technical stakeholder can actually read. "Clear documentation reduces remediation time by 60%" (TestParty). The AI narrative layer is not just a cost-reduction play; it is a genuine quality improvement over most human-produced reports.

### 7.5 The Free-to-Paid Funnel Is Proven

AccessGlance's free scan → $29 report model and The Audit Base's instant payment model both validate a self-serve, no-sales-call purchasing behavior for accessibility reports. SMB buyers do not want discovery calls for a $299 purchase.

---

## 8. Competitive Differentiators We Must Build

Based on competitor weakness analysis, our offer requires these elements to win:

| Differentiator | Why it matters | Competitor gap |
|---|---|---|
| Instant delivery (< 15 minutes) | Time is money; urgency drives purchase | Agencies: 2–6 weeks; Fiverr: 3–14 days |
| Business-language executive summary | Non-technical owners need to understand findings | Agencies produce technical jargon; tools produce raw data |
| Transparent methodology disclaimer | Post-FTC market demands honesty about automation limits | AccessiBe et al overclaimed; burned buyers are skeptical |
| Legal-risk framing per issue | Buyers want to know what matters most | Tools list everything equally; agencies bury the lede |
| Self-serve, no sales call | SMBs will not take a discovery call for $299 | Enterprise tools all require demo/quote |
| Shareable PDF format | Needs to be forwarded to lawyers, boards, developers | Tool dashboards are not shareable documents |
| Consistent methodology | Reproducible process buyers can reference | Fiverr gig quality is inconsistent and unverifiable |
| Upgrade path to human review | Cover the 60–70% automated tools miss; upsell opportunity | Most automated tools have no human layer available |

---

## 9. Pricing Strategy Recommendation

**Entry product:** $199 — Single-page/template audit (up to 10 pages). Targets: solopreneurs, micro-businesses. Positions us as accessible entry point vs. $1,500+ agencies.

**Core product:** $299–$349 — Full site audit (up to 50 pages). Targets: SMBs, local government, e-commerce. Sweet spot where Fiverr quality fails and agencies are out of reach.

**Premium product:** $499 — Full audit + VPAT-adjacent summary + remediation priority matrix (up to 100 pages). Targets: healthcare, higher ed, government contractors. Competes directly with The Audit Base's $999 tier and undercuts agency pricing by 70%.

**Add-on upsell:** $199–$499 — Human expert review layer. Certified auditor reviews AI-generated findings, adds screen reader test notes, signs the report. Adds legal defensibility and opens enterprise door.

---

*Sources consulted: Vendr, Capterra, G2, Accessible.org, DigitalA11Y, TestParty, FTC.gov, Accessibility.works, Fiverr, Upwork, AccessGlance, The Audit Base, Accesstive, ADA.gov, multiple accessibility industry publications.*
