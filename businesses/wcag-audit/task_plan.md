# Task Plan: WCAG Accessibility Scan Business — Validate & Sell

## Goal
Validate the WCAG scan business by manually running scans, generating sample reports, and cold-outreaching real business owners with proof of their issues. First paying customer before building any product. Run everything locally from CLI.

## Core Principle
**Sell first, build later.** No website, no landing page, no automated pipeline. Just:
1. Scan a real website with axe-core
2. Generate a teaser PDF (high-level stats + 3-5 example issues)
3. Email the owner: "We found 47 accessibility issues on your site. Here's a preview."
4. If they pay, run the full scan manually and deliver a complete report
5. Only build product after we have paying customers

## Current Phase
Phase 1

## Phases

### Phase 1: Set Up Local Scan Workflow
- [ ] Install axe-core CLI or browser extension
- [ ] Install Pa11y CLI for quick scans
- [ ] Test scan on a known website
- [ ] Create teaser report template (1-2 pages: score + 3-5 example issues)
- [ ] Create full report template (used only after payment)
- **Status:** pending
- **Deliverable:** Working local scan + teaser PDF template

### Phase 2: Find 50 Target Websites
- [ ] Pick industry (ecommerce or healthcare — highest lawsuit risk)
- [ ] Pick geography (NY, FL, CA — most ADA lawsuits)
- [ ] Find 50 SMB websites in target segment
- [ ] Scan all 50 for accessibility issues (batch)
- [ ] Rank by issue count (worst = best prospects)
- [ ] Find owner/decision-maker email for each
- **Status:** pending
- **Deliverable:** Prospect spreadsheet with scan results + emails

### Phase 3: Create Teaser Reports for Top 20
- [ ] For top 20 worst-scoring sites, generate teaser PDFs
- [ ] Each teaser: overall score, critical issue count, 3-5 specific examples with screenshots
- [ ] Include: "This is a preview. Full report with remediation steps available for $299."
- **Status:** pending
- **Deliverable:** 20 teaser PDFs ready to send

### Phase 4: Cold Outreach Blitz
- [ ] Send personalized emails to all 20 with teaser PDF attached
- [ ] LinkedIn DMs to 10 highest-value prospects
- [ ] Follow up Day 3, Day 7
- [ ] Track responses in spreadsheet
- **Status:** pending
- **Deliverable:** 20 emails sent, response tracking started

### Phase 5: Deliver Full Reports (on payment)
- [ ] When someone pays, run full scan manually
- [ ] Generate complete report with Claude (all issues + remediation)
- [ ] Format as PDF, deliver via email
- [ ] Ask for testimonial + referral
- **Status:** pending
- **Deliverable:** Paid report delivered, revenue earned

### Phase 6: Validate or Pivot
- [ ] Did anyone pay? (GO → build product)
- [ ] Did anyone reply but not pay? (adjust pricing/offer)
- [ ] Zero replies? (pivot industry, channel, or business model)
- **Status:** pending
- **Deliverable:** GO/NO-GO on building product

## What We're NOT Doing Yet
- No website or landing page
- No automated pipeline
- No Fiverr/Upwork listings
- No Stripe payment links
- No hosting or infrastructure
- No code beyond CLI scripts

## Teaser Report Format (1-2 pages)
```
[Logo placeholder]

ACCESSIBILITY SCAN PREVIEW
[Company Name] — [URL]
Date: [date]

OVERALL SCORE: [X/100]
Pages Scanned: [N]
Total Issues Found: [N]
  Critical: [N] | Serious: [N] | Moderate: [N] | Minor: [N]

TOP ISSUES FOUND (preview):

1. [Issue type] — [page URL]
   Impact: [who is affected and how]
   [Screenshot]

2. [Issue type] — [page URL]
   ...

3. [Issue type] — [page URL]
   ...

---
This is a preview of [N] issues found.
Full report with remediation steps: $299
Reply to this email or book a call: [calendly link]
```

## Budget: $0 for validation
- axe-core: free
- Pa11y: free
- Claude API for report writing: ~$1-2 total for 20 teasers
- Email: personal Gmail
- Total: essentially $0

## Success Criteria
- 1 paying customer = validated, proceed to build
- 3+ replies expressing interest = promising, refine offer
- 0 replies after 50 outreach = pivot

## Key Decisions
| Decision | Rationale |
|----------|-----------|
| Manual-first, no product | Validate demand before investing build time |
| Teaser PDF, not full report | Give enough to prove value, withhold enough to get paid |
| Personal email, not tool | Authenticity > scale at this stage |
| Target worst-scoring sites | Highest pain = highest conversion |

## Errors Encountered
| Error | Attempt | Resolution |
|-------|---------|------------|
|       |         |            |
