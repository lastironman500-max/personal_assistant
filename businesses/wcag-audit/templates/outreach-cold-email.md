# Cold Email Outreach Templates

> All emails follow the scan-first model: scan their site, find real issues, send evidence.
> Never send a generic pitch. Every email contains their specific violations.

---

## Template 1: Ecommerce / Direct Urgency

### Subject Line Variants

1. `Found {{X}} accessibility issues on {{CompanyName}}.com — quick heads up`
2. `{{CompanyName}}.com: {{X}} ADA violations I found in 60 seconds`
3. `Your checkout page has 4 accessibility failures — {{FirstName}}, worth a look?`

### Body

Hi {{FirstName}},

I ran a quick WCAG accessibility scan on {{CompanyName}}.com this morning — found {{X}} violations, including {{CRITICAL_COUNT}} critical issues on your checkout page.

The three most urgent:

- **Missing alt text** on {{ALT_COUNT}} product images (WCAG 1.1.1) — screen readers can't identify what's being sold
- **Color contrast failure** on your "Add to Cart" button (WCAG 1.4.3) — fails minimum ratio by {{CONTRAST_RATIO}}
- **No keyboard navigation** on your main navigation dropdown (WCAG 2.1.1) — keyboard-only users can't browse your site

I'm flagging this because ecommerce sites account for 77% of ADA web lawsuits filed in 2025, and {{STATE}} is one of the top filing states. The average settlement runs $25,000-$75,000 before legal fees.

I've attached a screenshot showing each issue highlighted on your site. Happy to send a full WCAG 2.1 AA scan report and remediation roadmap for ${{PRICE}} if useful — it tells your dev team exactly what to fix, in what order.

Worth a quick call?

{{SenderName}}
{{CalendarLink}}

---

## Template 2: Healthcare / Regulatory Deadline

### Subject Line Variants

1. `May 2026 HHS deadline — {{CompanyName}}'s site has compliance gaps`
2. `{{CompanyName}}: {{X}} WCAG violations that could affect your Medicare/Medicaid eligibility`
3. `Quick accessibility note for {{FirstName}} — HHS deadline approaching`

### Body

Hi {{FirstName}},

A new HHS rule requires healthcare organizations accepting Medicare or Medicaid to meet WCAG 2.1 AA standards by May 2026. I scanned {{CompanyName}}.com and found several issues that would put you out of compliance.

The top findings:

- **Missing form labels** on your patient intake form (WCAG 1.3.1) — assistive technologies cannot identify field purpose
- **Video content without captions** on your services page (WCAG 1.2.2)
- **Session timeout without warning** in your patient portal login (WCAG 2.2.1)

Non-compliance affects your ability to continue participating in federal programs and exposes the organization to OCR complaints.

I can deliver a full WCAG 2.1 AA scan report with a prioritized remediation roadmap within 48 hours for ${{PRICE}}. This gives your dev team a clear checklist of exactly what to fix before the deadline.

Would it make sense to connect this week?

{{SenderName}}
{{CalendarLink}}

---

## Template 3: SaaS / Enterprise Sales Blocker

### Subject Line Variants

1. `Your accessibility gaps may be blocking enterprise deals`
2. `{{CompanyName}}: WCAG issues that could disqualify you from government RFPs`
3. `Quick note for {{FirstName}} — found {{X}} accessibility issues on {{Product}}.com`

### Body

Hi {{FirstName}},

Enterprise procurement teams now routinely require a VPAT (Voluntary Product Accessibility Template) documenting WCAG 2.1 AA compliance before signing software contracts.

I scanned {{Product}}.com and found issues that would fail a standard procurement accessibility review:

- **Focus indicator missing** on interactive UI elements (WCAG 2.4.7)
- **Dynamic content updates** not announced to screen readers (WCAG 4.1.3)
- **Error identification** missing on form validation (WCAG 3.3.1)

Without documented compliance, {{CompanyName}} may already be losing enterprise and government deals that require WCAG certification in the RFP.

A full scan report + WCAG conformance statement typically costs $1,500-$5,000 with traditional vendors. Our AI-assisted scan delivers the same output for ${{PRICE}} in 48 hours.

Open to a 15-minute call to walk through what we found?

{{SenderName}}
{{CalendarLink}}

---

## Mini-Audit Results Format (Embed in Email)

When attaching or embedding scan evidence, format as:

```
QUICK SCAN RESULTS: {{CompanyName}}.com
Scanned: {{ScanDate}}

VIOLATIONS FOUND: {{TOTAL_COUNT}}
  Critical:  {{CRITICAL_COUNT}}  (immediate legal risk)
  Serious:   {{SERIOUS_COUNT}}   (significant barrier)
  Moderate:  {{MODERATE_COUNT}}  (degraded experience)
  Minor:     {{MINOR_COUNT}}     (best practice)

TOP 3 ISSUES:
1. [CRITICAL] {{ISSUE_1}} — {{PAGES_1}} pages affected
   WCAG {{CRITERION_1}} | {{ONE_LINE_DESCRIPTION_1}}

2. [CRITICAL] {{ISSUE_2}} — {{PAGES_2}} pages affected
   WCAG {{CRITERION_2}} | {{ONE_LINE_DESCRIPTION_2}}

3. [SERIOUS] {{ISSUE_3}} — {{PAGES_3}} pages affected
   WCAG {{CRITERION_3}} | {{ONE_LINE_DESCRIPTION_3}}

Full scan report available: ${{PRICE}}
```

Attach an annotated screenshot (Canva or Playwright screenshot with red boxes highlighting violations).

---

## Follow-Up Sequence

### Day 3 Follow-Up (Non-Responders)

**Subject:** Re: accessibility issues on {{CompanyName}}.com

Hi {{FirstName}},

Just bumping this up — wanted to make sure you saw the accessibility scan I ran on your site. Given that ADA web lawsuits are up 37% this year and {{STATE}} is seeing a surge in filings, I didn't want you to miss this.

The {{CRITICAL_COUNT}} critical issues I found are the exact type cited in most ADA demand letters. Happy to hop on a 15-minute call — no obligation.

{{SenderName}}
{{CalendarLink}}

---

### Day 7 Follow-Up (Final Touch)

**Subject:** Last thing — {{CompanyName}}.com accessibility check

Hi {{FirstName}},

I know you're busy — this is my last note. I found {{TOTAL_COUNT}} accessibility violations on your website that could lead to an ADA demand letter or lawsuit.

Quick context: 188 serial plaintiffs drove all 2,014 federal ADA web lawsuits filed in H1 2025. They specifically target sites with the type of issues I found on yours.

If you'd like a full report with a prioritized fix list, I'm offering it at ${{PRICE}} this week. After that I'm fully booked for the month.

{{SenderName}}
{{CalendarLink}}

---

## Email Sending Rules

1. **Never use bulk email tools for the first wave.** Send individually from Gmail/Outlook to avoid spam filters.
2. **Maximum 50 emails/day** from a single sending domain during warmup (first 2 weeks).
3. **Use a dedicated sending domain** — never your primary domain.
4. **Configure SPF, DKIM, DMARC** before sending a single email.
5. **Personalize the first 2 lines** with their specific scan findings — never use a generic opener.
6. **Respond to replies within 30 minutes** during business hours.
7. **Track opens and replies** via Streak CRM (free tier).
8. **Stop the sequence immediately** if someone replies with "not interested" or "unsubscribe."
