# Executive Report: AI-Powered Security Scan Report Business
**Evaluation Date:** March 15, 2026
**Classification:** Internal Strategy Document
**Decision Required:** GO / NO-GO — Automated Website Security Assessment for SMBs

---

## 1. Executive Summary

**CONDITIONAL GO.** The AI-Powered Security Scan Report business occupies a genuine, underserved gap in the market: SMBs face a cybersecurity threat environment that is actively worsening — Verizon's 2025 DBIR reports SMBs are targeted *nearly four times more* than large organizations — yet the cheapest professional pentesting starts at $5,000–$15,000 and subscription scanners (Detectify at €90–€302/month, Intruder at similar rates) require ongoing commitment and deliver raw technical output, not executive-ready findings. An AI-narrated, one-time-purchase report at $200–$1,000 solves a real problem at a price SMBs will pay, with unit economics that pencil out cleanly (estimated 75–85% gross margin post-tooling). The single existential risk — legal liability from unauthorized scanning — is manageable with explicit permission gating, but must be treated as a hard constraint, not an afterthought. This business can reach $1M ARR in 12–18 months as a solo founder operation, but requires a disciplined legal framework from Day 1 before any production scan fires.

---

## 2. The Business

### What We Sell

Automated website security assessment reports for SMBs who cannot afford a penetration test and do not have the technical staff to interpret raw scanner output. The deliverable is a polished, PDF-format executive report containing:

- An AI-narrated executive summary in plain English (no jargon)
- Prioritized vulnerability findings (Critical / High / Medium / Low / Informational)
- Contextual explanation of each finding and its real-world business risk
- Specific remediation steps, ordered by effort-to-impact ratio
- Compliance cross-references (PCI-DSS, HIPAA, SOC 2, cyber insurance requirements)
- SSL/TLS configuration grade and certificate chain analysis
- Security headers scorecard (CSP, HSTS, X-Frame-Options, etc.)
- Retest eligibility window (optional add-on)

### How AI Does 100% of the Work

The pipeline is fully automated. No human security analyst is involved in report generation:

1. **Discovery & Scanning Layer**
   - **Nuclei** (27,500+ GitHub stars, 9,000+ community templates as of 2025): YAML-based vulnerability scanner covering CVEs, misconfigurations, exposed panels, default credentials, and more across HTTP, DNS, TCP, SSL, and JavaScript protocols
   - **OWASP ZAP** (open-source DAST): Spidering, active scan, passive scan for OWASP Top 10 class vulnerabilities — SQLi, XSS, CSRF, broken auth, sensitive data exposure
   - **SSL Labs API** (Qualys): Automated grading of TLS configuration, certificate validity, cipher suite strength, HSTS preloading
   - **SecurityHeaders.io API**: Checks for presence and correct configuration of HTTP security headers

2. **Data Aggregation Layer**
   - Structured JSON output from all scanners normalized into a unified finding schema
   - Deduplication and severity mapping (CVSS v3 scores where available)
   - Screenshot capture of critical findings for evidence exhibits

3. **AI Narration Layer (Claude)**
   - Claude API receives structured findings + site context + customer industry
   - Generates executive summary, per-finding business risk narrative, remediation guidance
   - Tone-matched to the customer tier (SMB owner vs. IT manager vs. compliance officer)

4. **Report Assembly**
   - Findings + AI narrative + branding → PDF via WeasyPrint or Puppeteer
   - Delivered via email link within 15–30 minutes of scan completion

### Why Now

- **Cybersecurity spending has crossed $271B globally in 2025** (Grand View Research), growing at 11.9% CAGR through 2033, projected to reach $663B
- **Cyber insurance** is now a requirement for most commercial leases, enterprise vendor relationships, and SBA loan applications — insurers require documented security assessments
- **AI narration is now fast and cheap enough** to make a $200 price point profitable; 18 months ago it was not
- **SMBs remain the most underserved segment**: they face 4x the targeting rate of large enterprises (Verizon DBIR 2025) but lack the $5K+ minimum budget for professional testing
- **Compliance pressure is accelerating**: PCI-DSS 4.0 (effective March 2024) added new requirements for web-facing applications; HIPAA enforcement fines reached a record high in 2024; cyber insurance underwriters now routinely require proof of vulnerability scanning

---

## 3. Market Opportunity

### TAM / SAM / SOM

| Layer | Definition | Size |
|---|---|---|
| **TAM** | Global cybersecurity services market (2025) | $271.9B |
| **SAM** | SMB cybersecurity services, English-speaking markets (US, UK, AU, CA) — estimated 12–15% of TAM, excluding enterprise SIEM/SOC | ~$32–40B |
| **SOM** | One-time automated security reports for SMBs, web-only scope, Year 1–3 realistic capture | $15–50M |

**SOM Calculation (bottoms-up):**
- US alone has approximately 33 million small businesses (SBA 2024)
- Estimated 4–5 million operate e-commerce, healthcare/medical, financial, or SaaS websites that handle customer data
- Realistic conversion at cold outreach: 0.5–1.5%
- At $300 average order value × 50,000 customers = **$15M Year 3 target**
- At $500 AOV × 100,000 customers = **$50M** (requires channel partnerships)

### Who Buys

**Primary Buyers (highest urgency, highest willingness to pay):**

1. **E-commerce operators** (Shopify, WooCommerce, Magento sites) — PCI-DSS compliance requires documented vulnerability scanning; a breach means chargebacks and processor termination
2. **Healthcare practices and health tech startups** — HIPAA requires technical safeguard documentation; OCR audits are increasing; cyber insurance requires proof of controls
3. **SaaS companies under 50 employees** — SOC 2 Type II requires documented security assessments; enterprise customers increasingly require it as a vendor prerequisite
4. **Professional services firms** (law, accounting, financial advisors) — handle sensitive client data; subject to state-level privacy regulations (CCPA, VCDPA, etc.); cyber insurance renewal requires assessment
5. **Any SMB applying for cyber insurance** — underwriters are standardizing pre-quote security questionnaires that reference scan results

**Secondary Buyers:**
- Municipal governments and school districts with limited IT budgets
- Non-profits handling donor PII
- Franchisees required to demonstrate security to franchisor

### Compliance Drivers

| Standard | Requirement | SMB Impact |
|---|---|---|
| **PCI-DSS 4.0** | Req 6.3: Automated technical security scans required for all web-facing applications; effective March 2024 | Any business accepting card payments online |
| **HIPAA Security Rule** | §164.308(a)(8): Periodic technical and non-technical evaluation required | ~1M healthcare-adjacent SMBs |
| **SOC 2** | CC7.1: Vulnerability management procedures must be documented and executed | All SaaS companies pursuing SOC 2 |
| **Cyber Insurance** | Pre-bind questionnaire: "Do you perform regular vulnerability scans?" Most carriers now require yes | ~$100B US cyber insurance market, growing fast |
| **CCPA / State Privacy Laws** | Implied reasonable security standard; documented assessments support defense | All California-customer-facing businesses |

---

## 4. Competitive Advantage

### The Price Gap Is the Moat

| Solution | Price | Delivery | Audience |
|---|---|---|---|
| Manual pentest (Big 4 / boutique firm) | $15,000–$50,000+ | 2–6 weeks | Enterprise |
| Mid-tier pentest firm | $5,000–$15,000 | 1–3 weeks | Mid-market |
| Penetration Testing as a Service (PTaaS) | $3,000–$10,000/year | Ongoing | Growth-stage |
| Detectify Application Scanning | €90/month (~$95) | Continuous | Tech-savvy SMB |
| Intruder Essential | ~$100–149/month | Continuous | Tech-oriented SMB |
| **Our Product** | **$200–$1,000 one-time** | **Same day** | **Any SMB** |
| DIY (run Nuclei yourself) | Free | Days of setup | Developer |

### Why Competitors Miss the SMB Buyer

**Pentest firms**: Floor price of $5,000 eliminates 90%+ of SMBs. Require scoping calls, NDAs, lengthy engagement letters. Deliver 50-page technical reports that SMB owners cannot read. Turnaround of weeks is incompatible with "I need something for my insurance renewal next week."

**Subscription scanners (Detectify, Intruder, Tenable.io)**: Built for in-house security teams or developers. Require ongoing subscription commitment. Output is a dashboard of raw technical findings — no narrative, no prioritization in plain English, no PDF to hand to an auditor. Minimum viable use requires a technical employee to interpret results.

**Our differentiation:**
1. **One-time purchase, no subscription friction** — the SMB owner can buy at decision point (insurance renewal, compliance audit, post-breach, new vendor requirement)
2. **Plain-English AI narration** — the report is written for a business owner, not a CISO
3. **Same-day delivery** — 15–30 minute automated turnaround vs. weeks for human-led engagements
4. **Compliance-ready formatting** — designed to satisfy PCI-DSS, HIPAA, and cyber insurance questionnaire requirements out of the box
5. **Price point matches SMB budget reality** — $200–$500 is an impulse purchase for a business owner; $5,000 requires board approval

---

## 5. Unit Economics

### COGS Per Scan (Standard Tier, ~$300 price point)

| Cost Item | Estimate | Notes |
|---|---|---|
| Claude API (narration, ~50K tokens in+out) | $2.00–4.00 | Claude 3.5 Sonnet pricing ~$3/MTok in, $15/MTok out |
| Nuclei scan compute (t3.medium, 10 min) | $0.15 | EC2 on-demand; can optimize with spot instances |
| OWASP ZAP compute (15 min) | $0.20 | Co-located with Nuclei on same instance |
| SSL Labs API | $0.00 | Free for non-commercial; commercial license negotiable |
| PDF generation + storage (S3) | $0.05 | WeasyPrint compute + 1MB S3 storage |
| Email delivery (SES) | $0.01 | Sub-cent per email |
| Stripe payment processing | $9.00 | 2.9% + $0.30 on $300 |
| **Total COGS** | **~$12–15** | |
| **Gross Margin at $300** | **~95%** | |
| **Gross Margin at $200** | **~92%** | |

*Note: Gross margin is exceptional because compute costs are low and AI API costs dominate. Margin compresses at higher scan complexity (more pages, more endpoints) but remains >80% in all realistic scenarios.*

### Pricing Tiers

| Tier | Price | Scope | Target Customer |
|---|---|---|---|
| **Starter** | $199 | Single domain, surface-level scan (headers, SSL, top-20 Nuclei templates) | Freelancer, very small business, pre-launch check |
| **Standard** | $349 | Single domain + subdomains (up to 5), full Nuclei template suite, ZAP active scan, compliance summary | Core SMB customer — e-commerce, professional services |
| **Professional** | $699 | Up to 3 domains + subdomains, API endpoint scan, authentication-aware scan (with credentials provided), executive + technical report | SaaS, healthcare, any SOC 2 / HIPAA buyer |
| **Enterprise** | $999 | Up to 10 domains, prioritized queue, retest included in 30 days, phone debrief | Larger SMB, MSP white-label |
| **Retest Add-on** | $99 | Re-run Standard/Professional scan after remediation | Upsell for compliance validation |

### CAC and LTV

| Metric | Estimate | Basis |
|---|---|---|
| Blended AOV | $350 | Mix of Standard and Professional tiers |
| Repeat purchase rate (Year 1) | 40% | Annual re-scan for insurance renewal, compliance |
| LTV (2-year) | $490 | $350 + 40% × $350 |
| CAC via cold outreach | $30–60 | ~3 hours at $20/hr + tools; 10% outreach-to-trial conversion |
| CAC via MSP channel | $50–100 | Rev share: 20% to referring partner |
| CAC via content/SEO | $15–30 | Lower bound; slower to build |
| **LTV:CAC ratio** | **8–16x** | Healthy; SaaS benchmark is >3x |

### Path to $1M ARR

- 238 customers/month at $350 AOV = $1M ARR
- At 1% outreach conversion and 200 cold emails/day: ~2 customers/day → ~$1M ARR within 12 months
- With MSP channel adding 50+ customers/month: achievable in 6–9 months

---

## 6. Customer Acquisition

### Strategy 1: Scan-First Cold Outreach (Primary, Months 1–3)

The most powerful GTM motion for this business is *showing, not telling*: identify websites with detectable security issues using passive/public tools (Shodan, SSL Labs grade lookups, security header checks — all of which do not require target permission), then reach out with a truncated proof-of-value report.

**Critical legal note:** The pre-outreach intelligence gathering uses only *passive, non-invasive public tools* that do not interact directly with the target's infrastructure beyond what a normal browser request would do. No active scanning occurs without explicit written consent (see Section 7).

**Workflow:**
1. Use Shodan or similar to identify domains with poor SSL grades or missing headers (public data, no authorization required)
2. Run free SecurityHeaders.io check (public service, no authorization required)
3. Compose outreach email: "I ran a quick public security check on your site and found 3 issues that could affect your cyber insurance renewal. Here's a 1-page summary — would a full automated assessment for $349 be useful?"
4. Attach 1-page teaser showing 2–3 findings (headers/SSL only — no active scan findings without permission)
5. Full scan only runs *after* customer completes checkout and digitally signs the authorization form

**Target lists:**
- E-commerce stores on Shopify/WooCommerce (identifiable via technology fingerprinting)
- Healthcare practices (HIPAA regulated; identifiable via booking software signatures)
- SaaS companies (Product Hunt, AngelList, SaaStr audience)
- New businesses applying for cyber insurance (broker partnerships)

### Strategy 2: MSP and IT Consultant Partnerships (Months 2–6)

Managed Service Providers are a force multiplier. A single MSP managing 50 SMB clients is 50 potential customers.

**Partnership structure:**
- 20% revenue share on each scan sold through the MSP
- White-label option at $999/month flat fee for unlimited scans (for MSPs with 10+ clients/month)
- MSP gets branded PDF reports they can resell at their discretion
- Target: 10 MSP partners by Month 6, each referring 5 scans/month = 50 customers/month from channel alone

**Outreach:**
- ConnectWise and Kaseya community forums
- IT Nation conference (ConnectWise annual event)
- CompTIA ChannelCon

### Strategy 3: Cyber Insurance Broker Referral Network (Months 4–12)

Cyber insurance brokers are the highest-conversion referral channel. When a broker tells an SMB "you need a security scan to get this policy," the SMB buys.

- Target independent insurance brokers who write cyber policies (there are ~10,000 in the US)
- Offer $50–100 referral fee per completed scan
- Provide brokers with a co-branded landing page
- Compliance angle: "Get your Cyber Insurance Pre-Assessment — required by most carriers"

### Strategy 4: Content and SEO (Months 3–12)

- Target keywords: "cyber security report for small business," "HIPAA security assessment cost," "PCI DSS vulnerability scan," "web security assessment SMB"
- Publish free resources: "Security Header Checker," "Free SSL Grade Lookup" (thin tools that demonstrate value and collect email)
- Case studies: anonymized before/after reports

---

## 7. Technical Architecture

### Scanner Stack

| Tool | Role | License | Key Specs |
|---|---|---|---|
| **Nuclei** | Primary vulnerability scanner | MIT (open-source core) | 27,500+ GitHub stars; YAML templates for CVEs, misconfigs, exposed panels, default creds; supports HTTP, DNS, TCP, SSL, JS protocols; parallel processing with zero false-positive design |
| **OWASP ZAP** | DAST — OWASP Top 10 | Apache 2.0 | Active + passive scan; authenticated scanning with session handling; REST API for automation |
| **SSL Labs API** | TLS/SSL grading | Free (non-commercial); commercial terms via Qualys | A–F grading, cipher suite analysis, certificate chain validation |
| **SecurityHeaders.io** | HTTP security headers | Free public API | Checks CSP, HSTS, X-Frame-Options, X-Content-Type-Options, Referrer-Policy, Permissions-Policy |
| **Claude API** | AI narration | Anthropic commercial | Report generation, business risk translation, remediation guidance |

### CRITICAL: Legal Authorization Framework

**Unauthorized scanning is a federal crime under the Computer Fraud and Abuse Act (CFAA), 18 U.S.C. § 1030, and equivalent laws in the UK (Computer Misuse Act 1990), EU (NIS2), and Australia (Criminal Code Act 1995).** This is the single most important architectural decision in this business.

**Authorization Gate — Non-Negotiable Design Requirement:**

1. **Checkout flow includes mandatory authorization form** before any payment is processed
   - Customer inputs target domain(s)
   - Customer digitally signs (e-signature via DocuSign, HelloSign, or embedded in checkout): "I hereby authorize [Company Name] to perform automated security scanning of the domain(s) listed above. I confirm that I am the owner or have explicit written permission from the owner to authorize this scan."
   - Signature is timestamped, stored in immutable audit log (S3 + SHA-256 hash)
   - No scan job is enqueued until authorization record is confirmed in database

2. **Domain ownership verification (belt + suspenders)**
   - Before scan starts, system verifies customer owns or controls the domain via one of:
     - DNS TXT record challenge (similar to SSL certificate issuance)
     - File placement verification (upload a token to `/.well-known/security-scan-auth.txt`)
     - WHOIS email verification (email to registrant address on file)
   - This verification step prevents fraudulent scanning even if a bad actor fraudulently completes the authorization form

3. **Scan rate limiting and politeness controls**
   - Respect `robots.txt` for crawling components (ZAP spider)
   - Cap request rate at 10 req/sec per target to avoid DoS characterization
   - Scan windows default to business hours; customer can opt into off-hours scanning
   - Immediate scan abort if target returns 429 (rate limit) or shows signs of distress

4. **Legal review before launch**
   - Engage a cybersecurity attorney to review authorization language (estimate: $1,500–3,000 one-time)
   - Obtain E&O (Errors & Omissions) insurance — $500–1,500/year for a solo operation
   - Terms of Service must clearly disclaim that the report reflects findings at a point in time and does not constitute a guarantee of security

### MVP Scope (5-Day Build)

**Day 1:** Auth flow + domain verification + Nuclei integration (50 core templates)
**Day 2:** SSL Labs + SecurityHeaders APIs + finding normalization schema
**Day 3:** Claude API integration — prompt engineering for executive summary + per-finding narration
**Day 4:** PDF generation (WeasyPrint template) + S3 delivery + Stripe checkout
**Day 5:** End-to-end test on 3 real domains (own domains or pre-consented test targets), authorization form legal review, deploy to production

---

## 8. 5-Day Execution Plan

### Day 1 — Foundation and Legal Gate

- [ ] Register LLC or sole proprietor entity; open business bank account
- [ ] Purchase domain (e.g., scansafe.io, quicksecure.io, smbreport.io)
- [ ] Draft authorization form and Terms of Service (use cybersecurity attorney template as base)
- [ ] Set up AWS account: EC2 (t3.medium for scanner), S3 (report storage), SES (email delivery), RDS (PostgreSQL for job queue and auth records)
- [ ] Install Nuclei, OWASP ZAP on EC2; configure nuclei-templates repository
- [ ] Build job queue (SQS or Redis) for scan jobs
- [ ] Define unified finding schema (JSON): `{id, severity, title, description, evidence, cve_id, cvss_score, remediation, compliance_refs}`

### Day 2 — Scanner Pipeline

- [ ] Wire Nuclei CLI to job queue; capture JSON output; normalize to finding schema
- [ ] Integrate OWASP ZAP REST API; run active scan; parse XML/JSON output; normalize to same schema
- [ ] Integrate SSL Labs API; map grade + findings to schema
- [ ] Integrate SecurityHeaders.io; parse response; map to schema
- [ ] Deduplication logic: deduplicate findings by (target, finding_type, location) across all scanners
- [ ] End-to-end test: run full pipeline on a pre-consented test domain; verify all 4 data sources produce normalized output

### Day 3 — AI Narration Layer

- [ ] Design Claude prompt template: inputs = (findings JSON, target domain, industry vertical, tier), outputs = (executive_summary, [per_finding_narrative], remediation_plan, compliance_notes)
- [ ] Prompt engineering for tone calibration: "Business owner" vs. "Technical IT manager" modes
- [ ] Test prompt against 20+ diverse finding sets; refine until executive summary reads at 8th-grade level
- [ ] Add retry logic and fallback for Claude API failures (store raw findings; regenerate narration on retry)
- [ ] Cost validation: verify actual token usage per scan is within budget model ($2–4 target)

### Day 4 — Report Assembly and Commerce

- [ ] Design PDF template in WeasyPrint/Jinja2: cover page, executive summary, findings table, detail pages, remediation checklist, compliance appendix
- [ ] Wire AI narration output into PDF template
- [ ] Screenshot capture for critical findings (Playwright headless browser)
- [ ] Set up Stripe checkout: 4 SKUs (Starter/Standard/Professional/Enterprise) + Retest add-on
- [ ] Build authorization form in checkout flow (e-signature embedded or DocuSign link)
- [ ] Domain verification challenge system (DNS TXT or file-based)
- [ ] Delivery: post-scan job stores PDF to S3 pre-signed URL, sends email via SES with download link

### Day 5 — Testing, Hardening, and Launch

- [ ] Full end-to-end test: purchase → authorization → domain verification → scan → narration → PDF delivery; target: <30 minutes total
- [ ] Test on 3 pre-consented domains (own domains + 1 friendly SMB who volunteers)
- [ ] Security hardening of the scanner infrastructure itself: no inbound ports except HTTPS, scan worker is isolated from web tier, auth audit log is write-only
- [ ] Set up basic monitoring: CloudWatch alerts for scan failures, queue depth, API errors
- [ ] Launch: post on HackerNews (Show HN), post on r/entrepreneur and r/smallbusiness, send 50 cold emails to e-commerce prospects identified via Shodan SSL grade check
- [ ] Publish landing page with sample report (anonymized) as social proof

---

## 9. Risk Matrix

| # | Risk | Probability | Impact | Severity | Mitigation |
|---|---|---|---|---|---|
| 1 | **Legal: Unauthorized scan claim** | Medium | Catastrophic | **CRITICAL** | Hard authorization gate + domain ownership verification + cybersecurity attorney review + CFAA-compliant ToS. Maintain immutable audit log of every authorization. Never scan without confirmed auth record. |
| 2 | **Legal: Liability for missed vulnerabilities** | Medium | High | **HIGH** | E&O insurance. Clear ToS disclaimers: "Point-in-time assessment, not a security guarantee." Disclaim liability for zero-days and vulnerabilities outside scan scope. Recommend professional pentest for high-risk environments. |
| 3 | **False positive damage** | Medium | High | **HIGH** | Tune Nuclei templates conservatively; disable templates with known high false-positive rates. Include confidence scoring in output. Report language: "Potential issue detected — verify before remediation." Consider human review tier for Professional/Enterprise. |
| 4 | **Scanner weaponization** | Low | High | **HIGH** | Domain ownership verification prevents third-party abuse. Rate limiting prevents DoS. Isolated scanner infrastructure. Monitor for unusual job patterns (bulk submissions, non-owned domains). |
| 5 | **Competitive response from incumbents** | Low | Medium | **MEDIUM** | Detectify and Intruder are VC-backed and will eventually target this price point. First-mover advantage, MSP channel relationships, and reputation are the durable moats. Focus on compliance report format differentiation — incumbents output dashboards, not auditor-ready PDFs. |

### Additional Risks Worth Monitoring

| Risk | Notes |
|---|---|
| Claude API price increase | Anthropic has raised and lowered prices; build multi-model fallback (GPT-4o as backup) |
| Nuclei template licensing change | Core Nuclei is MIT; commercial templates require ProjectDiscovery license; plan for this cost |
| SMB credit card fraud | Use Stripe Radar; require domain verification before scan runs |
| Reputational risk if scan causes target instability | Scan rate limiting + robots.txt respect + customer education on scan timing |

---

## 10. VC Stress Test: 5 Hardest Questions

### Q1: "Isn't running automated security scans on websites illegal without authorization? How do you ensure you never get sued or prosecuted?"

**The full answer:**

Yes — unauthorized scanning is a federal crime under the CFAA (18 U.S.C. § 1030), punishable by up to 5 years imprisonment per count. This is the existential risk of this business, and the question deserves a complete answer rather than a dismissal.

Our legal framework has three layers: **(1) Explicit digital authorization** — no scan job enters the queue without a timestamped, stored e-signature from the customer attesting they own or are authorized to test the target domain. **(2) Domain ownership verification** — we independently verify domain control via DNS TXT challenge or file placement before any active scan runs, eliminating the scenario where a bad actor fraudulently claims permission to scan someone else's domain. **(3) Legal review and E&O insurance** — authorization language is reviewed by a cybersecurity attorney; E&O policy covers errors in assessment.

The analogy is a locksmith: a locksmith who breaks into a house is a burglar; a locksmith hired by the homeowner is providing a legal service. We are the locksmith. The authorization framework is our proof of hire. Companies including HackerOne, Bugcrowd, Synack, and every major vulnerability scanner on the market operate under equivalent frameworks.

The remaining risk is a customer who lies about domain ownership. Domain verification makes this extremely difficult and creates a clear legal defense: we took reasonable steps to verify authorization, and any fraud was committed by the customer, not us.

### Q2: "Nuclei and OWASP ZAP are open-source and free. Why won't SMBs just run these themselves?"

They won't, for the same reason they don't file their own taxes using TurboTax's raw API. The barrier is not cost — it is:

- **Setup complexity**: Running Nuclei + ZAP in a controlled environment requires Linux command-line comfort, Docker knowledge, and configuration tuning. Most SMB owners have none of these.
- **Template curation**: Nuclei has 9,000+ templates. Running all of them is noisy, slow, and produces hundreds of false positives. Knowing which 500 templates are high-signal requires security expertise.
- **Output interpretation**: Both tools produce raw JSON/XML. An SMB owner looking at a Nuclei output file has no idea what "CVE-2021-41773 RCE via path traversal" means for their business, what it costs to fix, or whether it affects their PCI-DSS scope.
- **Report generation**: There is no compliance-ready PDF at the end of a Nuclei run.

We sell the *interpretation and delivery*, not the scanning. The tools are the raw material. Our value is the same as H&R Block: they use TurboTax too.

### Q3: "This looks like a one-time purchase business, not a recurring revenue business. How do you build a defensible company?"

Three mechanisms create recurring revenue:

1. **Annual re-scan**: Cyber insurance renewals are annual. PCI-DSS requires at least annual assessments. SOC 2 requires periodic evaluation. We build a renewal reminder workflow that converts 40%+ of customers into annual repeats at the same or higher price point.

2. **MSP white-label subscriptions**: MSPs paying $999/month flat fee for unlimited scans are recurring revenue. At 50 MSP partners, this is $600K ARR before a single retail sale.

3. **Continuous monitoring upsell**: The natural evolution from "one-time report" is "quarterly report" or "monthly change monitoring." Once the technical infrastructure is built, subscription tiers are incremental engineering work. Detectify charges €90/month for this; our SMB base will pay $49–79/month for a stripped-down continuous version.

The one-time product is a customer acquisition tool. The real business is the annual renewal + MSP channel.

### Q4: "How do you compete when Intruder, Detectify, or a well-funded startup decides to launch a $299 one-time report product?"

The honest answer is: at sufficient funding, a competitor can replicate the technical stack in 3 months. Our moat is not technical — it is distribution and trust.

- **MSP relationships are sticky**: An MSP embedded in our white-label program has trained their staff, customized their pricing, and built client expectations around our report format. Switching costs are real.
- **Compliance report formats are institutional**: Once a particular report format is accepted by an insurance underwriter or a PCI-DSS auditor, it becomes the de facto standard for that customer base. This is why Qualys has kept enterprise customers for 20+ years despite cheaper alternatives.
- **Brand credibility in SMB security takes time to build**: A well-funded startup entering the space in Year 2 faces 12–18 months of brand building against our established case studies, testimonials, and channel relationships.
- **Incumbents (Detectify, Intruder) are optimized for a different buyer**: Their product, pricing, and sales motion are built for tech-savvy teams with monthly budgets, not for the insurance-renewal SMB. Pivoting to serve our buyer would require repositioning their entire brand.

Speed of execution in the first 18 months is the primary defensibility strategy.

### Q5: "What happens when you find a critical vulnerability in a customer's website — are you liable if they get breached before they fix it?"

This is a real liability question that the ToS must address explicitly. Our position:

- The report is a *point-in-time assessment*, not a warranty or guarantee of security
- Delivery of the report constitutes fulfillment of service; we have no ongoing monitoring obligation unless explicitly purchased
- We strongly recommend in every report that Critical and High findings be remediated within 24–72 hours, and we provide specific remediation steps
- E&O insurance covers the scenario where our tool *missed* a vulnerability that was later exploited; we are not liable for vulnerabilities we *found and reported* that the customer chose not to fix
- Our ToS includes a clear limitation of liability clause capping damages at the price paid for the report

The liability exposure runs in one direction: missed vulnerabilities (false negatives), not found-but-unfixed vulnerabilities. Accurate scanning and conservative severity ratings (prefer over-reporting to under-reporting) mitigate the false-negative risk.

---

## 11. GO/NO-GO with Conditions

### Decision: **CONDITIONAL GO**

### GO Conditions — All Must Be Met Before First Production Scan

| Condition | Why Non-Negotiable |
|---|---|
| **Legal review of authorization language** by a cybersecurity/tech attorney | CFAA liability is catastrophic and irreversible; $1,500–3,000 one-time cost is the best investment in this business |
| **Domain ownership verification** implemented and tested before checkout enables scan | Prevents weaponization against third parties; provides legal defense against fraudulent authorization claims |
| **E&O insurance policy bound** | Missed-vulnerability liability is real; policy is $500–1,500/year and essential |
| **ToS includes clear limitations of liability** (point-in-time, no guarantee) | Sets customer expectations; limits legal exposure |
| **Scan rate limiting and robots.txt compliance** implemented | Prevents DoS characterization; demonstrates good-faith effort |

### GO With Eyes Open — Accept These Constraints

| Constraint | Management Approach |
|---|---|
| **This is not a VC-scale business at $200–$1,000 one-time** | That's fine — this is a high-margin, low-overhead lifestyle/SMB business targeting $1–5M ARR in Years 1–3, with a potential channel/MSP path to $10M+ |
| **Recurring revenue requires active development of MSP channel and renewal workflow** | Build these in Months 2–4; do not let Year 1 become purely transactional |
| **Competitor entry is a when, not an if** | Execution speed, MSP relationships, and compliance format standardization are the only durable moats |
| **Scanner false positives damage credibility** | Invest in template curation and conservative severity scoring; reputation in SMB security is slow to build and fast to lose |

### NO-GO Triggers — Stop Immediately If Any Occur

- Attorney advises that authorization framework is insufficient under CFAA or applicable state law
- Domain verification is technically infeasible for a meaningful percentage of targets (>20%)
- E&O insurance is unavailable or cost-prohibitive for this business model
- Competitive analysis reveals an already-funded player has launched an identical product in the last 6 months at the same price point

### Final Recommendation

**Build the MVP in 5 days. Do not run a single production scan until the authorization framework and domain verification are complete and attorney-reviewed. Launch with the cold outreach GTM. Sign the first 10 customers within 30 days. If conversion rate on cold outreach exceeds 1%, scale the outreach. If it is below 0.5%, pivot to MSP partnership as primary channel before spending further on outreach infrastructure.**

The market is real. The price gap is real. The compliance tailwind is real. The unit economics are exceptional. The legal risk is manageable. This is a GO.

---

*Report prepared by: Strategic Analysis, March 15, 2026*
*Data sources: Grand View Research (cybersecurity market size 2025), IBM Cost of a Data Breach Report 2025, Verizon DBIR 2025, Detectify and Intruder public pricing pages, Accenture Cost of Cybercrime Study, SBA small business data, CFAA 18 U.S.C. § 1030, ProjectDiscovery/Nuclei GitHub repository*
