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

The contrast failures break into two categories. The first is **8 body text/link contrast failures** where content links (e.g., "medical services," "Los Angeles County," blog post titles) are rendered in a teal color (`approximately #00a19b` based on the scanner's recommendation of `#008482`) that only achieves a 3.21:1 contrast ratio against its background — below the required 4.5:1. The second, far larger category is **50 SVG icon contrast failures** where embedded SVG `<style>` blocks containing `fill-rule` CSS rules are flagged as having 1:1 contrast (zero contrast), which represents a scanner false-positive pattern common to inline SVG stylesheets. These SVG style blocks do not contain visible text; the scanner is interpreting the CSS content of `<style>` tags as visible text.

The overall accessibility posture is **moderate-to-good for a healthcare site** once the SVG false positives are excluded. The genuinely critical issue — the teal link color throughout body content — must be addressed because it affects actual readable text. A person with moderate low vision (approximately 20/80 visual acuity or a color vision deficiency) would find these links difficult to distinguish from surrounding body text. For a dermatology practice where patients seek clinical information and need to navigate to booking pages and location pages, this is a meaningful barrier. **Top 3 priorities: (1) Darken the teal hyperlink color throughout all body content. (2) Fix the empty Google Maps link in the locations section. (3) Evaluate the SVG icon library to confirm the contrast scanner false positives and add explicit `aria-hidden` to decorative SVGs.**

---

### Compliance Scorecard

| WCAG Principle | Guideline | Status | Issues Found |
|---|---|---|---|
| **1 — Perceivable** | 1.4.3 Contrast Minimum — body text links | FAIL | 8 |
| **1 — Perceivable** | 1.4.3 Contrast Minimum — SVG style elements (likely false positives) | REVIEW | 50 |
| **2 — Operable** | (no specific failures detected beyond the empty link) | PARTIAL | 0 |
| **3 — Understandable** | (no specific failures detected) | PASS | 0 |
| **4 — Robust** | 4.1.2 Name, Role, Value (empty link) | FAIL | 1 |

---

### All Issues Found (59 total)

| # | Severity | WCAG Rule | Issue Description | Element (simplified) | How to Fix |
|---|----------|-----------|-------------------|----------------------|------------|
| 1 | Error | 1.4.3 | Link text "medical services" has insufficient contrast ratio of 3.21:1 (minimum required: 4.5:1) | Main content — introductory paragraph link to medical services page | Change link color from teal (~#00a19b) to #006b69 or darker to achieve 4.5:1 contrast |
| 2 | Error | 1.4.3 | Link text "medical" has insufficient contrast ratio of 3.21:1 (minimum required: 4.5:1) | Main content — second descriptive paragraph link to medical page | Change link color from teal (~#00a19b) to #006b69 or darker to achieve 4.5:1 contrast |
| 3 | Error | 1.4.3 | Link text "multiple convenient locations" has insufficient contrast ratio of 3.21:1 (minimum required: 4.5:1) | Main content — second descriptive paragraph link to locations page | Change link color from teal (~#00a19b) to #006b69 or darker to achieve 4.5:1 contrast |
| 4 | Error | 1.4.3 | Link text "Los Angeles County" has insufficient contrast ratio of 3.21:1 (minimum required: 4.5:1) | Location section — service area link for Los Angeles County | Change link color from teal (~#00a19b) to #006b69 or darker to achieve 4.5:1 contrast |
| 5 | Error | 1.4.3 | Link text "Ventura County" has insufficient contrast ratio of 3.21:1 (minimum required: 4.5:1) | Location section — service area link for Ventura County | Change link color from teal (~#00a19b) to #006b69 or darker to achieve 4.5:1 contrast |
| 6 | Error | 1.4.3 | Link text "Santa Barbara" has insufficient contrast ratio of 3.21:1 (minimum required: 4.5:1) | Location section — service area link for Santa Barbara | Change link color from teal (~#00a19b) to #006b69 or darker to achieve 4.5:1 contrast |
| 7 | Error | 1.4.3 | Link text "San Bernardino" has insufficient contrast ratio of 3.21:1 (minimum required: 4.5:1) | Location section — service area link for San Bernardino | Change link color from teal (~#00a19b) to #006b69 or darker to achieve 4.5:1 contrast |
| 8 | Error | 1.4.3 | SVG style block flagged with contrast ratio of 1:1 (likely false positive — SVG style block; CSS fill rules misread as visible text) | SVG icon block #svg_block_69b1334d5e256 — embedded `<style>` tag | Add `aria-hidden="true" focusable="false"` to the parent `<svg>` element |
| 9 | Error | 1.4.3 | SVG style block flagged with contrast ratio of 1:1 (likely false positive — SVG style block; CSS fill rules misread as visible text) | SVG icon block #svg_block_69b1334d5e6e9 — embedded `<style>` tag | Add `aria-hidden="true" focusable="false"` to the parent `<svg>` element |
| 10 | Error | 1.4.3 | SVG style block flagged with contrast ratio of 1:1 (likely false positive — SVG style block; CSS fill rules misread as visible text) | SVG icon block #svg_block_69b1334d5ea03 — embedded `<style>` tag | Add `aria-hidden="true" focusable="false"` to the parent `<svg>` element |
| 11 | Error | 1.4.3 | SVG style block flagged with contrast ratio of 1:1 (likely false positive — SVG style block; CSS fill rules misread as visible text) | SVG icon block #svg_block_69b1334d5ecf7 — embedded `<style>` tag | Add `aria-hidden="true" focusable="false"` to the parent `<svg>` element |
| 12 | Error | 1.4.3 | SVG style block flagged with contrast ratio of 1:1 (likely false positive — SVG style block; CSS fill rules misread as visible text) | SVG icon block #svg_block_69b1334d5efaa — embedded `<style>` tag | Add `aria-hidden="true" focusable="false"` to the parent `<svg>` element |
| 13 | Error | 1.4.3 | SVG style block flagged with contrast ratio of 1:1 (likely false positive — SVG style block; CSS fill rules misread as visible text) | SVG icon block #svg_block_69b1334d5f243 — embedded `<style>` tag | Add `aria-hidden="true" focusable="false"` to the parent `<svg>` element |
| 14 | Error | 1.4.3 | SVG style block flagged with contrast ratio of 1:1 (likely false positive — SVG style block; CSS fill rules misread as visible text) | SVG icon block #svg_block_69b1334d5f4a8 — embedded `<style>` tag | Add `aria-hidden="true" focusable="false"` to the parent `<svg>` element |
| 15 | Error | 1.4.3 | SVG style block flagged with contrast ratio of 1:1 (likely false positive — SVG style block; CSS fill rules misread as visible text) | SVG icon block #svg_block_69b1334d5f6a9 — embedded `<style>` tag | Add `aria-hidden="true" focusable="false"` to the parent `<svg>` element |
| 16 | Error | 1.4.3 | SVG style block flagged with contrast ratio of 1:1 (likely false positive — SVG style block; CSS fill rules misread as visible text) | SVG icon block #svg_block_69b1334d5f8a5 — embedded `<style>` tag | Add `aria-hidden="true" focusable="false"` to the parent `<svg>` element |
| 17 | Error | 1.4.3 | SVG style block flagged with contrast ratio of 1:1 (likely false positive — SVG style block; CSS fill rules misread as visible text) | SVG icon block #svg_block_69b1334d5fa8d — embedded `<style>` tag | Add `aria-hidden="true" focusable="false"` to the parent `<svg>` element |
| 18 | Error | 1.4.3 | SVG style block flagged with contrast ratio of 1:1 (likely false positive — SVG style block; CSS fill rules misread as visible text) | SVG icon block #svg_block_69b1334d5fcbd — embedded `<style>` tag | Add `aria-hidden="true" focusable="false"` to the parent `<svg>` element |
| 19 | Error | 1.4.3 | SVG style block flagged with contrast ratio of 1:1 (likely false positive — SVG style block; CSS fill rules misread as visible text) | SVG icon block #svg_block_69b1334d5ff78 — embedded `<style>` tag | Add `aria-hidden="true" focusable="false"` to the parent `<svg>` element |
| 20 | Error | 1.4.3 | SVG style block flagged with contrast ratio of 1:1 (likely false positive — SVG style block; CSS fill rules misread as visible text) | SVG icon block #svg_block_69b1334d60250 — embedded `<style>` tag | Add `aria-hidden="true" focusable="false"` to the parent `<svg>` element |
| 21 | Error | 1.4.3 | SVG style block flagged with contrast ratio of 1:1 (likely false positive — SVG style block; CSS fill rules misread as visible text) | SVG icon block #svg_block_69b1334d604a6 — embedded `<style>` tag | Add `aria-hidden="true" focusable="false"` to the parent `<svg>` element |
| 22 | Error | 1.4.3 | SVG style block flagged with contrast ratio of 1:1 (likely false positive — SVG style block; CSS fill rules misread as visible text) | SVG icon block #svg_block_69b1334d60710 — embedded `<style>` tag | Add `aria-hidden="true" focusable="false"` to the parent `<svg>` element |
| 23 | Error | 1.4.3 | SVG style block flagged with contrast ratio of 1:1 (likely false positive — SVG style block; CSS fill rules misread as visible text) | SVG icon block #svg_block_69b1334d609f2 — embedded `<style>` tag | Add `aria-hidden="true" focusable="false"` to the parent `<svg>` element |
| 24 | Error | 1.4.3 | SVG style block flagged with contrast ratio of 1:1 (likely false positive — SVG style block; CSS fill rules misread as visible text) | SVG icon block #svg_block_69b1334d60ca4 — embedded `<style>` tag | Add `aria-hidden="true" focusable="false"` to the parent `<svg>` element |
| 25 | Error | 1.4.3 | SVG style block flagged with contrast ratio of 1:1 (likely false positive — SVG style block; CSS fill rules misread as visible text) | SVG icon block #svg_block_69b1334d60f73 — embedded `<style>` tag | Add `aria-hidden="true" focusable="false"` to the parent `<svg>` element |
| 26 | Error | 1.4.3 | SVG style block flagged with contrast ratio of 1:1 (likely false positive — SVG style block; CSS fill rules misread as visible text) | SVG icon block #svg_block_69b1334d6120f — embedded `<style>` tag | Add `aria-hidden="true" focusable="false"` to the parent `<svg>` element |
| 27 | Error | 1.4.3 | SVG style block flagged with contrast ratio of 1:1 (likely false positive — SVG style block; CSS fill rules misread as visible text) | SVG icon block #svg_block_69b1334d61494 — embedded `<style>` tag | Add `aria-hidden="true" focusable="false"` to the parent `<svg>` element |
| 28 | Error | 1.4.3 | SVG style block flagged with contrast ratio of 1:1 (likely false positive — SVG style block; CSS fill rules misread as visible text) | SVG icon block #svg_block_69b1334d616a5 — embedded `<style>` tag | Add `aria-hidden="true" focusable="false"` to the parent `<svg>` element |
| 29 | Error | 1.4.3 | SVG style block flagged with contrast ratio of 1:1 (likely false positive — SVG style block; CSS fill rules misread as visible text) | SVG icon block #svg_block_69b1334d61900 — embedded `<style>` tag | Add `aria-hidden="true" focusable="false"` to the parent `<svg>` element |
| 30 | Error | 1.4.3 | SVG style block flagged with contrast ratio of 1:1 (likely false positive — SVG style block; CSS fill rules misread as visible text) | SVG icon block #svg_block_69b1334d61ba3 — embedded `<style>` tag | Add `aria-hidden="true" focusable="false"` to the parent `<svg>` element |
| 31 | Error | 1.4.3 | SVG style block flagged with contrast ratio of 1:1 (likely false positive — SVG style block; CSS fill rules misread as visible text) | SVG icon block #svg_block_69b1334d61ddf — embedded `<style>` tag | Add `aria-hidden="true" focusable="false"` to the parent `<svg>` element |
| 32 | Error | 1.4.3 | SVG style block flagged with contrast ratio of 1:1 (likely false positive — SVG style block; CSS fill rules misread as visible text) | SVG icon block #svg_block_69b1334d62013 — embedded `<style>` tag | Add `aria-hidden="true" focusable="false"` to the parent `<svg>` element |
| 33 | Error | 1.4.3 | SVG style block flagged with contrast ratio of 1:1 (likely false positive — SVG style block; CSS fill rules misread as visible text) | SVG icon block #svg_block_69b1334d622d1 — embedded `<style>` tag | Add `aria-hidden="true" focusable="false"` to the parent `<svg>` element |
| 34 | Error | 1.4.3 | SVG style block flagged with contrast ratio of 1:1 (likely false positive — SVG style block; CSS fill rules misread as visible text) | SVG icon block #svg_block_69b1334d625eb — embedded `<style>` tag | Add `aria-hidden="true" focusable="false"` to the parent `<svg>` element |
| 35 | Error | 1.4.3 | SVG style block flagged with contrast ratio of 1:1 (likely false positive — SVG style block; CSS fill rules misread as visible text) | SVG icon block #svg_block_69b1334d628a8 — embedded `<style>` tag | Add `aria-hidden="true" focusable="false"` to the parent `<svg>` element |
| 36 | Error | 1.4.3 | SVG style block flagged with contrast ratio of 1:1 (likely false positive — SVG style block; CSS fill rules misread as visible text) | SVG icon block #svg_block_69b1334d62b41 — embedded `<style>` tag | Add `aria-hidden="true" focusable="false"` to the parent `<svg>` element |
| 37 | Error | 1.4.3 | SVG style block flagged with contrast ratio of 1:1 (likely false positive — SVG style block; CSS fill rules misread as visible text) | SVG icon block #svg_block_69b1334d62d9d — embedded `<style>` tag | Add `aria-hidden="true" focusable="false"` to the parent `<svg>` element |
| 38 | Error | 1.4.3 | SVG style block flagged with contrast ratio of 1:1 (likely false positive — SVG style block; CSS fill rules misread as visible text) | SVG icon block #svg_block_69b1334d6304b — embedded `<style>` tag | Add `aria-hidden="true" focusable="false"` to the parent `<svg>` element |
| 39 | Error | 1.4.3 | SVG style block flagged with contrast ratio of 1:1 (likely false positive — SVG style block; CSS fill rules misread as visible text) | SVG icon block #svg_block_69b1334d63289 — embedded `<style>` tag | Add `aria-hidden="true" focusable="false"` to the parent `<svg>` element |
| 40 | Error | 1.4.3 | SVG style block flagged with contrast ratio of 1:1 (likely false positive — SVG style block; CSS fill rules misread as visible text) | SVG icon block #svg_block_69b1334d634a3 — embedded `<style>` tag | Add `aria-hidden="true" focusable="false"` to the parent `<svg>` element |
| 41 | Error | 1.4.3 | SVG style block flagged with contrast ratio of 1:1 (likely false positive — SVG style block; CSS fill rules misread as visible text) | SVG icon block #svg_block_69b1334d636c9 — embedded `<style>` tag | Add `aria-hidden="true" focusable="false"` to the parent `<svg>` element |
| 42 | Error | 1.4.3 | SVG style block flagged with contrast ratio of 1:1 (likely false positive — SVG style block; CSS fill rules misread as visible text) | SVG icon block #svg_block_69b1334d63975 — embedded `<style>` tag | Add `aria-hidden="true" focusable="false"` to the parent `<svg>` element |
| 43 | Error | 1.4.3 | SVG style block flagged with contrast ratio of 1:1 (likely false positive — SVG style block; CSS fill rules misread as visible text) | SVG icon block #svg_block_69b1334d63c0c — embedded `<style>` tag | Add `aria-hidden="true" focusable="false"` to the parent `<svg>` element |
| 44 | Error | 1.4.3 | SVG style block flagged with contrast ratio of 1:1 (likely false positive — SVG style block; CSS fill rules misread as visible text) | SVG icon block #svg_block_69b1334d63e2a — embedded `<style>` tag | Add `aria-hidden="true" focusable="false"` to the parent `<svg>` element |
| 45 | Error | 1.4.3 | SVG style block flagged with contrast ratio of 1:1 (likely false positive — SVG style block; CSS fill rules misread as visible text) | SVG icon block #svg_block_69b1334d640cd — embedded `<style>` tag | Add `aria-hidden="true" focusable="false"` to the parent `<svg>` element |
| 46 | Error | 4.1.2 | Anchor element found with a valid href but no link content — link contains only a `<br>` tag with no visible or accessible text | Locations section — Google Maps link in address block (maps.app.goo.gl/R3pmxUhhfbAfnPhN8) | Replace the `<br>` inside the link with descriptive text such as "Get directions to our office" or add `aria-label` |
| 47 | Error | 1.4.3 | SVG style block flagged with contrast ratio of 1:1 (likely false positive — SVG style block; CSS fill rules misread as visible text) | SVG icon block #svg_block_69b1334d642cc — embedded `<style>` tag | Add `aria-hidden="true" focusable="false"` to the parent `<svg>` element |
| 48 | Error | 1.4.3 | SVG style block flagged with contrast ratio of 1:1 (likely false positive — SVG style block; CSS fill rules misread as visible text) | SVG icon block #svg_block_69b1334d644e2 — embedded `<style>` tag | Add `aria-hidden="true" focusable="false"` to the parent `<svg>` element |
| 49 | Error | 1.4.3 | SVG style block flagged with contrast ratio of 1:1 (likely false positive — SVG style block; CSS fill rules misread as visible text) | SVG icon block #svg_block_69b1334d646f3 — embedded `<style>` tag | Add `aria-hidden="true" focusable="false"` to the parent `<svg>` element |
| 50 | Error | 1.4.3 | SVG style block flagged with contrast ratio of 1:1 (likely false positive — SVG style block; CSS fill rules misread as visible text) | SVG icon block #svg_block_69b1334d64940 — embedded `<style>` tag | Add `aria-hidden="true" focusable="false"` to the parent `<svg>` element |
| 51 | Error | 1.4.3 | SVG style block flagged with contrast ratio of 1:1 (likely false positive — SVG style block; CSS fill rules misread as visible text) | SVG icon block #svg_block_69b1334d64be1 — embedded `<style>` tag | Add `aria-hidden="true" focusable="false"` to the parent `<svg>` element |
| 52 | Error | 1.4.3 | SVG style block flagged with contrast ratio of 1:1 (likely false positive — SVG style block; CSS fill rules misread as visible text) | SVG icon block #svg_block_69b1334d64e6e — embedded `<style>` tag | Add `aria-hidden="true" focusable="false"` to the parent `<svg>` element |
| 53 | Error | 1.4.3 | SVG style block flagged with contrast ratio of 1:1 (likely false positive — SVG style block; CSS fill rules misread as visible text) | SVG icon block #svg_block_69b1334d65091 — embedded `<style>` tag | Add `aria-hidden="true" focusable="false"` to the parent `<svg>` element |
| 54 | Error | 1.4.3 | SVG style block flagged with contrast ratio of 1:1 (likely false positive — SVG style block; CSS fill rules misread as visible text) | SVG icon block #svg_block_69b1334d652e5 — embedded `<style>` tag | Add `aria-hidden="true" focusable="false"` to the parent `<svg>` element |
| 55 | Error | 1.4.3 | SVG style block flagged with contrast ratio of 1:1 (likely false positive — SVG style block; CSS fill rules misread as visible text) | SVG icon block #svg_block_69b1334d6557e — embedded `<style>` tag | Add `aria-hidden="true" focusable="false"` to the parent `<svg>` element |
| 56 | Error | 1.4.3 | SVG style block flagged with contrast ratio of 1:1 (likely false positive — SVG style block; CSS fill rules misread as visible text) | SVG icon block #svg_block_69b1334d657da — embedded `<style>` tag | Add `aria-hidden="true" focusable="false"` to the parent `<svg>` element |
| 57 | Error | 1.4.3 | Blog post title link "Rash Treatment: When Should You See a Dermatologist?" has insufficient contrast ratio of 3.21:1 | Blog section — recent posts listing, first post title heading link | Change link color from teal (~#00a19b) to #006b69 or darker to achieve 4.5:1 contrast |
| 58 | Error | 1.4.3 | Blog post title link "Hyperhidrosis Treatment: How to Stop Excessive Sweating" has insufficient contrast ratio of 3.21:1 | Blog section — recent posts listing, second post title heading link | Change link color from teal (~#00a19b) to #006b69 or darker to achieve 4.5:1 contrast |
| 59 | Error | 1.4.3 | Blog post title link "How Often Should You Get a Chemical Peel for Best Results?" has insufficient contrast ratio of 3.21:1 | Blog section — recent posts listing, third post title heading link | Change link color from teal (~#00a19b) to #006b69 or darker to achieve 4.5:1 contrast |

---

#### Note on SVG Style Block Contrast Failures (50 instances — likely false positives)

The scanner flagged **50 instances** of `<style>` blocks embedded within SVG elements (`#svg_block_69b1334d5e256 > style`, etc.) as having a contrast ratio of 1:1 — which would indicate invisible text. These are SVG icon blocks (likely treatment/service icons displayed in a grid on the page) where the SVG definition includes an inline `<style type="text/css">` tag containing CSS rules like `.st0{fill-rule:evenodd;clip-rule:evenodd;...}`.

**Why this is almost certainly a false positive:** The CSS content inside these `<style>` tags is not rendered text — it is CSS code processed by the browser's style engine. The pa11y/htmlcs scanner, when evaluating contrast, may be treating the text content of `<style>` elements as visible rendered text, leading to a spurious 1:1 contrast result.

**Recommended action:**
1. Visually inspect the SVG icons on the homepage to confirm they are visible and legible.
2. If the icons are purely decorative, add `aria-hidden="true"` to each `<svg>` element to remove them from the accessibility tree entirely. This will suppress these false positives in future scans and is best practice for decorative SVGs: `<svg aria-hidden="true" focusable="false">`.
3. If the icons convey information (e.g., each represents a treatment type), add a `<title>` element inside the SVG and `aria-labelledby` on the `<svg>`: `<svg aria-labelledby="icon-title-1"><title id="icon-title-1">Skin Examination</title>...</svg>`.
4. These 50 items should be re-scanned after adding `aria-hidden` or `<title>` — the scanner should no longer flag the style blocks.

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
- Add `aria-hidden="true" focusable="false"` to all 50 decorative SVG icon elements in the treatment/services grid. This will eliminate the false-positive contrast warnings on their embedded `<style>` blocks.

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
- **Most common violation:** 1.4.3 Contrast Minimum — 58 instances (8 genuine link contrast failures + 50 SVG `<style>` false positives)
- **Second most common:** 4.1.2 Name, Role, Value — 1 instance (empty Google Maps link)
- **Platform:** WordPress (likely with a custom or premium dermatology theme)
- **WCAG Principles affected:** Perceivable, Robust
- **Estimated remediation effort:** Very low (half a developer day — the link color fix is a single CSS change; the SVG fix is adding `aria-hidden` to a batch of elements)
- **Highest risk area:** Teal body link color — affects all navigation links within content sections, location links, and blog post titles across the entire site
- **Notable finding:** This site has the fewest genuine issues of all 5 sites reviewed. After the link color fix and empty link fix, the site would pass all automated checks and present well for a manual audit.
