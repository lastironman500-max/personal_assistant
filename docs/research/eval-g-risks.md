# Risk Analysis: AI-Powered WCAG Accessibility Audit Business

**Date:** 2026-03-15
**Analyst:** Risk Assessment — AI Accessibility Audit Venture
**Scope:** Full risk register covering legal, quality, business, technical, market, and ethical dimensions

---

## Risk Register Summary

| ID | Category | Risk | Likelihood | Impact | Priority |
|----|----------|------|-----------|--------|----------|
| L1 | Legal | Legality of scanning public websites | Low | High | Medium |
| L2 | Legal | Liability if report misses issues and client is sued | Medium | High | High |
| L3 | Legal | No professional liability insurance | Medium | High | High |
| L4 | Legal | CAN-SPAM non-compliance for cold emails | Medium | Medium | Medium |
| L5 | Legal | GDPR implications of scanning EU sites | Medium | High | High |
| Q1 | Quality | axe-core ~57% coverage is insufficient | High | High | Critical |
| Q2 | Quality | Client relies on report and still gets sued | Medium | High | High |
| Q3 | Quality | Automated vs. manual audit expectations mismatch | High | Medium | High |
| Q4 | Quality | Inadequate disclaimer language | Medium | High | High |
| B1 | Business | No replies to cold outreach | High | High | Critical |
| B2 | Business | Competitors copy the model immediately | Medium | Medium | Medium |
| B3 | Business | axe-core or WCAG standards change | Low | Medium | Low |
| B4 | Business | Claude API pricing changes or downtime | Medium | High | High |
| B5 | Business | Cash flow collapse on $100 budget | High | High | Critical |
| T1 | Technical | Websites blocking automated scanning | High | Medium | High |
| T2 | Technical | SPAs are hard to crawl accurately | High | Medium | High |
| T3 | Technical | Dynamic content invisible to axe-core | High | Medium | High |
| T4 | Technical | Rate limiting from target websites | Medium | Low | Low |
| M1 | Market | Accessibility is a "vitamin" not "painkiller" | Medium | High | High |
| M2 | Market | ADA enforcement slows down | Low | High | Medium |
| M3 | Market | Free tools get good enough | Medium | Medium | Medium |
| M4 | Market | Market timing risk | Medium | Medium | Medium |
| E1 | Ethical | Fear-mongering about lawsuits | Medium | Medium | Medium |
| E2 | Ethical | Selling automated reports at human-audit prices | High | High | Critical |
| E3 | Ethical | Lack of transparency about AI involvement | Medium | High | High |

---

## 1. Legal Risks

### L1 — Legality of Scanning Public Websites

**Likelihood:** Low | **Impact:** High

**Analysis:** Scanning publicly accessible websites is generally legal under U.S. law. The landmark *hiQ Labs v. LinkedIn* Ninth Circuit rulings (2019, 2022) held that scraping publicly accessible data does not violate the Computer Fraud and Abuse Act (CFAA), since the CFAA requires "unauthorized access" and public pages carry no access restriction. The Supreme Court's *Van Buren v. United States* (2021) also narrowed CFAA scope. Accessibility auditing tools (axe-core, WAVE, Lighthouse) have operated publicly for years without legal challenge.

**Why it remains legal in our context:**
- We are reading publicly served HTML/CSS/JS — the same data any browser receives
- We are not bypassing authentication, extracting private user data, or circumventing technical access controls
- We are not storing scraped content for resale; we are analyzing structural properties of the page
- Our purpose (auditing for accessibility compliance) is a legitimate, socially beneficial use

**Mitigation:**
- Document legal basis in internal policy (hiQ Labs, Van Buren, Restatement of Torts § 652)
- Add Terms of Service to our own site clarifying scanning methodology
- Do NOT crawl pages behind login walls or scan at rates that could constitute a DoS attack
- Consult a technology attorney once revenue permits (~$500–$1,000 flat fee for a written opinion)
- Avoid scraping robots.txt-disallowed paths (even though not legally binding, it signals good faith)

**Residual Risk:** Very Low. This is the most legally settled of all risks in this register.

---

### L2 — Liability If Report Misses Issues and Client Gets Sued

**Likelihood:** Medium | **Impact:** High

**Analysis:** A client could theoretically claim that our report gave them a "clean bill of health," they relied on it, and they subsequently faced an ADA lawsuit. This is a negligence or professional malpractice claim. The key questions are: (a) did we make an express or implied warranty of completeness? (b) did the client reasonably rely on our report as a guarantee? (c) was there proximate causation?

**Mitigation:**
- **Contractual limitation of liability:** Cap damages at the amount paid for the report (standard SaaS/professional services practice)
- **Explicit scope disclaimer in every report:** "This automated analysis detects approximately 30–57% of potential WCAG 2.1 issues. It does not constitute a legal opinion, a complete manual audit, or a guarantee of ADA/Section 508 compliance."
- **No express warranties:** Never write "your site is compliant" — write "issues detected" and "issues not detected by automated tools"
- **Engagement letter / Terms of Service** signed before delivery
- **Professional liability (E&O) insurance** (see L3)

**Residual Risk:** Low-Medium. With proper contractual language and insurance, exposure is manageable. The main residual risk is reputational, not financial.

---

### L3 — No Professional Liability (E&O) Insurance

**Likelihood:** Medium | **Impact:** High

**Analysis:** Operating without errors and omissions (E&O) insurance means a single claim — even a frivolous one — could result in out-of-pocket legal defense costs ($10,000–$50,000+), even if we ultimately prevail. With a $100 starting budget this is a genuine bootstrapping constraint.

**Mitigation:**
- **Phase 1 (pre-revenue):** Operate under strict contractual disclaimers and limitation of liability clauses; keep client base small
- **Phase 2 (first revenue):** Obtain E&O insurance immediately. Small tech consultancy E&O policies start at ~$500–$1,200/year for $1M coverage (providers: Next Insurance, Hiscox, Embroker)
- Frame obtaining insurance as a milestone in the 90-day plan — tied to first paying client
- Consider LLC formation immediately (even a single-member LLC) to separate personal assets from business liability (~$50–$200 state filing fee)

**Residual Risk:** Low once insurance and LLC are in place. High during the uninsured bootstrapping phase, mitigated primarily by contractual language.

---

### L4 — CAN-SPAM Compliance for Cold Emails

**Likelihood:** Medium | **Impact:** Medium

**Analysis:** The CAN-SPAM Act (U.S.) applies to commercial email. Violations carry penalties of up to $51,744 per email. Key requirements: (1) honest subject lines, (2) physical mailing address, (3) clear opt-out mechanism, (4) honor opt-outs within 10 business days, (5) no deceptive headers.

**Mitigation:**
- Use a legitimate from address (no spoofing)
- Include physical address (can be a P.O. box or registered agent address — ~$10–$20/month)
- Include one-click unsubscribe in every cold email
- Use a cold email platform with built-in compliance (Apollo, Instantly, Lemlist) — all include unsubscribe handling
- Keep records of opt-outs in a suppression list
- For EU prospects, note that GDPR (see L5) is stricter than CAN-SPAM and requires opt-IN consent for B2B email in many member states

**Residual Risk:** Low. CAN-SPAM compliance is operationally simple with the right tooling. Primary risk is negligence in setup, not deliberate violation.

---

### L5 — GDPR Implications of Scanning EU Sites

**Likelihood:** Medium | **Impact:** High

**Analysis:** GDPR applies to the processing of personal data of EU residents. Two questions arise: (1) Does scanning EU websites constitute processing of personal data? (2) Does sending cold emails to EU business contacts violate GDPR?

For scanning: If we crawl pages that display personal data (names, emails in HTML source), we are technically processing it. However, we are analyzing structural HTML properties, not storing or using that personal data.

For cold email: GDPR's ePrivacy Directive (implemented variably across EU member states) generally requires opt-in consent for unsolicited B2B email in countries like Germany, France, and the Netherlands. The UK has similar rules under PECR post-Brexit.

**Mitigation:**
- **Scanning:** Do not store any personal data found during crawls. Discard HTML content after analysis; only retain the axe-core violation report. Document this data handling practice in a privacy policy.
- **Cold email:** Segment EU prospects and apply country-specific rules. For Germany/France/Netherlands, consider LinkedIn outreach (where you have a connection basis) rather than cold email.
- Publish a privacy policy on the business website before any EU outreach
- Appoint a GDPR data point of contact (can be the founder) and document data processing activities
- Do not use US-only email tools for EU contacts without confirming EU data transfer compliance (check Standard Contractual Clauses)

**Residual Risk:** Medium. GDPR compliance for a bootstrapped operation is resource-intensive. Primary residual risk is EU cold email; mitigated by focusing initial outreach on U.S. market and deferring EU expansion until a GDPR-compliant workflow is in place.

---

## 2. Quality Risks

### Q1 — axe-core Only Catches ~57% of WCAG Issues

**Likelihood:** High (this is a documented limitation, not a probability) | **Impact:** High

**Analysis:** Deque Systems, the creator of axe-core, publicly states automated tools can catch approximately 57% of WCAG issues. The remaining ~43% require human judgment: color contrast in complex images, meaningful alt text quality, logical reading order, cognitive accessibility, keyboard navigation flows, and screen reader compatibility. If we sell reports framed as "accessibility audits" without this caveat, we are materially misrepresenting our product.

**Mitigation:**
- **Reframe the product:** Do not call it an "audit." Call it an "Automated Accessibility Scan" or "WCAG Issue Detection Report"
- **Quantify coverage in marketing:** "Detects 57%+ of detectable WCAG issues automatically" — this is honest and still compelling
- **Tiered product structure:**
  - Tier 1: Automated scan report (our core product, $X)
  - Tier 2: Automated scan + manual review checklist (premium, $Y)
  - Tier 3: Refer to partner manual auditors for full audits (affiliate/referral revenue)
- **Report includes explicit gap disclosure:** Section in every report: "Issues automated tools cannot detect — manual review required for: [list]"
- Use this limitation as a sales tool: "We found 47 issues in 10 minutes. Imagine what a 20-hour manual audit reveals. Here's your starting point."

**Residual Risk:** Low. Once the product is correctly framed and scoped, the 57% limitation becomes a feature (speed, cost, accessibility) rather than a liability.

---

### Q2 — Client Relies on Report and Still Gets Sued

**Likelihood:** Medium | **Impact:** High

**Analysis:** Even with disclaimers, a client could overestimate their compliance based on our report, skip manual remediation, and face an ADA lawsuit. This creates reputational damage for us even if we are not legally liable.

**Mitigation:**
- Every report must include a "Next Steps" section recommending manual review and remediation
- Report language should make clear: "Fixing these issues reduces but does not eliminate ADA lawsuit risk"
- Offer a remediation roadmap service (upsell) that explicitly tracks issue resolution
- Build a follow-up workflow: 30-day check-in asking if client has begun remediation
- Consider offering a "certified remediation" badge only after manual verification — not just after scan

**Residual Risk:** Low-Medium. Reputational risk remains if a client ignores recommendations and faces a lawsuit. Mitigated by clear documentation of advice given.

---

### Q3 — Automated vs. Manual Audit Expectations Mismatch

**Likelihood:** High | **Impact:** Medium

**Analysis:** Many buyers will not understand the difference between an automated scan and a WCAG expert audit. If we do not set expectations proactively, we will have frustrated clients and chargeback risk.

**Mitigation:**
- Sales process must include a one-paragraph plain-English explanation of what the report covers and does not cover
- Onboarding email with report delivery explains the scope
- FAQ on website: "Is this a full accessibility audit?" — answered honestly with "No, here's what it is and isn't"
- Train any salespeople or outreach sequences to include scope language upfront

**Residual Risk:** Low. Expectation management is an operational discipline. Consistent messaging resolves this.

---

### Q4 — Inadequate Disclaimer Language

**Likelihood:** Medium | **Impact:** High

**Analysis:** Boilerplate disclaimers that no one reads do not constitute meaningful notice. Courts have looked unfavorably on disclaimers buried in terms of service when they contradict the marketing claims made to close the sale.

**Mitigation:**
- Disclaimer must appear:
  1. On the sales/marketing page (above the fold or immediately adjacent to pricing)
  2. In the engagement letter / Terms of Service (signed before delivery)
  3. On the cover page of every report
  4. In the report's executive summary
- Language review by an attorney before launch (one-time cost, ~$200–$500)
- Avoid superlatives in marketing ("complete," "comprehensive," "guaranteed compliance") that contradict disclaimers

**Residual Risk:** Low. This is a copy and legal review task with well-established precedent from similar SaaS/consulting businesses.

---

## 3. Business Risks

### B1 — No Replies to Cold Outreach

**Likelihood:** High | **Impact:** High

**Analysis:** Cold email and LinkedIn outreach have industry-average reply rates of 2–8%. At the low end, 100 emails = 2 replies. For a $100-budget operation, acquiring the first paying client through cold outreach is the single largest execution risk. The business fails if pipeline never converts.

**Mitigation:**
- **Hyper-personalization:** Every cold email must reference a specific accessibility issue found on the recipient's site (our scanner-as-lead-gen model). "I scanned your site and found 47 issues — here are the top 3" is radically more effective than generic outreach.
- **Vertical focus:** Pick one vertical (e.g., law firms, e-commerce, healthcare) where ADA lawsuit risk is documented and quantifiable. Specific verticals have specific watering holes.
- **Multi-channel:** Email + LinkedIn connection request + LinkedIn DM. Three touchpoints per prospect.
- **Follow-up sequence:** 5-touch sequence over 14 days. 80% of replies come after the second follow-up.
- **Offer a free sample:** Send a 2-page excerpt of their actual scan report in the first email. This converts curiosity into a conversation.
- **Track and iterate:** After 50 sends, evaluate subject line open rates, reply rates, and adjust. Treat outreach as a conversion optimization problem.

**Residual Risk:** Medium. Even with excellent execution, cold outreach has inherent uncertainty. The mitigation is to run outreach in parallel with content marketing (LinkedIn posts about accessibility, SEO) to build inbound over 60–90 days.

---

### B2 — Competitors Copy the Model Immediately

**Likelihood:** Medium | **Impact:** Medium

**Analysis:** The barriers to entry for "run axe-core + write a report with Claude" are low. Any developer could replicate the technical stack in a weekend. Our defensibility is not the technology.

**Mitigation:**
- **Defensibility is relationships, brand, and workflow:** The first 20 clients become case studies, testimonials, and referral sources. These are not copyable.
- **Build proprietary data moat:** Track remediation outcomes, benchmark by industry vertical, build a database of "typical issues for X industry." This data becomes proprietary IP.
- **Speed to market:** First-mover advantage in a specific niche (e.g., "the accessibility audit firm for law firms") creates brand association that is difficult to displace
- **Proprietary scoring model:** Develop a branded "Accessibility Risk Score" that becomes recognized and differentiated
- Do not fear competition — validate it. Competitors entering means the market is real.

**Residual Risk:** Medium. This is an inherently competitive space. Long-term defensibility requires continuous product differentiation. Accept this risk and compete on execution.

---

### B3 — axe-core or WCAG Standards Change

**Likelihood:** Low | **Impact:** Medium

**Analysis:** WCAG 2.2 was released in October 2023. WCAG 3.0 is in development and will introduce a substantially different conformance model. axe-core updates regularly. A major WCAG version change could render our reports outdated or require significant rework.

**Mitigation:**
- Subscribe to W3C WAI mailing list and monitor WCAG 3.0 working drafts
- Abstract our report generation layer from the scanning engine — if axe-core is swapped for a different library, the report format should not change
- Frame WCAG 3.0 transition as a business opportunity: "Your current audit is based on WCAG 2.2 — here's what changes under WCAG 3.0" is a natural upsell/re-engagement campaign
- axe-core is maintained by Deque Systems with enterprise backing; the risk of abandonment is low

**Residual Risk:** Low. Standards changes are slow (years of notice) and well-telegraphed. This is manageable with basic monitoring.

---

### B4 — Claude API Pricing Changes or Downtime

**Likelihood:** Medium | **Impact:** High

**Analysis:** Our report generation relies on Claude API. A 2x price increase directly compresses margins. Extended downtime during a client delivery creates fulfillment failure. Vendor lock-in to a single AI provider is a structural fragility.

**Mitigation:**
- **Multi-provider architecture:** Design the AI layer to be swappable. Maintain prompt compatibility with OpenAI GPT-4o and Google Gemini Pro as fallbacks. The incremental engineering cost is low.
- **Pricing buffer:** Build AI costs into pricing with a 3–4x margin. If Claude costs $0.10/report today, charge as if it costs $0.40/report to create a buffer against price increases.
- **Monitor Anthropic pricing announcements:** Historically, AI API prices have decreased over time (GPT-4 2023 vs 2025 is ~10x cheaper), making this risk directionally favorable
- **Downtime SLA:** For client-facing SLAs, include a 24–48 hour delivery window — not real-time — to absorb API downtime events
- **Cache common outputs:** Generic findings descriptions and recommendations can be templated and cached, reducing per-report API spend

**Residual Risk:** Low-Medium. Multi-provider fallback is the key mitigation. Without it, this risk is High.

---

### B5 — Cash Flow Collapse on $100 Starting Budget

**Likelihood:** High | **Impact:** High

**Analysis:** $100 covers roughly: domain ($12/year) + email tool (free tier) + Claude API (~$20 credit) + axe-core (free/open source) + basic hosting (free tier). There is almost no margin for error, paid advertising, or extended runway without revenue.

**Mitigation:**
- **Revenue before spend:** Every tool purchase must be justified by a specific revenue action. No speculative tool purchases.
- **Free tier stack:** Vercel (free), GitHub Pages (free), axe-core (open source), Puppeteer (open source), Claude API (pay-per-use, not subscription), Apollo.io (free tier for 50 leads/month), HubSpot CRM (free tier)
- **First client is the funding round:** The business model must generate revenue from client #1 before spending beyond the initial $100. Price the first report at $197–$297 minimum.
- **Avoid common cash traps:** Do not pay for LinkedIn Sales Navigator, ZoomInfo, or other expensive prospecting tools until revenue justifies it
- **Weekly cash flow tracking:** With a $100 budget, track every dollar weekly. Know exactly when and how cash runs out.
- **Revenue milestone for each spend tier:** Define: "I will purchase X tool when I reach $Y in monthly recurring revenue"

**Residual Risk:** High during weeks 1–4. Drops to Low once first client pays. This is the existential risk of the early phase and must be treated as the #1 priority.

---

## 4. Technical Risks

### T1 — Websites That Block Automated Scanning

**Likelihood:** High | **Impact:** Medium

**Analysis:** Large enterprise sites, financial institutions, and government portals often deploy Web Application Firewalls (WAFs) such as Cloudflare, Akamai, or Imperva that block headless browsers and automated crawlers. CAPTCHAs on key pages prevent automated page loads. These sites are often the highest-value targets.

**Mitigation:**
- **Accept scope limitations:** If a site blocks scanning, document this in the report: "Pages protected by WAF/CAPTCHA could not be automatically scanned. Manual review required for these sections."
- **Use browser-based crawling with respectful delays:** Puppeteer/Playwright with realistic user-agent strings and 2–5 second delays between requests mimics human browsing and passes many WAF heuristics
- **Focus initial product on SMB websites:** Small and medium business sites (the primary target for ADA lawsuit risk) rarely deploy enterprise WAFs. The blocking problem is concentrated among large enterprises who have dedicated accessibility teams anyway.
- **Selective crawl:** Offer to scan specific URLs provided by the client rather than autonomous full-site crawls — this sidesteps WAF issues entirely for enterprise clients

**Residual Risk:** Medium for enterprise targets. Low for SMB targets. Since SMBs are the primary ICP, the practical residual risk is Low.

---

### T2 — Single-Page Applications (SPAs) Are Hard to Crawl

**Likelihood:** High | **Impact:** Medium

**Analysis:** React, Vue, Angular, and Next.js applications render content client-side via JavaScript. A basic HTTP crawler receives only a shell HTML document with minimal content. axe-core must run after full JavaScript execution and DOM rendering, or it will miss the majority of rendered content.

**Mitigation:**
- **Use Playwright or Puppeteer exclusively** (not basic HTTP fetch) — both execute JavaScript and wait for DOM hydration before running axe-core
- **Implement intelligent wait conditions:** Wait for `DOMContentLoaded` + additional idle network period (Playwright's `networkidle` option) before injecting axe-core
- **Test against SPA-heavy sites during QA:** Build a test suite that includes React, Vue, and Angular sample sites to verify scan accuracy
- **Disclose limitation in edge cases:** If a site uses particularly aggressive lazy-loading or infinite scroll, document in the report that only the initially rendered view was scanned

**Residual Risk:** Low with Playwright implementation. The tooling exists to solve this; it is an implementation discipline issue, not a fundamental limitation.

---

### T3 — Dynamic Content Invisible to axe-core

**Likelihood:** High | **Impact:** Medium

**Analysis:** Modal dialogs, dropdown menus, form validation errors, toast notifications, and other interactive states only exist in the DOM when triggered by user interaction. axe-core scanning the initial page load cannot detect accessibility issues in these states (e.g., a modal with no focus trap, an error message with no ARIA role).

**Mitigation:**
- **Disclose scope explicitly in reports:** "This scan analyzed the page in its default loaded state. Interactive states (modals, forms, dropdowns) require manual testing."
- **Offer interaction simulation as premium tier:** Use Playwright to click common interactive elements (buttons, form submissions) and run axe-core after each state change — this catches a meaningful percentage of dynamic content issues
- **Include a manual testing checklist:** Appendix in every report listing common interactive patterns that require human testing
- Treat dynamic content coverage as a roadmap item and differentiation story for premium pricing

**Residual Risk:** Medium. This is a fundamental limitation of static-state scanning that cannot be fully automated. Honest disclosure is the primary mitigation.

---

### T4 — Rate Limiting from Target Websites

**Likelihood:** Medium | **Impact:** Low

**Analysis:** Aggressive crawling (hundreds of requests per minute) triggers rate limiting or temporary IP blocks from target websites. This slows down scan completion but does not fundamentally prevent it.

**Mitigation:**
- Implement configurable crawl rate limits (default: 1–2 requests/second)
- Respect `Crawl-delay` in robots.txt
- For large sites (500+ pages), offer a sampled audit (top 50 pages by traffic) rather than full-site crawl
- Use residential proxy rotation for persistent rate-limit situations (providers: Bright Data, Oxylabs — cost: ~$0.10–0.50/GB)

**Residual Risk:** Low. Rate limiting is a solved problem with standard crawl delay configuration.

---

## 5. Market Risks

### M1 — Accessibility Auditing Is a "Vitamin" Not a "Painkiller"

**Likelihood:** Medium | **Impact:** High

**Analysis:** A vitamin is something people know they should buy but don't. A painkiller is something they buy because they're in pain. Businesses that have not been sued for ADA violations may view accessibility as optional. Without a lawsuit threat, the urgency to buy is low.

**Mitigation:**
- **Lead with the lawsuit data:** 4,600+ federal ADA lawsuits filed in 2023 targeting websites. Average settlement: $25,000–$75,000. This converts accessibility from a "nice to have" to a "need to have."
- **Target businesses in high-risk verticals:** E-commerce, healthcare, hospitality, financial services — industries with documented high ADA lawsuit frequency. These businesses are already in pain or know peers who are.
- **Target businesses post-lawsuit notification:** Demand letters from serial ADA litigants (law firms like Carlson Lynch, Seyfarth Shaw) are public record. Businesses that have received demand letters are experiencing acute pain and are the hottest possible leads.
- **Frame as insurance, not improvement:** "Spend $297 now or risk $25,000+ later" is a painkiller framing.

**Residual Risk:** Medium. The lawsuit-driven framing converts the category to a painkiller. Without this framing, the risk is High.

---

### M2 — ADA Enforcement Slows Down

**Likelihood:** Low | **Impact:** High

**Analysis:** ADA web accessibility lawsuits are driven primarily by private plaintiff firms, not DOJ enforcement. A shift in DOJ posture (e.g., deprioritizing ADA tech enforcement under a new administration) could reduce the urgency narrative. However, private right of action under ADA Title III does not require DOJ enforcement — plaintiff's attorneys continue filing regardless.

**Mitigation:**
- Do not anchor the entire value proposition on DOJ enforcement
- Emphasize private plaintiff litigation (which is independent of administration)
- Diversify messaging: accessibility is also an SEO factor, improves UX for 15% of population with disabilities, and is increasingly required by enterprise procurement standards (Section 508 for government contractors)
- Monitor: *National Federation of the Blind v. Target* (precedent), DOJ guidance updates, and state-level accessibility legislation (California, New York are state-level active)

**Residual Risk:** Low. Private plaintiff ADA litigation is largely independent of federal enforcement trends and has been increasing year-over-year since 2015.

---

### M3 — Free Tools Get Good Enough

**Likelihood:** Medium | **Impact:** Medium

**Analysis:** WAVE (WebAIM), Lighthouse, and browser extensions already offer free automated scanning. If these tools add AI-generated report generation, the gap between our product and free narrows. Google Lighthouse is already integrated into Chrome DevTools.

**Mitigation:**
- **Free tools require technical sophistication to interpret.** Our value is translating technical findings into business-language reports, prioritized remediation plans, and professional deliverables that non-technical decision-makers can act on.
- **Free tools don't send themselves as cold email lead-gen.** Our scanner-as-outreach model generates leads; the tool is not the product — the relationship and workflow are.
- **Move upmarket before commoditization:** Add manual review, remediation tracking, and ongoing monitoring before free tools replicate these features
- **Focus on full-service workflow:** Scan + report + prioritized fix list + re-scan after remediation = a workflow that free tools will not replicate

**Residual Risk:** Medium long-term, Low short-term (3–18 month window). The race is to establish brand and client relationships before commoditization reaches the SMB segment.

---

### M4 — Market Timing Risk

**Likelihood:** Medium | **Impact:** Medium

**Analysis:** Three timing scenarios: (1) Too early — market not ready to pay for this yet. (2) On time — ideal entry. (3) Too late — market saturated with established players.

**Evidence for "on time":**
- ADA web lawsuits peaked in 2022–2023 and remain elevated
- WCAG 2.2 released October 2023 creates immediate re-audit demand
- AI-generated professional reports are a new capability (2023–2024 vintage)
- Most SMBs have never received an accessibility audit — market penetration is low

**Evidence for "late":**
- Larger players (AudioEye, UsableNet, accessiBe) already operate in the space at higher price points
- Some enterprise-level automated scanning tools exist (Deque AMP, Level Access)

**Mitigation:**
- Position as the affordable SMB alternative to enterprise players ($297 vs. $2,000+)
- The long tail of SMBs is underserved by enterprise tools — this is a blue ocean within an existing market
- First-mover advantage in specific niches (law firms, dental practices, local e-commerce) is still available

**Residual Risk:** Low-Medium. Timing appears favorable for an SMB-focused entry in the 2025–2026 window.

---

## 6. Ethical Risks

### E1 — Fear-Mongering About Lawsuits

**Likelihood:** Medium | **Impact:** Medium

**Analysis:** Using lawsuit statistics aggressively in marketing can cross from "informing" to "fear-mongering." This erodes trust, attracts clients making panic purchases who then resent the spend, and contributes to a generally predatory market dynamic. It also invites backlash from accessibility advocates who view ADA-lawsuit-driven accessibility work as ethically compromised.

**Mitigation:**
- Lead with positive framing first: "15% of your potential customers have a disability. Accessibility is good for business."
- Use lawsuit statistics as supporting evidence, not as the primary hook
- Include data on ROI of accessibility: improved SEO, expanded addressable market, brand reputation
- Engage authentically with the disability community — sponsor or donate to accessibility-focused nonprofits (even small amounts signal genuine commitment)
- Avoid language like "Is your website a lawsuit waiting to happen?" in cold outreach — replace with "Here are 3 accessibility issues we found on your site that affect users with visual impairments"

**Residual Risk:** Low. This is a tone and messaging discipline issue. The underlying business (helping businesses become more accessible) is ethically positive.

---

### E2 — Selling Automated Reports at Human-Audit Prices

**Likelihood:** High | **Impact:** High

**Analysis:** This is the highest-priority ethical risk. If we charge $1,500–$2,500 for a report that took 10 minutes to generate with a $0.15 Claude API call, we are either: (a) misleading buyers about the work involved, or (b) pricing on value delivered (legal risk reduction) rather than cost of production. The ethical line is whether we are transparent about what the client is actually receiving.

**Mitigation:**
- **Price on value, not cost — but disclose what you're selling.** Charging premium prices for a 10-minute automated scan is ethical only if the client understands they are buying: (1) the expertise to interpret results, (2) the professional report format, (3) the legal-risk-reduction value, and (4) the consulting relationship — not a hand-coded manual audit.
- **Recommended pricing strategy:**
  - $197–$497 for automated scan report (transparent about automated nature)
  - $997–$1,997 for automated scan + human review layer + remediation roadmap
  - $2,500+ for ongoing monitoring + re-scans + manual spot-checks
- **Never represent automated work as manual work.** If asked "Did a human review this?", the honest answer for the base tier is "No — an automated scanner detected these issues; here's exactly what it covers and doesn't cover."
- **Transparency statement in every report:** "This report was generated using automated accessibility scanning tools (axe-core) and AI-assisted analysis (Anthropic Claude). It has not been reviewed by a human accessibility expert unless explicitly noted."

**Residual Risk:** Low with transparent pricing and honest representation. High if pricing implies manual audit work that was not performed.

---

### E3 — Lack of Transparency About AI Involvement

**Likelihood:** Medium | **Impact:** High

**Analysis:** As AI-generated professional deliverables become common, clients increasingly ask (and regulators increasingly require) disclosure of AI involvement. Failing to disclose creates trust damage when discovered and potentially violates emerging AI transparency regulations (EU AI Act, FTC guidelines on AI disclosures in commercial contexts).

**Mitigation:**
- **Standard disclosure on every report:** "Analysis and recommendations in this report were generated with AI assistance (Anthropic Claude API). All findings are based on objective axe-core scan data."
- **Proactive disclosure in sales process:** Do not hide AI involvement. Frame it as a feature: "We use AI to generate comprehensive, consistent, actionable reports in hours instead of weeks."
- Monitor FTC AI disclosure guidance and EU AI Act provisions as they develop
- Build disclosure language into the report template so it cannot be accidentally omitted

**Residual Risk:** Low. AI disclosure is increasingly expected and, when handled proactively, is a differentiator (transparency builds trust) rather than a liability.

---

## Risk Heat Map

```
Impact
  High  | L2 L3 L5 | Q1 Q2 Q4 | B4 B5    | M1 M2 | E2 E3
        | B1       |          |          |       |
--------+----------+----------+----------+-------+-------
Medium  | L1 L4    | Q3       | B2       | M3 M4 | E1
        |          |          | B3       |       |
--------+----------+----------+----------+-------+-------
  Low   |          |          |          |       |
        +----------+----------+----------+-------+-------
          Low       Medium      High    (Likelihood)
```

**Critical Priority (High Likelihood + High Impact):**
- Q1: axe-core coverage limitation
- B1: No cold outreach replies
- B5: Cash flow collapse
- E2: Automated reports at human-audit prices

**High Priority (Medium Likelihood + High Impact):**
- L2, L3, L5: Legal liability, insurance, GDPR
- Q2, Q4: Client reliance, disclaimer language
- B4: Claude API dependency
- M1: Vitamin vs. painkiller
- E3: AI transparency

---

## Top 5 Mitigation Priorities (Sequenced by Phase)

**Week 1–2 (Before First Outreach):**
1. Form LLC and draft engagement letter with liability cap and disclaimer language (mitigates L2, L3, Q4)
2. Write transparent report template with automated-scan disclosure and scope limitations (mitigates Q1, Q3, E2, E3)
3. Set up CAN-SPAM compliant email infrastructure (mitigates L4)

**Week 3–4 (First Outreach):**
4. Personalize outreach with actual scan findings — "I scanned your site and found X" (mitigates B1)
5. Framing: lead with lawsuit data + positive accessibility ROI, not pure fear (mitigates E1, M1)

**Month 2 (Post First Revenue):**
6. Purchase E&O insurance and set up multi-provider AI fallback (mitigates L3, B4)
7. Build proprietary vertical benchmarks to begin creating data moat (mitigates B2, M3)

---

*This risk register should be reviewed and updated monthly as the business develops, market conditions change, and legal landscape evolves.*
