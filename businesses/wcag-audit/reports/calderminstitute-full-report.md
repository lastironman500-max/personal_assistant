# WCAG Accessibility Scan Report
## Calder Institute of Dermatology — https://www.calderminstitute.com
**Scan Date:** March 15, 2026
**Standard:** WCAG 2.1 Level AA
**Tool:** pa11y (htmlcs engine)

---

### Disclaimer
This report documents programmatically detectable accessibility issues found via automated scanning. Automated tools detect approximately 57% of WCAG 2.1 issues. Manual testing by an accessibility specialist is recommended for complete conformance assessment. This report does not constitute legal advice or guarantee ADA/EAA compliance.

---

### Executive Summary

The Calder Institute of Dermatology homepage was scanned and returned **59 errors** — all WCAG 2.1 Level AA violations. The issue profile for this site is unusually concentrated: **58 of the 59 issues are color contrast failures** (WCAG 1.4.3), with only 1 additional structural issue (an empty link). This means the site has essentially one systemic problem repeated many times, rather than the broad array of issues often seen in healthcare websites.

The contrast failures break into two categories. The first is **7 body text/link contrast failures** where content links (e.g., "medical services," "Los Angeles County," blog post titles) are rendered in a teal color (`approximately #00a19b` based on the scanner's recommendation of `#008482`) that only achieves a 3.21:1 contrast ratio against its background — below the required 4.5:1. The second, far larger category is **51 SVG icon contrast failures** where embedded SVG `<style>` blocks containing `fill-rule` CSS rules are flagged as having 1:1 contrast (zero contrast), which represents a scanner false-positive pattern common to inline SVG stylesheets. These SVG style blocks do not contain visible text; the scanner is interpreting the CSS content of `<style>` tags as visible text.

The overall accessibility posture is **moderate-to-good for a healthcare site** once the SVG false positives are excluded. The genuinely critical issue — the teal link color throughout body content — must be addressed because it affects actual readable text. A person with moderate low vision (approximately 20/80 visual acuity or a color vision deficiency) would find these links difficult to distinguish from surrounding body text. For a dermatology practice where patients seek clinical information and need to navigate to booking pages and location pages, this is a meaningful barrier. **Top 3 priorities: (1) Darken the teal hyperlink color throughout all body content. (2) Fix the empty Google Maps link in the locations section. (3) Evaluate the SVG icon library to confirm the contrast scanner false positives and add explicit `aria-hidden` to decorative SVGs.**

---

### Compliance Scorecard

| WCAG Principle | Guideline | Status | Issues Found |
|---|---|---|---|
| **1 — Perceivable** | 1.4.3 Contrast Minimum — body text links | FAIL | 7 |
| **1 — Perceivable** | 1.4.3 Contrast Minimum — SVG style elements (likely false positives) | REVIEW | 51 |
| **2 — Operable** | (no specific failures detected beyond the empty link) | PARTIAL | 0 |
| **3 — Understandable** | (no specific failures detected) | PASS | 0 |
| **4 — Robust** | 4.1.2 Name, Role, Value (empty link) | FAIL | 1 |

---

### Issues by Severity

#### Critical Issues (7)

---

**Group A: Insufficient color contrast on content hyperlinks — 7 instances**

All 7 instances involve the same teal link color (approximately `#00a19b`) used for in-body links throughout the homepage content. The scanner found a 3.21:1 contrast ratio against the page background, below the required 4.5:1 minimum for normal-weight body text.

| # | Issue | WCAG Criterion | Element | Location | Impact |
|---|---|---|---|---|---|
| 1 | "medical services" link — contrast 3.21:1 | 1.4.3 | `<a href=".../medical-dermatologist/">medical services</a>` | Main content, 3rd content block — introductory paragraph describing the practice's services | Users with low vision or color deficiencies cannot reliably distinguish this link from surrounding body text |
| 2 | "medical" link — contrast 3.21:1 | 1.4.3 | `<a href=".../medical-dermatologist/">medical</a>` | Main content, 4th content block — second descriptive paragraph | Same as above |
| 3 | "multiple convenient locations" link — contrast 3.21:1 | 1.4.3 | `<a href=".../locations/">multiple convenient locations</a>` | Main content, 4th content block | Link to locations page is hard to see for low-vision users |
| 4 | "Los Angeles County" link — contrast 3.21:1 | 1.4.3 | `<a href=".../dermatologist-los-angeles/">Los Angeles County</a>` | Location section, 7th content block — service area descriptions | Cannot distinguish from body text |
| 5 | "Ventura County" link — contrast 3.21:1 | 1.4.3 | `<a href=".../dermatologist-ventura/">Ventura County</a>` | Location section, 7th content block | Cannot distinguish from body text |
| 6 | "Santa Barbara" link — contrast 3.21:1 | 1.4.3 | `<a href=".../dermatologist-santa-barbara/">Santa Barbara</a>` | Location section, 7th content block | Cannot distinguish from body text |
| 7 | "San Bernardino" link — contrast 3.21:1 | 1.4.3 | `<a href=".../dermatologist-san-bernardino/">San Bernardino</a>` | Location section, 7th content block | Cannot distinguish from body text |

**How to fix:** Change the link color throughout the site's CSS from the current teal (approximately `#00a19b`) to a darker shade that achieves at least 4.5:1 against the white/light gray page background. The scanner recommends `#008482` as the minimum — but for a more comfortable reading experience and to give headroom for different background colors, use `#006b69` or `#005f5d`. Apply this change to the global `a` selector in the site's stylesheet, or to the specific `.entry-content a` and body content link selectors. Verify with the [WebAIM Contrast Checker](https://webaim.org/resources/contrastchecker/).

Additionally, consider adding `text-decoration: underline` to links, as this provides a non-color cue that helps users with color vision deficiencies identify links regardless of contrast.

---

**Group B: Blog post title links with low contrast — 3 additional instances (subset of Group A total)**

| # | Issue | WCAG Criterion | Element | Location | Impact |
|---|---|---|---|---|---|
| 1 | "Rash Treatment: When Should You See a Dermatologist?" blog link — 3.21:1 | 1.4.3 | `<h3><a href=".../rash-treatment-when-should-you-see-a-dermatologist/">...` | Blog section, 10th content block — recent blog posts listing | Low-vision patients researching conditions cannot easily find/read article links |
| 2 | "Hyperhidrosis Treatment: How to Stop Excessive Sweating" blog link — 3.21:1 | 1.4.3 | `<h3><a href=".../hyperhidrosis-treatment-how-to-stop-excessive-sweating/">...` | Blog section — second recent post | Same impact |
| 3 | "How Often Should You Get a Chemical Peel for Best Results?" blog link — 3.21:1 | 1.4.3 | `<h3><a href=".../how-often-should-you-get-a-chemical-peel-for-best-results/">...` | Blog section — third recent post | Same impact |

**Note:** These 3 are included in the 7 total contrast failures above. The fix is identical — darken the site-wide link color. Blog post title links in `<h3>` headings are slightly larger text, but they are not bold, so they do not qualify for the 3:1 large-text exception (which requires both 18px+ and bold, or 24px+).

---

#### Moderate Issues (1)

---

**Group C: Empty link / link with no accessible text — 1 instance**

| # | Issue | WCAG Criterion | Element | Location | Impact |
|---|---|---|---|---|---|
| 1 | A Google Maps link contains only a `<br>` tag — no visible or accessible text | 4.1.2 H91.A.NoContent | `<a href="https://maps.app.goo.gl/R3pmxUhhfbAfnPhN8" target="_blank" rel="noreferrer noopener"><br></a>` | Locations section, 9th content block — location address block, second paragraph | Screen readers announce only the URL or "link" with no indication of destination; the link purpose is completely unknown |

**How to fix:** Replace the `<br>` inside the link with descriptive text that names the location. For example:
```html
<a href="https://maps.app.goo.gl/R3pmxUhhfbAfnPhN8" target="_blank" rel="noreferrer noopener">
  Get directions to our [Location Name] office
</a>
```
Or, if the link is meant to display as a map icon or image, provide `aria-label="Get directions to [Location Name] — opens in Google Maps"`. Remove the bare `<br>` tag.

---

#### Note on SVG Style Block Contrast Failures (51 instances — likely false positives)

The scanner flagged **51 instances** of `<style>` blocks embedded within SVG elements (`#svg_block_69b1334d5e256 > style`, etc.) as having a contrast ratio of 1:1 — which would indicate invisible text. These are SVG icon blocks (likely treatment/service icons displayed in a grid on the page) where the SVG definition includes an inline `<style type="text/css">` tag containing CSS rules like `.st0{fill-rule:evenodd;clip-rule:evenodd;...}`.

**Why this is almost certainly a false positive:** The CSS content inside these `<style>` tags is not rendered text — it is CSS code processed by the browser's style engine. The pa11y/htmlcs scanner, when evaluating contrast, may be treating the text content of `<style>` elements as visible rendered text, leading to a spurious 1:1 contrast result.

**Recommended action:**
1. Visually inspect the SVG icons on the homepage to confirm they are visible and legible.
2. If the icons are purely decorative, add `aria-hidden="true"` to each `<svg>` element to remove them from the accessibility tree entirely. This will suppress these false positives in future scans and is best practice for decorative SVGs: `<svg aria-hidden="true" focusable="false">`.
3. If the icons convey information (e.g., each represents a treatment type), add a `<title>` element inside the SVG and `aria-labelledby` on the `<svg>`: `<svg aria-labelledby="icon-title-1"><title id="icon-title-1">Skin Examination</title>...</svg>`.
4. These 51 items should be re-scanned after adding `aria-hidden` or `<title>` — the scanner should no longer flag the style blocks.

---

### Remediation Roadmap

**Week 1 — Critical (Link Contrast):**
- Identify the CSS file(s) controlling hyperlink color (likely `style.css` or a child theme stylesheet).
- Find the `a { color: ... }` rule and change the teal value to `#006b69` or darker.
- Also update `.entry-content a`, `.page-content a`, and any component-specific link selectors.
- Check all pages — not just the homepage — as the same link color is likely used site-wide.
- Verify the fix with the WebAIM Contrast Checker before publishing.

**Week 2 — Moderate (Empty Link & SVGs):**
- Fix the empty Google Maps link in the locations section. Replace `<br>` with "Get directions — [Location Name]" or add `aria-label`.
- Add `aria-hidden="true" focusable="false"` to all 51 decorative SVG icon elements in the treatment/services grid. This will eliminate the false-positive contrast warnings on their embedded `<style>` blocks.

**Month 2 — Ongoing:**
- Conduct a full manual review of the locations page and individual treatment pages for additional contrast issues (the same teal link color will be present across all pages).
- Review all blog post title links for contrast compliance.
- Engage a screen reader user or accessibility specialist for a manual audit of the appointment booking flow (not covered in this automated scan).

---

### Technical Summary
- **Pages scanned:** 1 (homepage — https://www.calderminstitute.com)
- **Total violations:** 59
- **All issue types:** error (59 errors, 0 warnings, 0 notices)
- **Unique violation types:** 2
- **Most common violation:** 1.4.3 Contrast Minimum — 58 instances (7 genuine link contrast failures + 51 SVG `<style>` false positives)
- **Second most common:** 4.1.2 Name, Role, Value — 1 instance (empty Google Maps link)
- **Platform:** WordPress (likely with a custom or premium dermatology theme)
- **WCAG Principles affected:** Perceivable, Robust
- **Estimated remediation effort:** Very low (half a developer day — the link color fix is a single CSS change; the SVG fix is adding `aria-hidden` to a batch of elements)
- **Highest risk area:** Teal body link color — affects all navigation links within content sections, location links, and blog post titles across the entire site
- **Notable finding:** This site has the fewest genuine issues of all 5 sites reviewed. After the link color fix and empty link fix, the site would pass all automated checks and present well for a manual audit.
