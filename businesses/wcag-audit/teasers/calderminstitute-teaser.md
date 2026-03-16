# Website Accessibility Scan Preview
## Calder Institute of Dermatology — calderminstitute.com
**Scan Date:** March 15, 2026

---

### Overall Results
- **Pages Scanned:** 1 (homepage)
- **Total Issues Found:** 59
- **Critical/Error Issues:** 59

---

### Top 3 Issues Found (Preview)

**Issue 1: Low-Contrast Body Links Throughout the Homepage**
- What's wrong: Multiple in-content text links — including links to "medical services," service location pages for Los Angeles County, Ventura County, Santa Barbara, and San Bernardino — display at a contrast ratio of 3.21:1 against the page background. The WCAG AA minimum is 4.5:1.
- Where: Homepage body content (`#main-content > div > div:nth-child(3)`, `div:nth-child(4)`), location section link group
- Why it matters: Low-vision users, patients with age-related macular degeneration, or those accessing the site in bright light cannot reliably read or distinguish these links from surrounding body text — potentially preventing them from finding the services or locations they need.
- Legal risk: Healthcare providers serving patients across multiple counties have a particularly strong obligation to ensure equal access; contrast failures on service and location links are a documented basis for Section 504 and ADA Title III complaints.

**Issue 2: 50+ SVG Icon Elements With Invisible Text (1:1 Contrast)**
- What's wrong: Over fifty inline `<style>` blocks embedded within SVG icon elements register a contrast ratio of exactly 1:1 — meaning the text content (CSS within the SVG) is rendered against an identical background color, making it invisible. While these are style blocks rather than visible copy, the scan flags them as contrast failures that assistive technology may attempt to interpret.
- Where: Across the treatment and service icon grid (`#svg_block_*` selectors throughout the page)
- Why it matters: Screen readers and accessibility tooling parsing these elements encounter hidden or malformed content, which can disrupt page structure interpretation and cause unpredictable reading order for keyboard users.
- Legal risk: While individually minor, the volume of flagged elements (50+) signals a systemic templating issue that would be difficult to defend as an isolated oversight in a compliance review.

**Issue 3: Empty Map Link With No Accessible Label**
- What's wrong: A link pointing to a Google Maps location (`maps.app.goo.gl`) contains only a `<br>` tag as its content — no text, no aria-label, nothing that a screen reader can announce to the user.
- Where: Location section of the homepage (`#main-content > div > div:nth-child(9)`)
- Why it matters: A patient trying to navigate to a clinic location cannot determine where this link leads or activate it meaningfully with a screen reader, blocking access to the one piece of information most directly tied to in-person care.
- Legal risk: For a multi-location dermatology practice, an inaccessible "get directions" link is a concrete denial of service to disabled patients and a clear ADA violation.

---

### What This Means for Calder Institute
Dermatology practices face a dual compliance obligation: ADA Title III covers public-facing websites, and Section 504 of the Rehabilitation Act may apply if the practice receives any federal reimbursement (Medicare/Medicaid). California has some of the most active ADA litigation environments in the country, and medical providers are increasingly named in both federal and state-level accessibility complaints. With 59 errors on the homepage alone, a proactive remediation investment is far less costly than a demand letter.

---

*This is a preview showing 3 of 59 issues found. A full report with remediation steps for every issue is available.*

*Full Accessibility Scan Report — $299*
*Includes: All 59 issues documented, plain-English fix instructions, priority remediation roadmap, compliance scorecard*

*Reply to this email to get started.*
