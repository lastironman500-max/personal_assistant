# WCAG Accessibility Scan Report
## YAL New York — https://yalnewyork.com
**Scan Date:** March 15, 2026
**Standard:** WCAG 2.1 Level AA
**Tool:** pa11y (htmlcs engine)

---

### Disclaimer
This report documents programmatically detectable accessibility issues found via automated scanning. Automated tools detect approximately 57% of WCAG 2.1 issues. Manual testing by an accessibility specialist is recommended for complete conformance assessment. This report does not constitute legal advice or guarantee ADA/EAA compliance.

---

### Executive Summary

The YAL New York homepage was scanned and returned **132 errors** — all classified as Level AA violations under WCAG 2.1. Every single issue flagged was of type "error," indicating that there are no merely advisory or warning-level findings: the site has systemic, confirmed failures across all four WCAG principles (Perceivable, Operable, Understandable, and Robust).

The most critical patterns are: **35 product images missing alt text**, **34 image-only links missing alt text** (meaning screen reader users cannot tell what product is being linked to), and **36 elements with insufficient color contrast** (meaning low-vision users cannot read key content including section titles, prices, and promotional text). Together, these three patterns account for 105 of the 132 issues and represent a near-complete breakdown of image and visual accessibility.

The remaining 27 issues involve unlabeled form controls (login, registration, search, newsletter) and a handful of structural/semantic problems. From an ADA risk perspective, the unlabeled forms are the highest-priority items after images, since a screen reader user cannot complete a login, register an account, or subscribe to the newsletter without guessing what each field expects. The site's overall accessibility posture is **poor** — it would be extremely difficult for a blind or low-vision user to browse products, identify what is on sale, or create an account. **Top 3 priorities: (1) Add alt text to all product images and image links. (2) Fix color contrast on all text elements. (3) Add labels to all form fields.**

---

### Compliance Scorecard

| WCAG Principle | Guideline | Status | Issues Found |
|---|---|---|---|
| **1 — Perceivable** | 1.1.1 Non-text Content (alt text) | FAIL | 69 |
| **1 — Perceivable** | 1.3.1 Info and Relationships (form labels) | FAIL | 6 |
| **1 — Perceivable** | 1.4.3 Contrast (Minimum) | FAIL | 36 |
| **2 — Operable** | 2.4.1 Bypass Blocks (iframe title) | FAIL | 1 |
| **3 — Understandable** | (no specific failures detected) | PASS | 0 |
| **4 — Robust** | 4.1.1 Parsing (duplicate IDs) | FAIL | 1 |
| **4 — Robust** | 4.1.2 Name, Role, Value (unlabeled controls) | FAIL | 19 |

---

### Issues by Severity

#### Critical Issues (105)

These issues directly prevent blind, low-vision, or keyboard-only users from accessing core content and functionality.

---

**Group A: Product images missing alt text — 35 instances**

| # | Issue | WCAG Criterion | Element | Location | Impact |
|---|---|---|---|---|---|
| 1–35 | `img` element missing `alt` attribute | 1.1.1 Non-text Content | `<img class="owl-lazy product__hover-img">` | Product carousel/grid — hover images for each product card | Screen readers announce "image" with no description; users cannot identify product |

**How to fix:** Every product image in the carousel and grid needs an `alt` attribute describing the product. For example, for a ribbed knit vest: `<img alt="Ribbed Knit Mock Neck Vest in Camel">`. The alt text should match the product name and color. For decorative hover-effect images that duplicate the primary image, use `alt=""` (empty) to mark them as decorative so screen readers skip them.

---

**Group B: Image-only links missing alt text — 34 instances**

| # | Issue | WCAG Criterion | Element | Location | Impact |
|---|---|---|---|---|---|
| 1–34 | Image is the only link content but has no alt text | 1.1.1 / 2.4.4 Link Purpose | `<a href="...product-url..."><img src="..."></a>` | Product card links in the "In Carts Today" and featured product sections | Screen reader announces the URL instead of the product name; user cannot navigate products |

**How to fix:** Each product link that contains only an image must have a descriptive alt on the image. For the link pointing to `yalnewyork.com/ribbed-knit-mock-neck-vest-camel/`, use: `<img alt="Ribbed Knit Mock Neck Vest — Camel">`. Go through every product card link and add the product name and variant as the alt text.

---

**Group C: Color contrast failures — 36 instances**

| # | Issue | WCAG Criterion | Element | Location | Impact |
|---|---|---|---|---|---|
| 1 | Section heading "IN CARTS TODAY" — contrast ratio 3.41:1 (need 4.5:1) | 1.4.3 Contrast | `<h3 class="slider__title">` | Product carousel section heading | Low-vision users cannot read heading |
| 2–35 | Price labels ("2 items", product prices) — low contrast | 1.4.3 Contrast | `<p class="price">` | Product cards throughout carousel | Price information is invisible to low-vision users |
| 36 | Other text elements in carousel/promotional areas | 1.4.3 Contrast | Various | Throughout homepage | General readability barrier |

**How to fix:** The current text color used for prices, item counts, and section headings does not have sufficient contrast against its background. The scanner recommends changing the text color to `#767676` or darker as a minimum. In practice, move toward a near-black such as `#333333` for body text and `#222222` for headings to satisfy the 4.5:1 ratio requirement. Use the [WebAIM Contrast Checker](https://webaim.org/resources/contrastchecker/) to verify each combination before publishing.

---

#### Serious Issues (19)

These prevent screen reader and keyboard users from using interactive features of the site.

---

**Group D: Buttons without accessible names — 7 instances**

| # | Issue | WCAG Criterion | Element | Location | Impact |
|---|---|---|---|---|---|
| 1 | Mobile navigation toggle button has no label | 4.1.2 Name, Role, Value | `<button id="nav-bar-btn" class="btn-navbar navbar-toggle">` | Header — mobile hamburger menu button | Screen reader announces "button" with no indication of purpose |
| 2 | Search submit button contains only an SVG icon, no label | 4.1.2 | `<button class="btn"><svg class="img-search"></svg></button>` | Header search bar — submit button | Announced as unlabeled button |
| 3 | Close popup button has no label | 4.1.2 | `<button class="close-popup btn-close-popup"><span></span></button>` | Login/account popup — close button | User cannot tell how to dismiss the popup |
| 4–7 | Additional unlabeled buttons (account area and checkout flow) | 4.1.2 | Various `<button>` elements | Account and checkout sections | Cannot be identified by screen reader users |

**How to fix:** Add `aria-label` attributes to every icon-only button that describes its action:
- Mobile menu: `<button aria-label="Open navigation menu">`
- Search submit: `<button aria-label="Search">`
- Popup close: `<button aria-label="Close login popup">`
- Cart buttons: `<button aria-label="Add to cart">`

---

**Group E: Form fields without accessible names — 10 instances**

| # | Issue | WCAG Criterion | Element | Location | Impact |
|---|---|---|---|---|---|
| 1–2 | Two search input fields have no label (relying only on placeholder) | 4.1.2 / 1.3.1 | `<input type="text" name="search1">`, `<input type="text" name="search">` | Header search bar (desktop and mobile versions) | Screen readers do not read placeholder text as a label |
| 3–4 | Email inputs in newsletter signup and login popup have no label | 4.1.2 / 1.3.1 | `<input type="email" id="mce-EMAIL">`, `<input type="email" id="input-email-popup">` | Newsletter bar and login popup | Screen reader cannot announce field purpose |
| 5–6 | Password fields in login popup and account page have no label | 4.1.2 / 1.3.1 | `<input type="password" id="input-password-popup">`, `<input type="password" id="input-password">` | Login popup and account login page | Cannot determine field purpose |
| 7–8 | First name and other text fields in account registration have no label | 4.1.2 / 1.3.1 | `<input id="input-firstname">` | Account registration/profile section | Cannot determine field purpose |
| 9 | Forgot-password email field has no label | 4.1.2 / 1.3.1 | `<input id="input-email-forgot">` | Password reset form | Cannot determine field purpose |
| 10 | Telephone field has no label | 4.1.2 / 1.3.1 | `<input type="tel" id="input-telephone">` | Account registration | Cannot determine field purpose |

**How to fix:** Each form field needs a visible `<label>` element linked via the `for` attribute, or an `aria-label` on the input itself. Examples:

For the search bar: `<label for="search-input" class="visually-hidden">Search products</label><input type="text" id="search-input" name="search">` (use CSS `visually-hidden` class to hide label visually while keeping it available to screen readers).

For the newsletter: `<input type="email" id="mce-EMAIL" aria-label="Your email address for newsletter signup">`.

For the login popup: Add a visible label or `aria-label="Email address"` and `aria-label="Password"` to each field.

**Do not rely solely on placeholder text** — placeholders disappear when the user starts typing, and many screen readers do not read them as field labels.

---

#### Moderate Issues (2)

---

**Group F: Duplicate element ID — 1 instance**

| # | Issue | WCAG Criterion | Element | Location | Impact |
|---|---|---|---|---|---|
| 1 | Two elements share the `id="search"` | 4.1.1 Parsing | `<div id="search">` | Desktop and mobile search dropdowns both use the same ID | Assistive technologies use IDs to navigate; duplicate IDs break this and can cause unpredictable behavior |

**How to fix:** Give each element a unique ID. Rename the mobile version to `id="search-mobile"` and the desktop version to `id="search-desktop"`. Update any JavaScript or CSS selectors that reference `#search` to use the new, distinct IDs.

---

**Group G: Link with no accessible content — 1 instance**

| # | Issue | WCAG Criterion | Element | Location | Impact |
|---|---|---|---|---|---|
| 1 | Account icon link in header has no text or alt text | 4.1.2 / 2.4.4 | `<a href="https://yalnewyork.com/login/"><svg class="c_user-icon"></svg></a>` | Header — user account icon | Screen reader announces link URL instead of purpose |

**How to fix:** Add `aria-label="My Account"` to the anchor tag: `<a href="https://yalnewyork.com/login/" aria-label="My Account">`. Alternatively, add a visually hidden text span inside the link.

---

#### Minor Issues (1)

**Group H: iframe missing title attribute — 1 instance**

| # | Issue | WCAG Criterion | Element | Location | Impact |
|---|---|---|---|---|---|
| 1 | An invisible tracking iframe has no `title` attribute | 2.4.1 Bypass Blocks / H64.1 | `<iframe height="1" width="1" style="position:absolute...">` | Body — hidden tracking pixel iframe | Screen readers encounter this iframe and cannot identify its purpose |

**How to fix:** Add `title="Tracking pixel"` to the iframe element. Even though it is invisible, assistive technologies still traverse it: `<iframe height="1" width="1" title="Tracking pixel" ...>`.

---

### Remediation Roadmap

**Week 1 — Critical (Images & Contrast):**
- Add `alt` attributes to all 35 product images in the carousel and grid. Write meaningful alt text using the product name and color from the product catalog.
- Add `alt` attributes to all 34 image-only links (product cards linking to product pages).
- Audit all text colors site-wide and update to meet a 4.5:1 contrast ratio. Priority targets: section headings (`.slider__title`), price text (`.price`), and any text rendered over light gray or white backgrounds.

**Week 2–3 — Serious (Forms & Buttons):**
- Add `aria-label` attributes to all 7 unlabeled buttons: mobile nav toggle, search submit, popup close button, and any cart/action buttons.
- Add `<label>` elements (or `aria-label` attributes) to all 10 unlabeled form fields: both search inputs, newsletter email, login email, both password fields, first name, telephone, forgot-password email.
- Verify all labels are programmatically associated (`for` attribute matching field `id`) and not just visually proximate.

**Month 2 — Moderate:**
- Fix the duplicate `id="search"` by assigning unique IDs to desktop and mobile search components and updating associated JavaScript.
- Add `aria-label="My Account"` to the header account icon link.

**Ongoing — Minor:**
- Add `title="Tracking pixel"` to the hidden tracking iframe.
- Establish a policy that new images added to the product catalog always include alt text in the CMS before publishing.
- Integrate automated WCAG scanning (pa11y or axe-core) into the CI/CD pipeline to catch regressions before they reach production.

---

### Technical Summary
- **Pages scanned:** 1 (homepage — https://yalnewyork.com)
- **Total violations:** 132
- **All issue types:** error (132 errors, 0 warnings, 0 notices)
- **Unique violation types:** 12
- **Most common violation:** 1.1.1 Non-text Content — missing alt text on images (35 instances)
- **Second most common:** 1.1.1 Non-text Content — image-only links without alt text (34 instances)
- **Third most common:** 1.4.3 Contrast Minimum — insufficient color contrast (36 instances)
- **WCAG Principles affected:** All four (Perceivable, Operable, Understandable, Robust)
- **Estimated remediation effort:** Medium (2–4 developer days for critical/serious; most fixes are repetitive and templated)
- **Highest risk area:** Product image catalog — every product image is missing alt text, making the core shopping experience inaccessible to screen reader users
