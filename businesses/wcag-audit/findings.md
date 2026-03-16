# Findings: WCAG Scan Business Build

## Technical Findings
- axe-core catches ~57% of WCAG issues — sufficient for automated scan, not a full audit
- @axe-core/playwright is the standard integration — npm package, well-documented
- Puppeteer PDF reuses Chromium already loaded by Playwright — no extra dependency
- Resend free tier: 100K emails/month, 3K/day — more than enough
- Railway Hobby: $5/mo, handles Node.js + Chromium fine
- Claude Haiku 4.5 Batch API: $0.06 per report — negligible cost

## Market Findings
- ADA lawsuits: 4,500-5,000 projected for 2025, +37% YoY
- EAA (EU): enforcement started June 2025
- 77% of lawsuits target ecommerce
- Top states: NY (637), FL (487), CA (~400), IL (237)
- Agencies charge $1,250-15,000 for same deliverable

## Competitive Findings
- Only 1 direct competitor: The Audit Base ($199 scan, $999 remediation)
- Free tools (axe, WAVE, Lighthouse) give raw data, not reports
- Enterprise tools (Siteimprove $15K+/yr) won't serve SMBs

## Build Decisions
- Phase 1-4 can build in parallel (scanner, writer, PDF, delivery are independent)
- Phase 5 (prospector) depends on scanner being done
- Phase 6-7 (marketing + outreach) can start in parallel with build
