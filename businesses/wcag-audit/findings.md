# Findings: WCAG Scan Business — Validation Phase

## Validation Strategy
- Sell first, build later
- Manual scans from local CLI → teaser PDF → cold email → payment → full report
- $0 budget needed for validation (all tools free)
- Success = 1 paying customer

## Tools for Manual Scanning
| Tool | Use | Cost |
|------|-----|------|
| axe DevTools (Chrome extension) | Quick single-page scan | Free |
| Pa11y CLI (`npm i -g pa11y`) | CLI scan, JSON output | Free |
| WAVE (wave.webaim.org) | Visual overlay of issues | Free |
| Lighthouse (Chrome DevTools) | Accessibility score + details | Free |
| Claude API | Generate report narrative from scan data | ~$0.06/report |

## Target Selection Criteria
- Industry: Ecommerce (77% of ADA lawsuits) or Healthcare (HHS deadline May 2026)
- Geography: NY, FL, CA, IL (highest ADA lawsuit volume)
- Company size: 10-500 employees (big enough to pay, small enough to lack compliance team)
- Signal: no accessibility widget on site = likely non-compliant

## Outreach Approach
- Scan their site first → find real issues → lead with proof
- Teaser PDF shows 3-5 issues, withholds the rest
- CTA: "Full report with fixes for $299"
- Follow up Day 3 and Day 7 if no reply

## What We Learned from Research
- Agencies charge $1,250+ for this exact deliverable
- Our cost: ~$0.06 per report (Claude API)
- Only 1 direct competitor at this price point (The Audit Base)
- ADA lawsuits +37% YoY — urgency is real
- 94.8% of websites have WCAG failures (WebAIM Million 2025)
