# WCAG Accessibility Scan Report
## Giardino Salads — giardinosalads.com
**Scan Date:** March 15, 2026
**Standard:** WCAG 2.1 Level AA
**Tool:** pa11y (htmlcs engine)

---

### Disclaimer
This report documents programmatically detectable accessibility issues found via automated scanning. Automated tools detect approximately 57% of WCAG 2.1 issues. Manual testing by an accessibility specialist is recommended for complete conformance assessment. This report does not constitute legal advice or guarantee ADA/EAA compliance.

---

### Executive Summary

Giardino Salads' website returned 57 accessibility violations across a single page scan, representing the highest issue count among the five businesses audited. The violations fall into two dominant categories: color contrast failures and broken element semantics. The contrast failures alone account for 51 of the 57 issues, concentrated in the hero slideshow "Order Now" buttons (9 instances at a 1:1 ratio — rendering text effectively invisible against its background) and the embedded Instagram feed widget (42 instances across 10 posts). While many of these are repetitive instances of the same root issue, the underlying problems require targeted remediation in the theme configuration and the Instagram feed plugin settings.

The remaining 6 issues cover broken form semantics, duplicate element IDs, and an unlabeled iframe — problems that directly impair screen reader and assistive technology users. The most critical of these is the reCAPTCHA textarea element, which has no accessible label whatsoever, combined with an unlabeled embedded iframe and two anchor elements in the Instagram lightbox that carry no link content or identifier.

The site's top three remediation priorities are: (1) fix the "Order Now" button text color in the hero slider so that text has at least a 3:1 contrast ratio against its background, (2) configure the Instagram feed plugin to use accessible color values for post metadata and "more" links, and (3) resolve the three duplicate `id="ordering"` attribute instances that break browser and assistive technology ID-based navigation.

---

### Compliance Scorecard

| WCAG Principle | Status | Issues |
|---|---|---|
| Perceivable (1.x) | Fail | 51 |
| Operable (2.x) | Fail | 1 |
| Understandable (3.x) | Pass | 0 |
| Robust (4.x) | Fail | 5 |

---

### Issues by Severity

#### Error Issues — 57 Total

---

**PERCEIVABLE — Contrast Failures (51 issues)**

| # | Issue | WCAG Criterion | Element | Impact |
|---|---|---|---|---|
| 1 | Hero slider "Order Now" button text is invisible (1:1 contrast ratio) — slide 1 | 1.4.3 Contrast (Minimum) | "Order Now" button, hero slide 1 | Critical — users cannot read the primary call-to-action |
| 2 | Hero slider "Order Now" button text is invisible (1:1 contrast ratio) — slide 2 | 1.4.3 | "Order Now" button, hero slide 2 | Critical |
| 3 | Hero slider "Order Now" button text is invisible (1:1 contrast ratio) — slide 3 | 1.4.3 | "Order Now" button, hero slide 3 | Critical |
| 4 | Hero slider "Order Now" button text is invisible (1:1 contrast ratio) — slide 4 | 1.4.3 | "Order Now" button, hero slide 4 | Critical |
| 5 | Hero slider "Order Now" button text is invisible (1:1 contrast ratio) — slide 5 | 1.4.3 | "Order Now" button, hero slide 5 | Critical |
| 6 | Hero slider "Order Now" button text is invisible (1:1 contrast ratio) — slide 6 | 1.4.3 | "Order Now" button, hero slide 6 | Critical |
| 7 | Hero slider "Order Now" button text is invisible (1:1 contrast ratio) — slide 7 | 1.4.3 | "Order Now" button, hero slide 7 | Critical |
| 8 | Hero slider "Order Now" button text is invisible (1:1 contrast ratio) — slide 8 | 1.4.3 | "Order Now" button, hero slide 8 | Critical |
| 9 | Hero slider "Order Now" button text is invisible (1:1 contrast ratio) — slide 9 | 1.4.3 | "Order Now" button, hero slide 9 | Critical |
| 10 | "Hand-Crafted Salads" menu category heading has 1:1 contrast (invisible) | 1.4.3 | Menu category heading | Serious |
| 11 | "Warm Grain Bowls" menu category heading has 1:1 contrast (invisible) | 1.4.3 | Menu category heading | Serious |
| 12 | "Gourmet Wraps" menu category heading has 1:1 contrast (invisible) | 1.4.3 | Menu category heading | Serious |
| 13 | Instagram post 1 — "..." expand link has 2.85:1 contrast (required: 4.5:1) | 1.4.3 | Instagram feed post 1, caption expand link | Moderate |
| 14 | Instagram post 1 — likes count has 3.23:1 contrast (required: 4.5:1) | 1.4.3 | Instagram feed post 1, likes | Moderate |
| 15 | Instagram post 1 — comments count has 3.23:1 contrast (required: 4.5:1) | 1.4.3 | Instagram feed post 1, comments | Moderate |
| 16 | Instagram post 2 — "..." expand link has 2.85:1 contrast | 1.4.3 | Instagram feed post 2, caption expand link | Moderate |
| 17 | Instagram post 2 — likes count has 3.23:1 contrast | 1.4.3 | Instagram feed post 2, likes | Moderate |
| 18 | Instagram post 2 — comments count has 3.23:1 contrast | 1.4.3 | Instagram feed post 2, comments | Moderate |
| 19 | Instagram post 3 — "..." expand link has 2.85:1 contrast | 1.4.3 | Instagram feed post 3, caption expand link | Moderate |
| 20 | Instagram post 3 — likes count has 3.23:1 contrast | 1.4.3 | Instagram feed post 3, likes | Moderate |
| 21 | Instagram post 3 — comments count has 3.23:1 contrast | 1.4.3 | Instagram feed post 3, comments | Moderate |
| 22 | Instagram post 4 — "..." expand link has 2.85:1 contrast | 1.4.3 | Instagram feed post 4, caption expand link | Moderate |
| 23 | Instagram post 4 — likes count has 3.23:1 contrast | 1.4.3 | Instagram feed post 4, likes | Moderate |
| 24 | Instagram post 4 — comments count has 3.23:1 contrast | 1.4.3 | Instagram feed post 4, comments | Moderate |
| 25 | Instagram post 5 — "..." expand link has 2.85:1 contrast | 1.4.3 | Instagram feed post 5, caption expand link | Moderate |
| 26 | Instagram post 5 — likes count has 3.23:1 contrast | 1.4.3 | Instagram feed post 5, likes | Moderate |
| 27 | Instagram post 5 — comments count has 3.23:1 contrast | 1.4.3 | Instagram feed post 5, comments | Moderate |
| 28 | Instagram post 6 — "..." expand link has 2.85:1 contrast | 1.4.3 | Instagram feed post 6, caption expand link | Moderate |
| 29 | Instagram post 6 — likes count has 3.23:1 contrast | 1.4.3 | Instagram feed post 6, likes | Moderate |
| 30 | Instagram post 6 — comments count has 3.23:1 contrast | 1.4.3 | Instagram feed post 6, comments | Moderate |
| 31 | Instagram post 7 — "..." expand link has 2.85:1 contrast | 1.4.3 | Instagram feed post 7, caption expand link | Moderate |
| 32 | Instagram post 7 — likes count has 3.23:1 contrast | 1.4.3 | Instagram feed post 7, likes | Moderate |
| 33 | Instagram post 7 — comments count has 3.23:1 contrast | 1.4.3 | Instagram feed post 7, comments | Moderate |
| 34 | Instagram post 8 — "..." expand link has 2.85:1 contrast | 1.4.3 | Instagram feed post 8, caption expand link | Moderate |
| 35 | Instagram post 8 — likes count has 3.23:1 contrast | 1.4.3 | Instagram feed post 8, likes | Moderate |
| 36 | Instagram post 8 — comments count has 3.23:1 contrast | 1.4.3 | Instagram feed post 8, comments | Moderate |
| 37 | Instagram post 9 — "..." expand link has 2.85:1 contrast | 1.4.3 | Instagram feed post 9, caption expand link | Moderate |
| 38 | Instagram post 9 — likes count has 3.23:1 contrast | 1.4.3 | Instagram feed post 9, likes | Moderate |
| 39 | Instagram post 9 — comments count has 3.23:1 contrast | 1.4.3 | Instagram feed post 9, comments | Moderate |
| 40 | Instagram post 10 — "..." expand link has 2.85:1 contrast | 1.4.3 | Instagram feed post 10, caption expand link | Moderate |
| 41 | Instagram post 10 — likes count has 3.23:1 contrast | 1.4.3 | Instagram feed post 10, likes | Moderate |
| 42 | Instagram post 10 — comments count has 3.23:1 contrast | 1.4.3 | Instagram feed post 10, comments | Moderate |

**How to fix (hero slider buttons):** In the Elementor theme settings for the hero section, change the "Order Now" button text color to a value that achieves at least 3:1 contrast against the button background. The scanner recommends `#949494` as a minimum; a darker value such as white (#ffffff) on a dark button background is preferable. Check each slide individually since the contrast ratio is 1:1, meaning text and background are the same color.

**How to fix (menu category headings):** Open the Elementor editor for the menu section and update the text color of "Hand-Crafted Salads," "Warm Grain Bowls," and "Gourmet Wraps" headings so they achieve at least 3:1 contrast against their background. Currently all three read as 1:1, indicating the text is the same color as the background.

**How to fix (Instagram feed widget):** In the Smash Balloon Instagram Feed plugin settings (or equivalent), go to the Style settings and update the post metadata color from `rgb(140, 143, 154)` to at least `#737681` for likes/comments counts. For the "more" expand links, change the color to at least `#767676`. These color changes will apply across all posts automatically.

---

**PERCEIVABLE — Form Field Labeling (1 issue)**

| # | Issue | WCAG Criterion | Element | Impact |
|---|---|---|---|---|
| 43 | The reCAPTCHA hidden textarea has no accessible label | 1.3.1 Info and Relationships | reCAPTCHA response field | Serious — screen readers will announce this unlabeled field |

**How to fix:** This reCAPTCHA hidden textarea (`id="g-recaptcha-response-100000"`) is injected by Google's reCAPTCHA v2 script. Add `aria-hidden="true"` to the element so screen readers skip it entirely, since it is not a user-facing field. If you control the reCAPTCHA wrapper, add the attribute via JavaScript after the widget loads: `document.getElementById('g-recaptcha-response-100000').setAttribute('aria-hidden', 'true')`.

---

**OPERABLE — Iframes Without Titles (1 issue)**

| # | Issue | WCAG Criterion | Element | Impact |
|---|---|---|---|---|
| 44 | A hidden iframe in the page footer has no title attribute | 2.4.1 Bypass Blocks | Hidden iframe at bottom of page | Moderate — screen readers announce unlabeled frames |

**How to fix:** Add a descriptive `title` attribute to the iframe. If the iframe serves no user-facing purpose (e.g., it is a tracking pixel or script loader), add both `title="Tracking frame"` and `aria-hidden="true"` to suppress it from the accessibility tree.

---

**ROBUST — Duplicate IDs and Broken Links (6 issues)**

| # | Issue | WCAG Criterion | Element | Impact |
|---|---|---|---|---|
| 45 | `id="ordering"` is used on 3 separate elements (Order Now link, Order Catering link, and a third Order Now link) | 4.1.1 Parsing | Three "Order Now" / "Order Catering" buttons | Serious — assistive technologies cannot reliably identify elements |
| 46 | `id="ordering"` duplicate — instance 2 | 4.1.1 | "Order Catering" button | Serious |
| 47 | `id="ordering"` duplicate — instance 3 | 4.1.1 | Second "Order Now" button | Serious |
| 48 | The reCAPTCHA textarea has no name accessible to the accessibility API | 4.1.2 Name, Role, Value | reCAPTCHA hidden textarea | Serious |
| 49 | Instagram lightbox "share close" button is an anchor with no text content and no ID | 4.1.2 | Lightbox share-close button | Critical — keyboard and screen reader users cannot activate this control |
| 50 | Instagram lightbox "close" button is an anchor with no text content and no ID | 4.1.2 | Lightbox close (×) button | Critical — keyboard and screen reader users cannot close the lightbox |

**How to fix (duplicate IDs):** Each element on a page must have a unique `id`. Rename the three buttons: give them IDs like `ordering-now-header`, `ordering-catering`, and `ordering-now-footer` respectively. Update any anchor links (`href="#ordering"`) to match the renamed IDs.

**How to fix (Instagram lightbox close buttons):** In the Instagram feed plugin template or custom CSS/JS overrides, add accessible labels to the close buttons. For the share-close link: `<a class="sbi_share_close" aria-label="Close share options">`. For the lightbox close link: `<a class="sbi_lb-close" aria-label="Close lightbox">`. Alternatively, convert these to `<button>` elements, which is the semantically correct element for actions that do not navigate to a URL.

---

### Remediation Roadmap

**Week 1 — Critical (address immediately):**
- Fix the duplicate `id="ordering"` — assign unique IDs to all three order buttons
- Add `aria-label` to both Instagram lightbox close/share anchors so keyboard users can dismiss the lightbox
- Fix hero slider "Order Now" button text color — change from matching the background to a readable contrast value (the entire primary call-to-action is currently invisible)

**Week 2–3 — Serious:**
- Fix menu category headings ("Hand-Crafted Salads," "Warm Grain Bowls," "Gourmet Wraps") — update text colors so they are visible against their backgrounds
- Add `aria-hidden="true"` to the reCAPTCHA hidden textarea and the hidden iframe
- Add a `title` attribute to the hidden footer iframe

**Month 2 — Moderate:**
- Update Instagram Feed plugin color settings for post metadata (likes counts, comment counts, and caption expand links) to meet 4.5:1 minimum contrast — this single plugin config change resolves 39 of the 57 total violations

---

### Technical Summary

- **Pages scanned:** 1
- **Total violations:** 57
- **Unique issue types:** 6
- **Most common issue:** 1.4.3 Color Contrast Minimum (51 instances)
- **Principles affected:** Perceivable (51), Operable (1), Robust (5)
- **Root cause concentration:** 39 of 57 issues originate from the Instagram Feed plugin's default color settings; 9 originate from the Elementor hero slider button styling
