# Task Plan: WCAG Accessibility Scan Business — Build & Launch

## Goal
Build and launch a fully operational WCAG accessibility scan business that can accept a URL, produce a professional PDF report, and deliver it to a paying customer — all with zero human intervention. Target: $1,000 revenue in 5 days.

## Current Phase
Phase 1

## Phases

### Phase 1: MVP Scanner (Code)
- [ ] Build Node.js CLI tool: URL → crawl → axe-core scan → JSON output
- [ ] Multi-page support (sitemap + link following)
- [ ] Screenshot capture of violations
- [ ] Output structured JSON for Claude
- **Status:** pending
- **Owner:** Scanner subagent
- **Deliverable:** `src/scanner/` — working CLI tool

### Phase 2: AI Report Writer
- [ ] Claude prompt that converts axe-core JSON → narrative report
- [ ] Executive summary generation
- [ ] Issue-by-issue plain-English explanations
- [ ] Prioritized remediation roadmap
- [ ] Compliance scorecard (WCAG 2.2 A/AA/AAA)
- **Status:** pending
- **Owner:** Writer subagent
- **Deliverable:** `src/writer/` — prompt + formatting logic

### Phase 3: PDF Generator
- [ ] Convert markdown report → branded PDF
- [ ] Cover page with client branding
- [ ] Table of contents
- [ ] Professional styling (headers, tables, severity colors)
- [ ] Disclaimer page
- **Status:** pending
- **Owner:** PDF subagent
- **Deliverable:** `src/pdf/` — PDF generation pipeline

### Phase 4: Delivery Pipeline
- [ ] Email delivery via Resend (free tier)
- [ ] Stripe payment link integration
- [ ] End-to-end CLI: `scan <url> --email <client@email.com>`
- **Status:** pending
- **Owner:** Pipeline subagent
- **Deliverable:** `src/delivery/` — email + payment wiring

### Phase 5: Prospect Scanner (Bulk)
- [ ] Batch scan multiple URLs for accessibility issues
- [ ] Output: prospect list with issue counts + severity
- [ ] Used for cold outreach — "we found 47 issues on your site"
- **Status:** pending
- **Owner:** Prospector subagent
- **Deliverable:** `src/prospector/` — bulk scanning tool

### Phase 6: Landing Page + Fiverr
- [ ] Carrd or HTML landing page with pricing
- [ ] Fiverr gig listing
- [ ] Upwork profile
- **Status:** pending
- **Owner:** Marketing subagent
- **Deliverable:** `site/` — landing page files

### Phase 7: Outreach Blitz (Day 2-5)
- [ ] Scan 50 prospects per day
- [ ] Send personalized cold emails with mini-audit
- [ ] LinkedIn outreach
- [ ] Follow up on Day 3, Day 7
- **Status:** pending
- **Owner:** Outreach subagent

## Architecture Overview
```
scan-cli <url>
  ├── 1. Crawl (Playwright + sitemap)
  ├── 2. Scan (axe-core on each page)
  ├── 3. Analyze (Claude API → narrative)
  ├── 4. Generate PDF (Puppeteer)
  └── 5. Deliver (Resend email)
```

## Tech Stack
| Component | Tool | Cost |
|-----------|------|------|
| Crawler | Playwright | Free |
| Scanner | @axe-core/playwright | Free |
| AI Writer | Claude API (Haiku for bulk, Sonnet for premium) | ~$0.06-0.50/report |
| PDF | Puppeteer | Free |
| Email | Resend | Free (100K/mo) |
| Hosting | Railway Hobby | $5/mo |
| Domain | Namecheap | $12/yr |
| Payments | Stripe | 2.9% + $0.30 |

## Budget Allocation ($100)
| Item | Cost | Priority |
|------|------|----------|
| Domain | $12 | Day 1 |
| Railway hosting | $5 | Day 1 |
| Claude API credits | $20 | Day 1 |
| Hunter.io (email finding) | $0 (free tier) | Day 1 |
| Fiverr promoted gig | $20 | Day 2 |
| Reserve | $43 | Buffer |

## Key Decisions
| Decision | Rationale |
|----------|-----------|
| Node.js + TypeScript | Best ecosystem for Playwright + axe-core |
| CLI-first, no web UI for MVP | Ship faster, add web later |
| Haiku for standard reports | $0.06 vs $0.50, quality sufficient |
| Puppeteer PDF over WeasyPrint | Reuses Chromium from Playwright |
| Resend over SendGrid | Permanent free tier (100K/mo) |

## Errors Encountered
| Error | Attempt | Resolution |
|-------|---------|------------|
|       |         |            |

## Notes
- Commit after each phase
- Use subagents for parallel build
- Test with real websites before outreach
- Never call it an "audit" — always "scan report"
