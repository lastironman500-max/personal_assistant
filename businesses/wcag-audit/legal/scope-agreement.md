# Client Scope Agreement and Authorization

> This agreement is signed (or acknowledged via email) before scanning begins.
> For Fiverr/Upwork orders, acceptance of gig terms serves as implicit authorization.
> For direct clients, send this as a PDF or include in the order confirmation email.

---

## WEBSITE ACCESSIBILITY SCAN AUTHORIZATION AND SCOPE AGREEMENT

**Agreement Date:** {{DATE}}
**Report ID:** {{REPORT_ID}}

---

### Parties

**Service Provider:** {{BRAND_NAME}} ("Provider")
**Client:** {{CLIENT_NAME}}, {{CLIENT_COMPANY}} ("Client")

---

### 1. Authorization to Scan

Client hereby authorizes Provider to perform an automated accessibility scan of the following website(s):

| # | Website URL | Page Limit |
|---|------------|-----------|
| 1 | {{WEBSITE_URL_1}} | {{PAGE_LIMIT}} |
| 2 | {{WEBSITE_URL_2}} (if applicable) | {{PAGE_LIMIT}} |

Client represents and warrants that:

- [ ] Client is the owner of the website(s) listed above, OR
- [ ] Client has explicit written authorization from the website owner to request this scan

Client understands that the scan will access only publicly available web pages — the same content any visitor can view in a standard web browser. The scan will NOT:

- Access password-protected or authenticated areas
- Submit forms or modify any website content
- Collect personal data of website visitors
- Bypass any security measures
- Perform penetration testing or vulnerability scanning

---

### 2. Scope of Service

**Service Tier:** {{SERVICE_TIER}} (Starter / Standard / Compliance)

**Included in this engagement:**

| Deliverable | Starter ($197) | Standard ($299) | Compliance ($497/mo) |
|-------------|:-----------:|:------------:|:----------------:|
| Automated WCAG 2.1/2.2 AA scan | Yes | Yes | Yes |
| AI-generated violation analysis | Yes | Yes | Yes |
| Executive summary | -- | Yes | Yes |
| Full issue-by-issue breakdown | Top issues | All issues | All issues |
| Code-level fix instructions | -- | Yes | Yes |
| Prioritized remediation roadmap | -- | Yes | Yes |
| Compliance scorecard | -- | Yes | Yes |
| Monthly re-scans | -- | -- | Yes |
| Video walkthrough | -- | -- | Yes |
| Conformance status statement | -- | -- | Yes |
| Professional PDF report | Yes | Yes | Yes |

**Explicitly NOT included:**

- Manual accessibility testing with assistive technologies
- Legal advice or legal compliance certification
- Code implementation or remediation services
- Guarantee of ADA, Section 508, EAA, or any regulatory compliance
- Ongoing monitoring (unless Compliance tier)

---

### 3. Scan Methodology

The scan uses the following tools and methods:

1. **Crawling:** Playwright (headless Chromium browser) discovers pages via sitemap and link-following
2. **Scanning:** axe-core (industry-standard accessibility engine, maintained by Deque Systems, used by Google, Microsoft, and the BBC) tests each page against WCAG 2.1/2.2 Level AA criteria
3. **Analysis:** Claude AI (by Anthropic) deduplicates findings, writes plain-English descriptions, generates remediation code examples, and prioritizes issues
4. **Report Generation:** Professional PDF with executive summary, issue breakdown, priority matrix, and remediation roadmap

**Detection scope:** Automated tools detect approximately 57% of WCAG issues by volume. The remaining 43% require manual testing. This limitation is documented in the report.

---

### 4. Delivery

- **Starter:** Delivered within 48 hours of scan authorization
- **Standard:** Delivered within 3-5 business days
- **Compliance:** Initial report within 5 business days; monthly re-scans on the same date each month

Delivery method: Professional PDF report sent to Client's email address.

---

### 5. Payment Terms

| Tier | Amount | Billing |
|------|--------|---------|
| Starter | $197 | One-time, due before scan |
| Standard | $299 | One-time, due before scan |
| Compliance | $497 | Monthly, first payment due before initial scan |

Payment methods accepted: Stripe (credit/debit card), PayPal, bank transfer.

---

### 6. Confidentiality

Provider agrees to:

- Keep all scan findings confidential
- Not share, publish, or disclose the report or its contents to any third party
- Not use Client's website URL, company name, or scan findings in marketing materials without explicit written permission
- Store scan data securely and delete upon Client request

---

### 7. Limitations and Disclaimers

Client acknowledges and agrees that:

1. This is an **automated accessibility scan**, not a full manual audit or legal compliance certification
2. Automated tools detect approximately **57% of WCAG issues** — the remaining 43% require manual testing
3. The report does NOT constitute legal advice or a guarantee of regulatory compliance
4. The report does NOT guarantee protection from lawsuits, demand letters, or regulatory enforcement
5. Provider's **total liability is limited to the amount paid** for the specific scan
6. Provider recommends Client engage a certified accessibility specialist for complete conformance assessment
7. AI (Claude by Anthropic) is used in the analysis and report generation process

---

### 8. Acceptance

By proceeding with payment / replying "I agree" to this email / placing the order on [platform], Client agrees to the terms of this Scope Agreement.

**Client:**
Name: {{CLIENT_NAME}}
Company: {{CLIENT_COMPANY}}
Email: {{CLIENT_EMAIL}}
Date: {{DATE}}

**Provider:**
Name: {{PROVIDER_NAME}}
Company: {{BRAND_NAME}}
Email: {{PROVIDER_EMAIL}}
Date: {{DATE}}

---

### Quick-Start Version (Email Confirmation)

> For speed, send this condensed version via email. Client's reply constitutes acceptance.

Subject: Scan Authorization — {{CLIENT_COMPANY}}

Hi {{CLIENT_NAME}},

Before I begin your WCAG accessibility scan, please confirm the following by replying "I agree":

1. **Website to scan:** {{WEBSITE_URL}}
2. **Service tier:** {{SERVICE_TIER}} (${{PRICE}})
3. **You are authorized** to request a scan of this website
4. **You understand** this is an automated scan (not a manual audit or legal certification) that detects ~57% of WCAG issues
5. **You understand** the report is for informational purposes and does not guarantee regulatory compliance

Full terms: [link to Terms of Service]

Once confirmed, I'll begin the scan and deliver your report within {{DELIVERY_WINDOW}}.

Best,
{{PROVIDER_NAME}}
