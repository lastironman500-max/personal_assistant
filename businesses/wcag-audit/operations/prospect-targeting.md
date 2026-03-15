# Prospect Targeting Strategy

---

## How to Find Prospects with Accessibility Issues

The core advantage of this business is the scan-first model: scan their site, find real issues, use the evidence in outreach. This converts cold outreach into a "gift first" interaction — the prospect receives proof of a problem they didn't know about before being asked for money.

### The Scan-First Pipeline

```
1. Build target list (industry + geography + company size)
2. Run automated axe-core scan on homepage + 2-3 key pages
3. Extract top 3-5 critical violations with annotated screenshots
4. Send personalized outreach with their specific findings as proof
5. Offer: full scan report + remediation roadmap for $197-$497
```

Scan throughput: 200-500 URLs per hour on a standard VPS.

---

## Industry Targets (Ranked by Conversion Probability)

### Tier 1: Highest Urgency, Fastest Close

| Rank | Industry | % of ADA Lawsuits | Why They Convert |
|------|----------|------------------|-----------------|
| 1 | **Fashion/Apparel Ecommerce** | 35.2% (1,121 suits in 2024) | Image-heavy sites with missing alt text; checkout accessibility failures |
| 2 | **Restaurant/Food/Beverage** | 23.8% (758 suits) | Online menus, ordering, reservation widgets are accessibility nightmares |
| 3 | **Consumer Goods/Retail Ecommerce** | ~11% | Product pages, filters, checkout flows |
| 4 | **Healthcare (Medicare/Medicaid)** | ~4% | HHS May 2026 deadline; double liability (HIPAA + ADA) |

### Tier 2: Strong Urgency, Slightly Longer Sales Cycle

| Rank | Industry | Why They Convert |
|------|----------|-----------------|
| 5 | **SaaS (selling to gov/enterprise)** | VPAT required for procurement; no VPAT = disqualified from RFPs |
| 6 | **K-12 and Higher Education** | Section 508, OCR complaints, aging web infrastructure |
| 7 | **Financial Services** | CFPB oversight, state-level rules, high lawsuit volume in NY/CA/FL |
| 8 | **Hospitality/Travel** | Booking flows, image galleries, reservation widgets |

### Tier 3: Good Market, Longer Education Cycle

| Rank | Industry | Why They Convert |
|------|----------|-----------------|
| 9 | **Law Firms** | Irony sells — they understand liability immediately |
| 10 | **Government Contractors** | ADA Title II mandate for all vendors |
| 11 | **Nonprofits** | Grant requirements increasingly require WCAG compliance |

---

## Geographic Targets (Ranked by ADA Lawsuit Volume)

### Primary Target States

| Rank | State | H1 2025 Lawsuits | Key Cities | Notes |
|------|-------|-----------------|------------|-------|
| 1 | **New York** | 637 | NYC, Brooklyn, Queens | Courts accept suits against ANY website visited by NY residents |
| 2 | **Florida** | 487 | Miami, Tampa, Orlando | Nearly doubled from 2024; hot emerging market |
| 3 | **California** | ~400 | LA, SF Bay Area, San Diego | 3,252 total ADA Title III filings in 2024 |
| 4 | **Illinois** | 237 | Chicago | Exploded 745% from just 28 cases in 2024 |

### Secondary Target States

| State | Notes |
|-------|-------|
| **Texas** | Large SMB base; growing lawsuit awareness |
| **New Jersey** | Spillover from NY filing patterns |
| **Pennsylvania** | Philadelphia metro area |
| **Massachusetts** | Boston tech/healthcare corridor |

### Key Geographic Insight

New York courts accept ADA web lawsuits against websites *visited* by NY residents — not just NY-based companies. This means any ecommerce or consumer-facing business in the US is exposed to NY jurisdiction. Lead with this fact in outreach to companies in other states.

---

## Google Search Operators for Finding Targets

### Ecommerce (Shopify/WooCommerce Stores)

```
# Fashion boutiques without accessibility statements
site:shopify.com -inurl:"accessibility" "clothing" OR "fashion" OR "apparel"

# WooCommerce stores in target cities
"woocommerce" OR "shopify" clothing [city]
inurl:"/shop" OR inurl:"/store" -inurl:"accessibility-statement"

# Ecommerce stores on Yelp/Google Maps
site:yelp.com "order online" [industry] [city]
```

### Healthcare

```
# Healthcare practices with online booking
"healthcare" OR "medical" site:.org OR site:.com inurl:"patient-portal" -inurl:"accessibility"
dentist "[city]" "book appointment" online
chiropractor "[city]" "schedule online"

# Telehealth platforms
"telehealth" OR "telemedicine" inurl:"login" -inurl:"accessibility"
```

### Restaurants

```
# Restaurants with online ordering
site:yelp.com "order online" restaurant [city]
"menu" "order online" restaurant [city] -uber -doordash -grubhub

# Restaurant websites (direct ordering)
inurl:"order" OR inurl:"menu" restaurant [city] site:.com
```

### SaaS Without VPAT

```
# SaaS companies without accessibility documentation
inurl:"pricing" inurl:"enterprise" -inurl:"vpat" -inurl:"accessibility"

# SaaS with government customers
"government" OR "federal" OR "state agency" inurl:"customers" -inurl:"vpat"
```

### Education

```
# Education portals without accessibility statements
site:.edu -inurl:"accessibility" -inurl:"ada-compliance" inurl:"login" OR inurl:"portal"
```

### Companies Recently Sued (Find Peers to Target)

```
# Find companies named in ADA web lawsuits, then target their competitors
"web accessibility" "demand letter" OR "lawsuit" site:courtlistener.com
site:pacer.gov "accessibility" "website" [industry]
```

---

## Industry Directories and Prospect Lists

| Source | What to Find | Access | Best For |
|--------|-------------|--------|----------|
| Shopify Partner Directory | Ecommerce merchants by niche | Free | Fashion, retail, D2C |
| Inc. 5000 / Deloitte Fast 500 | Fast-growing companies (high web traffic) | Free | High-value targets |
| SAM.gov / USASpending.gov | Government contractors with web presence | Free | Gov contractors |
| CMS Provider Enrollment | Healthcare orgs accepting Medicare/Medicaid | Free (FOIA) | Healthcare |
| Crunchbase / Apollo.io | SaaS companies by funding stage | Paid | SaaS vertical |
| PACER / CourtListener | Companies recently named in ADA suits | Free | Peer targeting |
| State chamber of commerce | Regional SMBs by city | Free | Local businesses |
| NRF member directory | Retailers (77% of lawsuits target retail) | Free | Retail/ecommerce |
| Clutch.co / Agency Spotter | Web agencies (partnership channel) | Free | Agency partners |
| Yelp Business Pages | Local businesses by category + city | Free | Restaurants, services |

---

## Bulk Scanning Strategy

### Phase 1: Quick Scan (WAVE Extension)

For rapid prospect qualification:
1. Open target website in Chrome
2. Click WAVE extension
3. Screenshot the error overlay (shows red error count)
4. Record error count in tracking sheet
5. **Threshold:** 10+ errors = high priority prospect

**Speed:** ~30 seconds per site (manual)

### Phase 2: Detailed Scan (axe-core CLI)

For bulk automated scanning:
1. Build `urls.txt` file with prospect URLs (one per line)
2. Run batch scan via Pa11y CLI or custom axe-core script
3. Output: JSON violation reports for all URLs
4. Filter by error severity and count

**Speed:** 200-500 URLs per hour (automated)

### Phase 3: Annotated Evidence (Playwright Screenshots)

For high-priority prospects:
1. Playwright captures screenshot of page with violations highlighted
2. Annotate in Canva with red boxes around problem areas
3. Attach to outreach email

**Speed:** ~2 minutes per annotated screenshot

---

## Finding Decision-Maker Emails

### Email Discovery Waterfall (Stop When Found)

1. **Hunter.io Domain Search** — Enter domain, get emails + confidence scores. Use only 80%+ confidence.
   - Free: 25 searches/month
   - Starter: $49/month for 500 searches

2. **Apollo.io** — Search company name, find owner/founder/marketing director with email
   - Free: 10 exports/month
   - Basic: $49/month for 1,000 contacts

3. **LinkedIn** — Company page > People tab > filter by title (Owner, Founder, CEO, Marketing) > note name > use Hunter Email Finder (name + domain)

4. **Website Contact Page** — Many small businesses list owner email directly

5. **Google Business Profile** — Sometimes lists email in business details

6. **Facebook Business Page** — About tab often has email

7. **WHOIS Lookup** — whois.domaintools.com (less common due to privacy protection)

8. **Pattern Guessing + Verification** — Common patterns:
   - firstname@domain.com
   - first.last@domain.com
   - info@domain.com
   - Verify with Hunter's email verifier before sending

### Target Job Titles (In Priority Order)

| Title | Why They Buy | Decision Speed |
|-------|-------------|---------------|
| Owner / Founder / CEO | Final authority, especially at SMBs | Fast |
| Director of Legal / General Counsel | Threat of lawsuit lands on their desk | Fast |
| Compliance Officer | Responsible for regulatory filings | Fast |
| CTO / VP Engineering | Owns technical compliance | Medium |
| VP Marketing / Digital | Owns website, flagged in reviews | Medium |
| Head of Product (SaaS) | VPAT blocks enterprise deals | Medium |

---

## LinkedIn Sales Navigator Filters

### Account Filters

- **Industry:** Retail & Ecommerce, Healthcare, Financial Services, Software/SaaS, Government Administration
- **Company headcount:** 50-1,000 (big enough for budget, small enough to lack in-house accessibility)
- **Geography:** NY, CA, FL, IL (highest lawsuit states) OR EU (EAA pressure)
- **Technology:** Shopify, WooCommerce, Magento (ecommerce platforms = direct lawsuit target)

### Lead Filters

- **Job title (Boolean):** `("Legal" OR "Compliance" OR "Accessibility") AND ("Director" OR "VP" OR "Manager" OR "Head of")`
- **Seniority level:** Director, VP, CXO, Owner
- **Function:** Legal, Information Technology, Engineering, Marketing
- **Years in role:** 0-2 years (new leaders audit their department's risk exposure)

### High-Intent Spotlight Filters

- **Changed jobs in past 90 days** — new leaders audit risk exposure
- **Posted on LinkedIn in past 30 days** — active professional, more likely to respond
- **Viewed your profile** — warm signal, message immediately

---

## Trigger Events That Create Urgency

Prospects are most likely to buy immediately after these events:

| Trigger | How to Find It | Outreach Angle |
|---------|---------------|----------------|
| Received ADA demand letter | They tell you / public court filings | "We can help you respond with documented remediation" |
| EAA enforcement (June 2025+) | Company sells to EU customers | "EAA fines up to EUR 100K — here's what we found on your site" |
| HHS healthcare deadline (May 2026) | CMS provider databases | "Your site has gaps that affect Medicare/Medicaid eligibility" |
| RFP requires WCAG statement | SAM.gov, procurement portals | "You need a WCAG conformance statement — here's your current status" |
| New website launch | Press releases, domain registration alerts | "Your new site launched without accessibility review — found X issues" |
| Overlay removal | News monitoring for "accessiBe" removals | "Good call removing the overlay — here's what still needs fixing" |
| Competitor got sued | Public court filings | "Your competitor just got sued for the same type of issues on your site" |
