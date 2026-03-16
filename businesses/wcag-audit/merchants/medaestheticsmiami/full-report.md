# WCAG Accessibility Scan Report
## Med Aesthetics Miami — https://medaestheticsmiami.com
**Scan Date:** March 15, 2026
**Standard:** WCAG 2.1 Level AA
**Tool:** pa11y (htmlcs engine)

---

### Disclaimer
This report documents programmatically detectable accessibility issues found via automated scanning. Automated tools detect approximately 57% of WCAG 2.1 issues. Manual testing by an accessibility specialist is recommended for complete conformance assessment. This report does not constitute legal advice or guarantee ADA/EAA compliance.

---

### Executive Summary

The Med Aesthetics Miami homepage was scanned and returned **105 errors** — all WCAG 2.1 Level AA violations. The site is built on WordPress with the Contact Form 7 (CF7) plugin and an Enfold/Kaliber-style theme, and the violations closely reflect common accessibility gaps in these platforms when not configured correctly.

The dominant issue pattern is **27 links with no accessible name**, meaning buttons and links that contain only icon graphics (social media icons, close buttons) and carry no text label that screen readers can announce. These affect the entire social media sidebar, repeated in multiple widgets throughout the page. The second major pattern is **13 form fields missing labels** across the multiple contact forms embedded on the page (Contact Form 7 instances), which would prevent a blind user from completing a consultation booking, service inquiry, or newsletter signup. There are also **18 contrast failures** affecting promotional text and decorative arrows.

The overall accessibility posture of this site is **poor-to-moderate**. The core clinical content (service descriptions, treatment information) is likely text-based and readable, but all interactive elements — navigation menus, contact forms, social links, search — have significant barriers. For a medical aesthetics practice where booking consultations and inquiries are core business actions, inaccessible contact forms represent both a usability failure and a legal risk. **Top 3 priorities: (1) Add accessible names to all empty social links and icon buttons. (2) Label all Contact Form 7 form fields. (3) Fix color contrast on promotional/section text.**

---

### Compliance Scorecard

| WCAG Principle | Guideline | Status | Issues Found |
|---|---|---|---|
| **1 — Perceivable** | 1.3.1 Info and Relationships (form labels, fieldsets) | FAIL | 18 |
| **1 — Perceivable** | 1.4.3 Contrast Minimum | FAIL | 18 |
| **1 — Perceivable** | 1.4.1 Use of Color / 1.4.11 Non-text Contrast | FAIL | 1 |
| **1 — Perceivable** | 1.3.1 Deprecated HTML (align attribute) | FAIL | 2 |
| **2 — Operable** | 2.4.1 Bypass Blocks (iframe title) | FAIL | 2 |
| **3 — Understandable** | (no specific failures detected) | PASS | 0 |
| **4 — Robust** | 4.1.1 Parsing (duplicate IDs) | FAIL | 9 |
| **4 — Robust** | 4.1.2 Name, Role, Value (unlabeled controls & links) | FAIL | 55 |

---

### Issues by Severity

#### Critical Issues (55)

These issues directly prevent screen reader users from navigating the site and using its interactive features.

---

**Group A: Links with no accessible content — 27 instances**

| # | Issue | WCAG Criterion | Element | Location | Impact |
|---|---|---|---|---|---|
| 1 | Close button for slide-out menu has no text | 4.1.2 | `<a href="#" class="eltd-close-side-menu"><span aria-hidden="true">...</span></a>` | Top of page — mobile/side menu close button | Screen reader announces the URL "#" instead of a meaningful action |
| 2 | Facebook social icon link has no accessible name | 4.1.2 | `<a href="https://www.facebook.com/MedAestheticsM/"><span aria-hidden="true">...</span></a>` | Social media widget sidebar (widget-17) | Announced as link to URL, not "Facebook" |
| 3 | Instagram social icon link has no accessible name | 4.1.2 | `<a href="https://www.instagram.com/medaestheticsmiami/"><span aria-hidden="true">...</span></a>` | Social media widget sidebar (widget-18) | Announced as URL, not "Instagram" |
| 4 | Pinterest social icon link has no accessible name | 4.1.2 | `<a href="https://www.pinterest.com/medaestheticsm/med-aesthetics-miami/"><span aria-hidden="true">...</span></a>` | Social media widget sidebar (widget-19) | Announced as URL |
| 5 | YouTube social icon link has no accessible name | 4.1.2 | `<a href="https://www.youtube.com/channel/UCb830NdXwIXCpGnPD8KXw2g"><span aria-hidden="true">...</span></a>` | Social media widget sidebar (widget-20) | Announced as URL |
| 6 | LinkedIn social icon link has no accessible name | 4.1.2 | `<a href="https://www.linkedin.com/in/medaestheticsmiami/"><span aria-hidden="true">...</span></a>` | Social media widget sidebar (widget-28) | Announced as URL |
| 7–11 | Second set of social icon links (Facebook, Instagram, Pinterest, YouTube, LinkedIn) | 4.1.2 | Same pattern repeated in widget-29 through widget-33 area | Social icons repeated in second widget area (possibly footer or second sidebar) | Same impact — all social links inaccessible |
| 12–27 | Remaining empty anchor elements throughout the page | 4.1.2 | Various `<a>` tags with icon-only content and `aria-hidden` on the inner span | Various locations including navigation and promotional areas | Screen reader users cannot identify these link destinations |

**How to fix:** Each social media link needs an `aria-label` attribute that names the platform. The icon `<span>` is already marked `aria-hidden="true"` (which is correct), but since it's the only content in the link, the link itself has no name. Add `aria-label` to each anchor:
```html
<a href="https://www.facebook.com/MedAestheticsM/" aria-label="Med Aesthetics Miami on Facebook">
<a href="https://www.instagram.com/medaestheticsmiami/" aria-label="Med Aesthetics Miami on Instagram">
<a href="https://www.youtube.com/channel/UCb830NdXwIXCpGnPD8KXw2g" aria-label="Med Aesthetics Miami on YouTube">
<a href="https://www.linkedin.com/in/medaestheticsmiami/" aria-label="Med Aesthetics Miami on LinkedIn">
<a href="https://www.pinterest.com/medaestheticsm/med-aesthetics-miami/" aria-label="Med Aesthetics Miami on Pinterest">
```
For the close-menu button: `<a href="#" aria-label="Close navigation menu">`. Also consider changing the `<a>` to a `<button>` for the close action since it doesn't navigate anywhere.

---

**Group B: Form fields without accessible names — 17 instances (across 8 + 5 + 4 subtypes)**

| # | Issue | WCAG Criterion | Element | Location | Impact |
|---|---|---|---|---|---|
| 1 | Site-wide search field has no label | 4.1.2 / 1.3.1 | `<input type="text" name="s" class="eltd-search-field">` | Page-level search bar (appears to be a slide-in search) | Screen reader cannot identify field purpose |
| 2–4 | Name text field in Contact Form 7 instances (appears 3x across 3 form embeds) | 4.1.2 / 1.3.1 | `<input class="wpcf7-text wpcf7-validates-as-required">` | Contact/consultation forms (wpcf7-f14021-o1, -o2, -o3) | Cannot identify "Name" field |
| 5–7 | Email text field in Contact Form 7 instances (3 form embeds) | 4.1.2 / 1.3.1 | `<input class="wpcf7-email wpcf7-validates-as-required">` | Contact forms (3 instances) | Cannot identify "Email" field |
| 8–10 | Telephone field in Contact Form 7 instances (3 form embeds, but 4 total) | 4.1.2 / 1.3.1 | `<input class="wpcf7-tel wpcf7-validates-as-required">` | Contact forms | Cannot identify "Phone" field |
| 11–15 | Textarea (message/comment field) in Contact Form 7 instances (5 total) | 4.1.2 / 1.3.1 | `<textarea class="wpcf7-textarea">` | Contact forms | Cannot identify message field |

**How to fix:** In the Contact Form 7 plugin editor, each field needs an explicit label. CF7 supports labels natively:
```
[label* your-name "Your Name"]
[text* your-name placeholder "Full Name"]
```
Or better practice, add `<label>` tags in the CF7 form template:
```html
<label for="your-name">Full Name</label>
[text* your-name id:your-name]
```
For the search field, add: `<input type="text" name="s" aria-label="Search this website">`.

**Note:** The same form appears to be embedded 3–5 times on the homepage. Each duplicate adds its own set of unlabeled fields. Consider whether all instances are necessary, or if they can be consolidated.

---

**Group C: Form fields missing label elements — 13 additional instances (1.3.1 F68)**

These are the same fields as Group B, additionally flagged under WCAG 1.3.1 (Info and Relationships). The fix is the same — adding proper `<label>` elements. Listed separately here because the scanner flagged them under two different WCAG criteria.

---

#### Serious Issues (27)

---

**Group D: Fieldsets without legend elements — 5 instances**

| # | Issue | WCAG Criterion | Element | Location | Impact |
|---|---|---|---|---|---|
| 1–5 | Five `<fieldset>` elements in Contact Form 7 have no `<legend>` | 1.3.1 H71.NoLegend | `<fieldset class="hidden-fields-container">` | Contact forms (wpcf7-f14021-o1 through o5) | Screen readers cannot identify what group of fields the fieldset represents |

**How to fix:** Each `<fieldset>` element must contain a `<legend>`. Even if the fieldset is used for hidden/honeypot fields, it still needs a legend. Add:
```html
<fieldset class="hidden-fields-container">
  <legend class="visually-hidden">Hidden fields</legend>
  <!-- hidden inputs -->
</fieldset>
```
Use a CSS `visually-hidden` class to hide it from visual display while keeping it accessible.

---

**Group E: Fieldsets without accessible names via ARIA — 5 instances**

| # | Issue | WCAG Criterion | Element | Location | Impact |
|---|---|---|---|---|---|
| 1–5 | Same five fieldsets also fail the 4.1.2 name check | 4.1.2 H91.Fieldset.Name | `<fieldset class="hidden-fields-container">` | Contact forms | Compound failure — both missing legend and missing ARIA name |

**How to fix:** Covered by the fix above (adding `<legend>`). Once a `<legend>` is present, both issues resolve.

---

**Group F: Color contrast failures — 18 instances**

| # | Issue | WCAG Criterion | Element | Location | Impact |
|---|---|---|---|---|---|
| 1 | Promotional subtitle text has contrast ratio below threshold | 1.4.3 | `<h5 class="eltd-section-subtitle">Get ready for Spring...</h5>` | Promotional column section — section subtitle | Low-vision users cannot read seasonal promotional text |
| 2 | Decorative arrow text `⮞` rendered in red (`color: red`) with contrast ratio below threshold | 1.4.3 | `<span style="color: red;">⮞</span>` | Promotional column section — list or CTA area | Decorative character is illegible to low-vision users |
| 3–18 | 16 additional elements across the promotional and content sections with contrast failures | 1.4.3 | Various heading, paragraph, and span elements | Throughout page sections | General readability failures for low-vision users |

**How to fix:** For the subtitle, change the text color in the theme's CSS or inline style. The recommended minimum is `#767676` on a white background; for a more professional result, use `#444444` or darker. For the red arrow span, either remove it or ensure its background/foreground contrast meets 4.5:1. Do not use pure `red` (#FF0000) over white — it only achieves a 4:1 ratio, just below the threshold. Use `#c00000` or darker.

---

**Group G: Duplicate element IDs — 9 instances**

| # | Issue | WCAG Criterion | Element | Location | Impact |
|---|---|---|---|---|---|
| 1–9 | Multiple WooCommerce "Add to Cart" describedby spans share duplicate IDs | 4.1.1 Parsing | `<span id="woocommerce_loop_add_to_cart_link_describedby_10363">` | Product listing / service listing area | `aria-describedby` references break when IDs are duplicated; screen readers may read wrong description or fail to find it |

**How to fix:** This is a WooCommerce theme/plugin issue. Update WooCommerce to the latest version, as recent versions fixed duplicate ID generation in product loop templates. If the theme overrides `content-product.php`, update that template. Each "add to cart" block must generate a unique ID, typically by appending the product ID: `id="woocommerce_loop_add_to_cart_link_describedby_{{ product.id }}"`.

---

#### Moderate Issues (4)

---

**Group H: Iframes missing title attributes — 2 instances**

| # | Issue | WCAG Criterion | Element | Location | Impact |
|---|---|---|---|---|---|
| 1 | Google Drive video embed has no title | 2.4.1 H64.1 | `<iframe src="https://drive.google.com/file/d/1UAvWEL3DxWMno2kpNt5SiAnZnYCNxU_4/preview" class="home-vid-testimoinals">` | Testimonials section — embedded video | Screen readers cannot identify iframe content; may announce "frame" with no context |
| 2 | Hidden iframe (likely a pixel or third-party tag) has no title | 2.4.1 H64.1 | `<iframe style="display: none;">` | Body — invisible tracking frame | Although invisible, screen readers still encounter it |

**How to fix:**
- Testimonial video: `<iframe title="Med Aesthetics Miami — Patient Testimonials Video" src="...">`
- Hidden frame: `<iframe title="Tracking pixel" style="display: none;">`

---

**Group I: Deprecated `align` attribute on paragraph elements — 2 instances**

| # | Issue | WCAG Criterion | Element | Location | Impact |
|---|---|---|---|---|---|
| 1–2 | `<p align="center">` uses a deprecated HTML attribute for layout | 1.3.1 H49.AlignAttr | `<p align="center" style="">` | Popup/modal content area (poptinFormSubmit overlay) | Deprecated HTML attributes may not be interpreted correctly by all assistive technologies |

**How to fix:** Replace `align="center"` with CSS: `<p style="text-align: center;">` or add a CSS class `class="text-center"` with the corresponding CSS rule.

---

#### Minor Issues (2)

---

**Group J: Low-contrast large text (WCAG AA 3:1 threshold) — 1 instance**

| # | Issue | WCAG Criterion | Element | Location | Impact |
|---|---|---|---|---|---|
| 1 | Phone number link in gold/amber color fails large-text contrast | 1.4.3 G145.Fail (3:1 for large text) | `<a style="color: #e3b533 !important;" href="tel://3053567402">305-356-7402</a>` | Promotional section — phone number CTA | Low-vision users may not be able to read the phone number |

**How to fix:** The color `#e3b533` (gold) does not achieve 3:1 contrast ratio against the background in this context. Darken the color to at least `#a07800` or choose a different color that achieves the required ratio. For phone numbers that are primary CTAs, stronger contrast is worth prioritizing.

---

**Group K: Unlabeled chat button — 1 instance**

| # | Issue | WCAG Criterion | Element | Location | Impact |
|---|---|---|---|---|---|
| 1 | Quriobot live chat button has no accessible label | 4.1.2 | `<button id="quriobotPopupButton" role="button" data-content="CHAT LIVE">` | Fixed chat widget (bottom of page) | The `data-content` attribute is not read by screen readers; button announces as unlabeled |

**How to fix:** Add `aria-label="Open live chat"` to the button element: `<button id="quriobotPopupButton" aria-label="Open live chat">`. If this is a third-party widget, report the issue to Quriobot support and request an accessible version of their widget.

---

### Remediation Roadmap

**Week 1 — Critical (Links & Form Names):**
- Add `aria-label` to all 5 social media icon links in both widget locations (10 total links across 2 widget areas). This is a 15-minute fix in the WordPress widget settings or theme template.
- Add `aria-label="Close navigation menu"` to the slide-out menu close button.
- In Contact Form 7, edit all form templates to add `<label>` elements for every field: Name, Email, Phone, and Message. This applies to all 3–5 embedded form instances.
- Add `aria-label="Search this website"` to the site search input field.

**Week 2–3 — Serious (Fieldsets, Contrast, Duplicate IDs):**
- Add `<legend class="visually-hidden">Hidden fields</legend>` to each Contact Form 7 fieldset (5 instances).
- Update WooCommerce or its templates to generate unique IDs for Add to Cart elements (9 duplicate IDs).
- Review and fix all 18 contrast failures. Focus first on the promotional section text and the phone number CTA, which are high-visibility CTAs.

**Month 2 — Moderate:**
- Add `title` attributes to both iframes (testimonial video and hidden tracking frame).
- Replace deprecated `align="center"` attributes with CSS in the popup/modal content.
- Darken the phone number link color (`#e3b533`) to meet the 3:1 large-text contrast ratio.

**Ongoing — Minor:**
- Report the Quriobot chat widget inaccessibility to the vendor; request accessible widget version.
- Add WCAG scanning to the development/update workflow so WooCommerce or plugin updates don't reintroduce issues.
- Audit all other pages (services, about, contact, individual treatment pages) as this scan only covered the homepage.

---

### Technical Summary
- **Pages scanned:** 1 (homepage — https://medaestheticsmiami.com)
- **Total violations:** 105
- **All issue types:** error (105 errors, 0 warnings, 0 notices)
- **Unique violation types:** 14
- **Most common violation:** 4.1.2 / Links with no accessible name — 27 instances (social icon links throughout page)
- **Second most common:** 1.3.1 / Unlabeled form fields — 13 instances (Contact Form 7 fields)
- **Third most common:** 1.4.3 / Insufficient color contrast — 18 instances
- **Platform:** WordPress + Contact Form 7 + WooCommerce + Kaliber/Enfold theme
- **WCAG Principles affected:** All four (Perceivable, Operable, Understandable, Robust)
- **Estimated remediation effort:** Medium (2–3 developer days; most issues are template-level fixes in WordPress)
- **Highest risk area:** Contact forms — the primary lead-generation mechanism of a medical practice is inaccessible to screen reader users
