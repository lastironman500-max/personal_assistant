# VC Teardown: WCAG Accessibility Audit Business

**Date:** 2026-03-15
**Role:** Skeptical VC Partner — Pre-Mortem Analysis
**Verdict:** Read to the end.

---

## 1. Why hasn't someone already done this? Where are the incumbents?

**The question behind the question:** If there's a real $200-500 price point gap between free tools and $1,250+ agencies, why hasn't Deque, Siteimprove, Level Access, or any of the dozens of accessibility SaaS companies filled it? They have the technology, the brand, and the distribution. You're claiming they left money on the table.

**Why this matters:** This is the "efficient market" objection. If the opportunity exists, the absence of incumbents either means (a) you're wrong about the opportunity, or (b) there's a structural reason they don't want to play here. Both are dangerous.

**What a good answer looks like:**
- Incumbents sell enterprise SaaS ($5K-$30K/year contracts). A $300 one-time report cannibalizes their upsell pipeline. Siteimprove's 2025 addition of AI-powered explanations proves they see the narration gap but won't price down to serve SMBs.
- accessiBe ($49/month overlay) targets this segment but sells a widget, not an audit. They've been repeatedly sued and discredited — 22.6% of 2025 ADA lawsuits targeted sites with overlays installed.
- The real answer: agencies won't automate because it destroys their labor model. SaaS companies won't sell one-time reports because it destroys their recurring revenue model. This is a structural gap, not an oversight.

**Kill shot or survivable?** Survivable — but only if you move fast. Siteimprove already added AI explanations. The window is 12-18 months before incumbents launch a "lite" tier.

---

## 2. What's the actual conversion rate for cold outreach selling compliance services?

**The question behind the question:** You're projecting $1,000 in 5 days from cold outreach. That requires 2-5 closed deals at $200-500. B2B cold email reply rates average 5.8%, and conversion rates hover at 0.2%-2.4%. You need to send hundreds of emails to close 2-5 deals. Can you even do that in 5 days?

**Why this matters:** The math might not work. At a 1% conversion rate, you need 200-500 prospects in your pipeline. At 2.4% (B2B average), you still need 80-200. Cold email sequences typically run 3-5 touches over 7-14 days. Your 5-day window is too short for a full sequence.

**What a good answer looks like:**
- This isn't generic cold email. You're leading with a free preview — the prospect's actual violations with screenshots. That's not a pitch; it's a wake-up call. Personalized, evidence-based cold email campaigns hit 10-20% reply rates (top 10% of campaigns hit 8-12% consistently).
- The conversion shortcut: you're not selling a concept, you're selling a fix to a specific problem you've already identified. "Your checkout page has 23 WCAG violations. Here are the top 3. Full report with remediation steps is $299." That's consultative selling, not cold email.
- Realistic target: 100-150 prospects scanned, 15-25 replies (10-15% reply rate), 3-5 closed deals. Tight but achievable.

**Kill shot or survivable?** Survivable — the free preview is the key differentiator. Without it, this is dead-on-arrival generic outreach. With it, you're in the top decile of cold campaigns.

---

## 3. axe-core catches 57% of issues. You're selling an incomplete audit. Isn't that fraud?

**The question behind the question:** Deque's own documentation says axe-core catches 57% of WCAG issues on average (they claim 80% with their paid DevTools). The UK Government Digital Service puts combined automated tools at ~30-35%. You're charging $200-500 for something that misses 43-70% of actual accessibility issues. If a client relies on your report and gets sued, you gave them a false sense of security.

**Why this matters:** This is the existential risk. If you position this as a "full WCAG audit," you're making an implicit representation that could be legally and ethically indefensible. Accessibility professionals will call you out. Disability advocates will be hostile. Plaintiff's attorneys will use your report against your client.

**What a good answer looks like:**
- Never call it a "full audit" or "WCAG certification." Position it as an "automated accessibility scan with remediation guidance" — explicitly scoped to programmatically-detectable issues.
- Disclose the limitation prominently: "This report covers issues detectable through automated scanning (approximately 57% of WCAG 2.2 criteria). Manual testing by a qualified auditor is recommended for complete conformance."
- The value is still real: most businesses have zero awareness of their accessibility issues. Going from 0% knowledge to 57% knowledge with prioritized remediation steps is genuinely valuable. No agency provides a full audit for $300 either — their $1,250 entry-level products are also limited-scope.
- Build an upsell path to manual review (partner with accessibility consultants for full audits at $2,500-5,000).

**Kill shot or survivable?** Survivable with disciplined positioning. Kill shot if you oversell the scope. One client who gets sued after relying on your "audit" destroys the business through reputation damage alone.

---

## 4. $200-500 for an automated report — why wouldn't the customer just run axe-core themselves?

**The question behind the question:** axe-core is free. The axe DevTools browser extension is free. WAVE is free. Lighthouse is built into Chrome. Any developer can run these in 5 minutes. Why would anyone pay you $200-500 for what is essentially a wrapper around freely available tools?

**Why this matters:** If your customers are technical, this is a fatal value proposition problem. Developers don't need you. The question is whether your actual customer is technical.

**What a good answer looks like:**
- The customer isn't the developer. The customer is the business owner, marketing director, or compliance officer who doesn't know what axe-core is and doesn't have a developer on staff.
- axe-core outputs raw JSON. Lighthouse outputs a score. Neither produces: (a) plain-English explanation of what each issue means, (b) prioritized remediation steps a non-developer can act on, (c) legal risk context explaining why each issue matters under ADA/EAA, (d) a professional PDF they can hand to their web agency or insurance company.
- The analogy: TurboTax doesn't do anything you can't do with IRS forms. But 40 million people pay for it because the narration, guidance, and packaging have value.
- Data point: SMBs spend $500-2,000 on website audits from agencies who literally run the same tools, add a Word doc, and charge 10x. The market has proven willingness to pay for interpretation.

**Kill shot or survivable?** Survivable. This is the core thesis of the business — the narration gap. If you can't articulate this clearly in the sales process, you fail. But the gap is real and proven by existing agency pricing.

---

## 5. How do you handle the "who are you?" trust problem?

**The question behind the question:** Cold email from an unknown sender saying "your website has legal compliance issues" reads as a scam. It reads like the SEO spam that every business owner gets 10 times a day. How do you establish credibility when you have no brand, no testimonials, no IAAP certification, and no track record?

**Why this matters:** Trust is the #1 barrier in compliance services. Companies buy audits from people and firms they trust, not from unknown entities emailing them. Without trust, your conversion rate is effectively zero regardless of how good the report is.

**What a good answer looks like:**
- Lead with evidence, not credentials. The preview email shows their actual violations with screenshots. This is impossible to fake and impossible to ignore. It demonstrates competence immediately.
- Create a professional landing page with sample reports, methodology documentation, and clear tool disclosure (axe-core + AI analysis).
- Get 3-5 testimonials fast by offering the first reports free or at deep discount to local businesses, then use those in all outreach.
- Partner with a certified accessibility professional (CPACC, WAS, CPWA) who reviews a sample of reports. Even a part-time advisor adds credibility.
- Register an LLC. Get a professional email domain. These are table stakes.

**Kill shot or survivable?** Survivable with execution. The evidence-based outreach helps. But the first 10 sales will be painful. Expect 2-3 weeks to build enough social proof to accelerate.

---

## 6. ADA lawsuits target big companies. Are SMBs actually scared enough to pay?

**The question behind the question:** The famous cases are Target, Domino's, Beyonce's website. Are SMBs really being sued? Or are you projecting enterprise fear onto a market segment that doesn't feel the pain?

**Why this matters:** If SMBs don't perceive legal risk, you're selling a vitamin, not a painkiller. Vitamins don't sell through cold outreach.

**What a good answer looks like:**
- The data says you're wrong about this being a big-company problem. ADA web accessibility lawsuits rose 37% in 2025, with the **majority** of eCommerce defendants having less than $25 million in revenue. Restaurants and apparel alone made up 60% of filings. These are Main Street businesses.
- Geographic concentration creates targetable fear: New York (637 lawsuits), Florida (487), California (380), and Illinois exploded 746% year-over-year to 237 cases. If you target businesses in these states, the fear is real and specific.
- The EAA adds international pressure: penalties up to EUR 100,000 or 4% of annual revenue for any business selling to EU consumers. This hits US-based eCommerce businesses selling internationally.
- 69% of 2025 ADA lawsuits targeted online retailers. If you target eCommerce SMBs in litigious states, you're selling to businesses whose peers are actively being sued.

**Kill shot or survivable?** Survivable — in fact, this is your strongest selling point. The data overwhelmingly supports SMB vulnerability. Target eCommerce businesses in NY, FL, CA, and IL for maximum conversion.

---

## 7. What's the moat? If this works, what stops Siteimprove or Deque from offering the same thing at $99?

**The question behind the question:** You have no proprietary technology. axe-core is open source. Claude is available to everyone. Report templates can be copied. If you prove the market exists, a well-funded competitor can replicate your entire offering in a week and undercut you with brand advantage.

**Why this matters:** This is the "will you survive success?" question. Proving the market works might be the thing that kills you, because it invites competition you can't beat on brand, price, or technology.

**What a good answer looks like:**
- Honest answer: there is no technical moat. Zero.
- The real moat is operational speed and niche focus. Siteimprove won't sell a $99 report because it destroys their $30,000/year enterprise ASP. Deque won't because they sell $40/month developer tools. The structural incentive gap persists.
- Build a moat through: (a) industry-specific report templates (eCommerce, healthcare, restaurant, etc.), (b) ongoing monitoring subscriptions (scan monthly, flag regressions), (c) remediation partnerships with dev agencies (become the audit front-end for a referral network), (d) a database of scan results that enables benchmarking ("your site is worse than 73% of restaurants in Florida").
- The real defensibility is customer relationships and distribution, not technology. The first mover who builds a list of 1,000+ SMB clients and converts them to monthly monitoring has a defensible recurring revenue base.

**Kill shot or survivable?** Survivable if you treat the one-time report as a wedge product and build toward recurring revenue. Kill shot if you stay a one-time report business — someone will undercut you within 6 months.

---

## 8. Unsolicited website scanning — isn't that a legal risk?

**The question behind the question:** Your go-to-market requires scanning websites before you have permission. Under the Computer Fraud and Abuse Act (CFAA), accessing a computer system "without authorization" is a federal crime. Some companies have aggressive legal teams that will send cease-and-desist letters. You might also violate Terms of Service.

**Why this matters:** If a single prospect threatens legal action for unauthorized scanning, it could create a PR disaster or actual litigation that kills the business before it starts.

**What a good answer looks like:**
- axe-core and browser-based accessibility scanning access only publicly available web pages — the same content any visitor sees in a browser. This is legally equivalent to visiting a website. No authentication is bypassed, no systems are penetrated, no data is extracted. Courts have consistently held that accessing public web pages is not a CFAA violation.
- This is materially different from port scanning, vulnerability scanning, or penetration testing. You're running a browser automation tool that checks if alt tags exist and if contrast ratios meet thresholds. It's the same thing Google's crawler does millions of times per day.
- Mitigate residual risk: (a) only scan publicly accessible pages, (b) respect robots.txt, (c) don't scan at high frequency (no DDoS risk), (d) include opt-out in all outreach, (e) consult an attorney to confirm.
- Precedent: companies like BuiltWith, Wappalyzer, and SimilarWeb scan every website on the internet and sell the data commercially. This is an established, legal practice.

**Kill shot or survivable?** Survivable. The legal risk is near-zero for public page accessibility scanning. But get a lawyer's opinion in writing before launch. Budget $200-500 for a legal consultation.

---

## 9. $1,000 in 5 days from cold outreach — show me comparable benchmarks.

**The question behind the question:** You're claiming you can go from zero to $1,000 in revenue in 5 business days with no existing brand, no pipeline, no testimonials, and a $100 budget. That means you need to: build the product, identify prospects, scan their sites, write outreach, send emails, get replies, do sales calls, close deals, deliver reports, and collect payment — all in 120 hours. This sounds like fantasy.

**Why this matters:** If the 5-day target is unrealistic, the entire pitch is built on a lie. Investors fund realistic plans, not miracles.

**What a good answer looks like:**
- Be honest: 5 days is aggressive. Here's the realistic breakdown:
  - Day 1: Finalize report template, set up email infrastructure (domain, warmup tools)
  - Day 2-3: Scan 100-150 target websites, generate preview findings
  - Day 3-4: Send personalized outreach with preview findings
  - Day 5+: Handle replies, close deals, deliver reports
- The 5-day target assumes everything goes right. More realistic: 7-10 days to first revenue, 14-21 days to hit $1,000.
- Comparable benchmarks: freelancers on Upwork selling accessibility audits close their first sale within 1-2 weeks. B2B cold email campaigns using personalized lead magnets (which this is) show 5-15 day sales cycles for sub-$500 products.
- The $100 budget constraint is the real bottleneck: email tooling ($30-50), domain ($12), Claude API costs ($20-40). Leaves almost nothing for contingencies.

**Kill shot or survivable?** Survivable — but reframe the timeline. 5 days is a stretch goal. 14 days is realistic for first $1,000. If the investor needs proof-of-concept, run a 2-week sprint, not a 5-day sprint.

---

## 10. What happens when a client gets sued AFTER using your report?

**The question behind the question:** A client buys your $300 report, "fixes" the 57% of issues you identified, feels compliant, and gets sued for the 43% you missed. Their lawyer calls you. The plaintiff's lawyer subpoenas your report and uses it to prove the defendant knew about accessibility issues. You've created a discoverable document that helps the plaintiff's case while simultaneously giving the defendant a false sense of security.

**Why this matters:** This is the nightmare scenario. You could face: (a) professional negligence claims, (b) indemnification demands from the client's defense team, (c) breach of implied warranty claims, (d) devastating PR when the accessibility community points out you sold an incomplete audit.

**What a good answer looks like:**
- Bulletproof disclaimers: every report must state explicitly that it covers only automated detectable issues, does not constitute legal advice, does not guarantee ADA/EAA compliance, and that manual expert review is recommended.
- Professional liability insurance (E&O insurance): budget $500-1,500/year. This is non-negotiable.
- Structure the deliverable as a "scan report" not an "audit" or "certification." Language matters legally.
- Include a "limitations" section in every report that a lawyer has reviewed.
- Case law context: website designers and vendors have faced indemnification claims. The precedent for downstream liability exists.

**Kill shot or survivable?** Survivable with proper legal structure. Kill shot if you skip the disclaimers, skip the insurance, or position the report as comprehensive compliance certification.

---

## 11. Is this a real business or a side hustle that caps at $5K/month?

**The question behind the question:** You're selling one-time reports at $200-500. To make $10K/month, you need 20-50 new clients every month. That's a sales treadmill with no recurring revenue. Every month starts at zero. That's not a business; it's freelancing with extra steps.

**Why this matters:** VCs don't invest in treadmills. If there's no path to $50K+ MRR with compounding growth, this is a lifestyle business at best.

**What a good answer looks like:**
- The report is the wedge, not the product. The product roadmap:
  1. **One-time reports** ($200-500) — prove the market, build the client base
  2. **Monthly monitoring** ($49-99/month) — scan monthly, alert on regressions, new pages. Recurring revenue.
  3. **Remediation partnerships** — refer clients to dev agencies for fixes, take 15-20% referral fee
  4. **Annual re-certification** — regulations change (WCAG 2.2 now, 3.0 coming), clients need updated reports annually
  5. **API/white-label** — sell the scanning + reporting engine to agencies who want to offer it under their brand
- Unit economics: 100 monitoring clients at $79/month = $7,900 MRR. 500 clients = $39,500 MRR. The monitoring upsell is where the business becomes venture-scale.
- The eCommerce vertical alone has millions of SMBs. With EAA enforcement creating urgency for any business selling to EU consumers, the addressable market is enormous.

**Kill shot or survivable?** Kill shot if you stay in one-time reports forever. Survivable if you launch monitoring within 60 days and achieve 30%+ conversion from report buyers to monitoring subscribers.

---

## 12. EU EAA compliance — do you actually understand what's required?

**The question behind the question:** You mentioned EAA as a selling point. The European Accessibility Act became enforceable on June 28, 2025. It covers products and services including eCommerce, telecoms, banking, and transport. Compliance requires conformance with EN 301 549, not just WCAG. Penalties can reach EUR 100,000 or 4% of annual revenue. Do you actually understand the differences between ADA requirements, WCAG conformance, and EAA/EN 301 549 requirements? Or are you hand-waving "EU regulations" as a scare tactic?

**Why this matters:** If you sell EAA compliance reports without understanding EN 301 549, you're selling something you can't deliver. This is the fastest path to the negligence problem in Question 10.

**What a good answer looks like:**
- Be specific: EN 301 549 maps closely to WCAG 2.1 AA for web content (Section 9), but also covers non-web documents (Section 10), software (Section 11), and documentation/support services (Section 12). axe-core covers the web content portion only.
- Scope the EAA offering honestly: "Our report covers the web content accessibility requirements of EN 301 549 Section 9, which aligns with WCAG 2.1 Level AA. Full EAA compliance may require additional assessment of non-web documents, software interfaces, and support services."
- Build separate report templates for ADA (US) and EAA (EU) contexts with jurisdiction-specific language, penalties, and legal references.
- Partner with an EU-based accessibility consultant for EAA-specific guidance.

**Kill shot or survivable?** Survivable with honest scoping. Kill shot if you claim "full EAA compliance" based on a WCAG web scan.

---

## 13. Single-vendor AI dependency — Claude goes down or reprices, what happens?

**The question behind the question:** Your entire narration layer depends on Anthropic's Claude API. If Claude experiences downtime, changes pricing, implements rate limits, or modifies its terms of service to prohibit this use case, your business stops instantly. You have a single point of failure with zero control over it.

**Why this matters:** API dependency risk is a known startup killer. OpenAI has changed pricing 4 times. Anthropic could double prices tomorrow. A 48-hour outage during a client delivery deadline destroys your reputation.

**What a good answer looks like:**
- Build the system to be LLM-agnostic from day one. Use a prompt abstraction layer that can route to Claude, GPT-4, Gemini, or Llama. Test report quality across multiple models.
- Current Claude API costs for a full report: approximately $0.15-0.50 per report (input: scan data ~10K tokens, output: report ~5K tokens). Even at 5x price increase, this is $0.75-2.50 per report on a $300 product. The margin can absorb significant price increases.
- Cache common remediation patterns locally. Most accessibility issues have standard fixes — you don't need to call the API for "add alt text to images" every time.
- Keep a 30-day cash reserve for API costs. Monitor API changelog and terms of service weekly.

**Kill shot or survivable?** Survivable. The API cost is <1% of revenue per report. Even a 10x price increase is manageable. Build model-agnostic architecture as insurance.

---

## 14. Cold email deliverability — how do you avoid spam filters?

**The question behind the question:** You're planning to send 50-100+ emails about "your website has legal compliance issues." That subject line pattern is identical to phishing attacks and SEO spam. Gmail, Outlook, and corporate email filters will flag this aggressively. If your domain gets blacklisted in week 1, your entire outreach channel is dead.

**Why this matters:** Email deliverability is a technical skill that most founders underestimate. A new domain sending compliance-related cold emails has a high probability of being flagged as spam. If your first 50 emails bounce or land in spam, you've burned your domain and your budget.

**What a good answer looks like:**
- Domain warmup: buy a separate outreach domain (not your main brand domain) 2+ weeks before launch. Send 5-10 genuine emails per day, gradually increasing volume. Use a warmup tool like Lemwarm or Warmbox.
- Email infrastructure: set up SPF, DKIM, and DMARC records. Use a dedicated sending tool (Instantly, Lemlist, or similar) with built-in deliverability monitoring.
- Subject lines that avoid spam triggers: "Quick question about [companyname].com" is better than "Your website has ADA compliance violations." Lead with curiosity, not fear.
- Volume limits: max 30-50 emails per day per sending account. Use 2-3 sending accounts to scale.
- Personalization: include the prospect's actual website URL, specific violation count, and a screenshot. This signals human effort and reduces spam classification probability.
- Compliance: include physical address, unsubscribe link, and honor CAN-SPAM requirements.

**Kill shot or survivable?** Survivable with proper email infrastructure investment. Kill shot if you skip warmup and blast 200 emails from a new domain on day 1 — your domain gets blacklisted and you're done.

---

## 15. The accessibility community may see this as predatory.

**The question behind the question:** The disability rights and accessibility community has strong opinions about companies that exploit ADA fear for profit. accessiBe faced massive backlash from the National Federation of the Blind and other advocacy groups for selling an overlay widget that provided false compliance. Your model — cold emailing businesses about their violations and selling automated reports — could be perceived as the same predatory pattern: exploiting fear of lawsuits with an incomplete solution.

**Why this matters:** If the accessibility community turns against you, you lose: (a) potential referral partners (accessibility consultants), (b) credibility with clients who do their research, (c) ability to recruit accessibility expertise, and (d) you become a cautionary tale on accessibility Twitter/Mastodon.

**What a good answer looks like:**
- accessiBe's mistake was claiming their overlay "solved" accessibility. That was dishonest. Your model is fundamentally different: you're identifying real issues and providing real remediation guidance, not slapping a widget on and claiming compliance.
- Engage the community proactively: (a) be transparent about automation limitations, (b) always recommend manual testing in every report, (c) donate 5% of revenue to accessibility advocacy organizations, (d) hire or partner with people with disabilities in the testing process.
- Position as "accessibility democratization," not "compliance fear-mongering." The framing matters. "We make accessibility auditing affordable for businesses that can't afford $5,000 agency audits" is very different from "You'll get sued if you don't buy our report."
- Never use scare tactics in outreach. Lead with "we found these issues and here's how to fix them" not "you're going to get sued."

**Kill shot or survivable?** Survivable with intentional community engagement. Kill shot if you adopt accessiBe's playbook of overclaiming and fear-mongering. The accessibility community has long memory and loud voices.

---

## 16. ADDITIONAL: Customer acquisition cost vs. lifetime value math doesn't work for one-time reports.

**The question behind the question:** Cold email outreach costs time and money. If you're spending 30-60 minutes per prospect (scanning their site, personalizing the email, following up), and your close rate is 5%, you're spending 10-20 hours of labor to close one $300 deal. That's $15-30/hour before COGS. You're building a minimum-wage business.

**Why this matters:** Unit economics determine whether a business can scale. If CAC > 50% of revenue on a one-time product, the business is unsustainable.

**What a good answer looks like:**
- Automate prospecting: batch-scan websites using a headless browser + axe-core script. Scan 100 websites in 1-2 hours, not 30-60 minutes each. Generate preview emails automatically from scan results.
- Target CAC: <$50 per closed deal (including tools, time, and API costs). At $300 average deal size, that's 83% gross margin before report generation costs.
- LTV expansion: if 30% of report buyers convert to $79/month monitoring, LTV jumps from $300 to $300 + ($79 x 12 x 0.3) = $584 in year 1. With monitoring retention, LTV could reach $1,000+ over 2 years.
- The real answer: automate everything possible so human time is spent only on closing, not prospecting or scanning.

**Kill shot or survivable?** Survivable if you automate the prospecting pipeline. Kill shot if every prospect requires 30+ minutes of manual work.

---

## 17. ADDITIONAL: What's your plan when WCAG 3.0 ships and changes everything?

**The question behind the question:** WCAG 3.0 is in development and introduces a completely new conformance model (Bronze/Silver/Gold instead of A/AA/AAA) and new testing methodologies. When it ships, every report template, every remediation guide, and every claim about "WCAG compliance" becomes outdated. Are you building for a standard that's about to change?

**Why this matters:** Regulatory changes create both opportunity and risk. If you're not prepared, you lose credibility. If you are prepared, you have a re-engagement opportunity with every past client.

**What a good answer looks like:**
- WCAG 3.0 is years from becoming a legal requirement. WCAG 2.1 AA is the current EAA standard. WCAG 2.2 is the latest W3C recommendation. The business has a long runway on current standards.
- When WCAG 3.0 arrives, it's actually a tailwind: every existing client needs updated reports. This is the annual re-certification revenue opportunity.
- Build the reporting system to be standards-configurable (WCAG version as a parameter, not hardcoded).
- Monitor W3C working drafts and update axe-core when Deque adds 3.0 rules.

**Kill shot or survivable?** Survivable — actually an opportunity for re-engagement revenue.

---

## 18. ADDITIONAL: You're competing with free browser extensions that non-technical people already use.

**The question behind the question:** WAVE, Google Lighthouse, and axe DevTools all have free browser extensions that generate visual reports with explanations. Microsoft's Accessibility Insights is free and user-friendly. These aren't just raw JSON anymore — they have real UIs. Your "narration gap" thesis might already be closing.

**Why this matters:** If free tools are "good enough" for SMBs, your pricing power disappears.

**What a good answer looks like:**
- Browser extensions scan one page at a time. A business website has 20-200+ pages. Your report scans the full site.
- Extensions don't produce a deliverable document. A compliance officer needs a PDF to hand to their boss, their lawyer, or their web agency. "Go install this Chrome extension" isn't a deliverable.
- Extensions don't provide legal context (ADA/EAA implications), prioritized remediation plans, or cost estimates for fixes.
- But take the threat seriously: as these tools improve their UX, the bottom of your market (the most tech-savvy SMBs) will self-serve. Price accordingly and focus on the least technical segments.

**Kill shot or survivable?** Survivable. The deliverable format and full-site scanning are genuine differentiators. But the narration gap is narrowing — this is a 2-3 year window, not a permanent advantage.

---

## 19. ADDITIONAL: Your $100 starting budget is a red flag, not a feature.

**The question behind the question:** You're pitching this as bootstrappable with $100. That means no legal review of your disclaimers, no E&O insurance, no proper email infrastructure, no professional branding, and no buffer for anything going wrong. You're building a compliance-adjacent business with zero compliance of your own.

**Why this matters:** Cutting corners on legal and operational foundations to save money is how businesses get destroyed by their first problem.

**What a good answer looks like:**
- Acknowledge the risk honestly. The $100 is for the proof-of-concept phase only. Here's what's needed within 30 days of first revenue:
  - LLC formation: $50-200 (state dependent)
  - E&O insurance: $500-1,500/year
  - Legal review of disclaimers/ToS: $500-1,000
  - Professional email infrastructure: $30-50/month
  - Domain + hosting: $50-100/year
- Total real startup cost: $1,200-2,800. The first $1,000 in revenue goes straight back into the business.
- The $100 buys: domain ($12), email tool trial ($0-30), Claude API credits ($20-40), and the remaining sweat equity.

**Kill shot or survivable?** Survivable if you reinvest aggressively from first revenue. Kill shot if you stay at the $100 level and skip legal/insurance protections.

---

## 20. ADDITIONAL: Who's actually making the buying decision, and can they even spend $300 without approval?

**The question behind the question:** In SMBs, the person who receives your cold email (often the owner or marketing manager) may not have budget authority for unplanned $300 compliance expenses. In larger SMBs, this requires procurement, legal review, or management approval. Your sales cycle might be longer than you think.

**Why this matters:** B2B sales cycles for compliance services average 2-6 weeks. If the decision-maker needs to consult their lawyer or boss before buying, your 5-day timeline is fantasy.

**What a good answer looks like:**
- Target business owners directly (1-20 employee companies) where the email recipient IS the decision-maker. No procurement process. Credit card purchase.
- For larger SMBs (20-200 employees), target the head of marketing or compliance with the preview report, but expect a 1-3 week sales cycle.
- Reduce friction: offer the report immediately upon payment (automated delivery), accept credit card, offer a money-back guarantee.
- Price psychology: $299 feels like a business expense, not a major purchase. Most small business owners can charge this to a business credit card without approval.

**Kill shot or survivable?** Survivable if you target the right company size. The sweet spot is 5-50 employee eCommerce businesses where the owner makes purchasing decisions.

---

## Overall Verdict

| Category | Count |
|----------|-------|
| Kill shots (if mishandled) | 5 |
| Survivable with discipline | 12 |
| Actually advantages | 3 |

**The five ways this business dies:**
1. Overselling the report as "full compliance" and facing negligence claims
2. Staying a one-time report business with no recurring revenue
3. Skipping legal/insurance protections to save money
4. Adopting fear-mongering tactics that alienate the accessibility community
5. Failing to automate prospecting, resulting in unsustainable unit economics

**The three things that are actually strong:**
1. SMB lawsuit data is overwhelming — this is a real, growing, quantifiable pain point (37% YoY growth in lawsuits, majority targeting sub-$25M revenue companies)
2. The structural pricing gap is real — agencies can't go lower, SaaS won't go lower, free tools don't produce deliverables
3. The evidence-based outreach model (scan first, then pitch) is genuinely differentiated from generic cold email

**Bottom line:** This is not a venture-scale business in its current form. It's a high-margin, bootstrappable services business that could reach $10K-30K/month within 6 months if executed well. The path to venture scale requires (a) converting to recurring monitoring revenue, (b) building a white-label/API offering for agencies, and (c) expanding beyond accessibility into full compliance suites. The 5-day/$1K target is aggressive but not impossible. The real question isn't whether this can work — it's whether the founder has the discipline to position honestly, invest in legal protections, and build toward recurring revenue instead of chasing one-time reports.

---

## Sources

- [2025 ADA Lawsuit Statistics - EcomBack](https://www.ecomback.com/ada-website-lawsuits-recap-report/2025-mid-year-ada-website-lawsuit-report)
- [Accessibility Lawsuits Rose 37% in 2025 - KEYT](https://keyt.com/news/money-and-business/stacker-money/2026/01/14/accessibility-lawsuits-rose-by-37-in-2025-why-small-businesses-can-no-longer-ignore-their-websites/)
- [2026 ADA Compliance Predictions - Accessible.org](https://accessible.org/2026-ada-website-compliance-lawsuits-ai/)
- [axe-core Issue Detection Rate - GitHub Issue #4415](https://github.com/dequelabs/axe-core/issues/4415)
- [B2B Cold Email Statistics 2025 - Martal Group](https://martal.ca/b2b-cold-email-statistics-lb/)
- [Cold Email Reply-Rate Benchmarks 2025 - The Digital Bloom](https://thedigitalbloom.com/learn/cold-outbound-reply-rate-benchmarks/)
- [Cold Email Response Rate 2025 - Belkins](https://belkins.io/blog/cold-email-response-rates)
- [Digital Accessibility Software Market - Mordor Intelligence](https://www.mordorintelligence.com/industry-reports/digital-accessibility-software-market)
- [EAA Enforcement - European Commission](https://accessible-eu-centre.ec.europa.eu/content-corner/news/eaa-comes-effect-june-2025-are-you-ready-2025-01-31_en)
- [European Accessibility Act Guide - Level Access](https://www.levelaccess.com/compliance-overview/european-accessibility-act-eaa/)
- [Siteimprove Alternatives - TestParty](https://testparty.ai/blog/siteimprove-alternatives)
- [Top Accessibility Vendors 2025 - TestParty](https://testparty.ai/blog/accessibility-audit-remediation-vendors)
- [Computer Fraud and Abuse Act - Rapid7](https://www.rapid7.com/blog/post/2013/10/30/legal-considerations-for-widespread-scanning/)
- [ADA Litigation Insights 2025 - DarrowEverett LLP](https://darroweverett.com/ada-website-accessibility-litigation-insights-legal-analysis/)
- [Top Accessibility Providers Pricing - ADA Compliance Pros](https://www.adacompliancepros.com/blog/top-5-digital-accessibility-providers-in-2025-features-pricing-and-reviews)
