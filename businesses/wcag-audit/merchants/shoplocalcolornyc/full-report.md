# WCAG Accessibility Scan Report
## Shop Local Color NYC — shoplocalcolornyc.com
**Scan Date:** March 15, 2026
**Standard:** WCAG 2.1 Level AA
**Tool:** pa11y (htmlcs engine)

---

### Disclaimer
This report documents programmatically detectable accessibility issues found via automated scanning. Automated tools detect approximately 57% of WCAG 2.1 issues. Manual testing by an accessibility specialist is recommended for complete conformance assessment. This report does not constitute legal advice or guarantee ADA/EAA compliance.

---

### Executive Summary

Shop Local Color NYC's Shopify-powered storefront returned 30 accessibility violations. The issues are spread across all four WCAG principles and reflect a consistent pattern: interactive elements throughout the site — navigation icons, search buttons, social media links, and product image links — have no text labels, making them entirely opaque to screen readers and keyboard users. A blind or low-vision customer would be unable to search the store, navigate to social media profiles, identify the store logo, or understand what product images link to.

Three product images in the featured collection section are also missing alt text entirely, and the email newsletter signup field has no accessible label. Two popup iframes from the MailChimp signup form have no title attributes. Additionally, footer attribution text has a 1.66:1 contrast ratio — well below the 4.5:1 minimum — rendering it unreadable to anyone with low contrast sensitivity.

The top three priorities for remediation are: (1) add descriptive `aria-label` attributes to all icon-only buttons and links (search, social icons, navigation icons), (2) add alt text to all product images and logo images used as links, and (3) label the email signup field with a proper form label.

---

### Compliance Scorecard

| WCAG Principle | Status | Issues |
|---|---|---|
| Perceivable (1.x) | Fail | 11 |
| Operable (2.x) | Fail | 2 |
| Understandable (3.x) | Pass | 0 |
| Robust (4.x) | Fail | 17 |

---

### Issues by Severity

#### Error Issues — 30 Total

---

**PERCEIVABLE — Missing Alt Text and Image Links (7 issues)**

| # | Issue | WCAG Criterion | Element | Impact |
|---|---|---|---|---|
| 1 | The store logo image used as the homepage link has no alt text | 1.1.1 Non-text Content / 1.3.1 | Logo link in header | Critical — screen reader users cannot identify the site logo or navigate home |
| 2 | The hero slideshow image linking to "All Products" has no alt text describing the link destination | 1.1.1 | Hero slide 1 product image link | Serious — users cannot determine where this link leads |
| 3 | The hero slideshow image linking to the Gift Card product page has no alt text | 1.1.1 | Hero slide 2 gift card image link | Serious |
| 4 | A featured collection item image (first row) is missing an alt attribute entirely | 1.1.1 | Featured collection product photo | Serious — screen readers skip the image entirely |
| 5 | A featured collection item image (second item) is missing an alt attribute entirely | 1.1.1 | Featured collection product photo | Serious |
| 6 | A featured collection item image (third item, .heic file) is missing an alt attribute entirely | 1.1.1 | Featured collection product photo | Serious |
| 7 | Empty heading tag `<h2>` found on hero slide with no content | 1.3.1 Info and Relationships | Empty slide title heading, slide 2 | Moderate — creates confusing page structure for screen readers |

**How to fix (logo):** The logo `<img>` inside the homepage link needs an `alt` attribute that names the store. Change it to `<img src="..." alt="Local Color NYC — Home">`. The alt text on a logo link should describe the link destination, not just the image.

**How to fix (hero slide images):** For each slideshow image that is wrapped in a link, add descriptive alt text to the `<img>` element: e.g., `alt="Shop all Local Color NYC products"` for the all-products link and `alt="Gift card — give the gift of Local Color NYC"` for the gift card slide.

**How to fix (missing collection images):** Add an `alt` attribute to each featured collection product image. The alt text should describe the product shown: e.g., `alt="Colorful tote bag by Local Color NYC"`. If the product name is available from your Shopify theme data, populate alt text dynamically from the product title.

**How to fix (empty heading):** Remove the empty `<h2 class="slide-title"></h2>` element from the second hero slide in the Shopify theme template. If the heading is conditionally populated, add a check so it is only rendered when it has content.

---

**PERCEIVABLE — Color Contrast (3 issues)**

| # | Issue | WCAG Criterion | Element | Impact |
|---|---|---|---|---|
| 8 | Footer "Local Color NYC" link text has 1.66:1 contrast ratio (required: 4.5:1) | 1.4.3 Contrast (Minimum) | Footer attribution link — site name | Moderate |
| 9 | Footer "Shopify Theme" link text has 1.66:1 contrast ratio | 1.4.3 | Footer attribution link — theme credit | Moderate |
| 10 | Footer "Powered by Shopify" link text has 1.66:1 contrast ratio | 1.4.3 | Footer attribution link — Shopify credit | Moderate |

**How to fix:** In your Shopify theme's CSS, locate the footer attribution text color (likely set on `#close p a` or similar). Change the color to at least `#757575` on a white background. The current color is too light. These are small footer links, but they still must meet WCAG contrast requirements.

---

**PERCEIVABLE — Form Label (1 issue)**

| # | Issue | WCAG Criterion | Element | Impact |
|---|---|---|---|---|
| 11 | Email newsletter signup input field has no accessible label | 1.3.1 / 4.1.2 | Email address field in newsletter signup section | Serious — screen readers will not announce the field's purpose |

**How to fix:** Add a `<label>` element associated with the email input. If a visible label is not desired for design reasons, add `aria-label="Enter your email address"` directly to the `<input>` element. Placeholder text alone ("Enter Your Email Address") is not a substitute for a label.

---

**OPERABLE — Iframes Without Titles (2 issues)**

| # | Issue | WCAG Criterion | Element | Impact |
|---|---|---|---|---|
| 12 | MailChimp popup signup form contains an unlabeled banner iframe | 2.4.1 Bypass Blocks | Popup signup form, banner iframe | Moderate |
| 13 | MailChimp popup signup form contains an unlabeled modal iframe | 2.4.1 | Popup signup form, modal iframe | Moderate |

**How to fix:** These iframes are injected by the MailChimp embedded form script. If the MailChimp form provider allows configuration, check for an option to add frame titles. Otherwise, after the MailChimp script loads, use JavaScript to retroactively add titles: `document.querySelector('#PopupSignupForm_0 iframe').title = 'Email signup form'`. If there are two iframes, address each one.

---

**ROBUST — Unlabeled Interactive Elements (17 issues)**

| # | Issue | WCAG Criterion | Element | Impact |
|---|---|---|---|---|
| 14 | Mobile navigation search button (icon only, no text) has no accessible name | 4.1.2 Name, Role, Value | Mobile nav search submit button | Critical — keyboard/screen reader users cannot activate search |
| 15 | Mobile navigation search text input has no accessible name | 4.1.2 / 1.3.1 | Mobile search input field | Critical — screen readers do not know this is a search field |
| 16 | Mobile navigation search text input missing label — second instance (desktop search, duplicate ID "q") | 1.3.1 | Desktop search input field | Serious |
| 17 | Desktop search submit button (icon only) has no accessible name | 4.1.2 | Desktop search form submit button | Critical |
| 18 | Mobile nav search input has duplicate `id="q"` — both mobile and desktop forms share the same ID | 4.1.1 Parsing | Search input (both forms) | Serious — ID collision breaks label associations |
| 19 | Mobile navigation link to /search has no text content (icon only) | 4.1.2 | Mobile menu search icon link | Critical |
| 20 | Mobile navigation link to /account/login has no text content (icon only) | 4.1.2 | Mobile menu account/login icon link | Critical — users cannot identify this as a login link |
| 21 | Hero slideshow "Previous" navigation button has no text content | 4.1.2 | Slideshow previous-slide control | Serious — keyboard users cannot navigate the slideshow |
| 22 | Hero slideshow "Next" navigation button has no text content | 4.1.2 | Slideshow next-slide control | Serious |
| 23 | Hero slide 1 overlay "Shop Now" (or similar) link has no text content | 4.1.2 | Hero slide 1 call-to-action overlay link | Serious |
| 24 | Hero slide 2 (gift card) overlay call-to-action link has no text content | 4.1.2 | Hero slide 2 call-to-action overlay link | Serious |
| 25 | Facebook social icon link has no text content | 4.1.2 | Footer Facebook link | Serious — screen readers cannot identify this as a Facebook link |
| 26 | Pinterest social icon link has no text content | 4.1.2 | Footer Pinterest link | Serious |
| 27 | Instagram social icon link has no text content | 4.1.2 | Footer Instagram link | Serious |
| 28 | Email newsletter submit button (paper plane icon) has no accessible name | 4.1.2 | Newsletter form submit button | Critical — users cannot submit the newsletter form |
| 29 | Mobile search input missing label — first instance (unlabeled) | 4.1.2 | Mobile nav search input | Serious |
| 30 | Desktop search input missing label — first instance | 1.3.1 | Desktop nav search input | Serious |

**How to fix (icon-only buttons and links):** Every interactive element that has no visible text must have an `aria-label` attribute. Apply the following fixes:

- Search submit buttons: `<button type="submit" aria-label="Search the store">`
- Search inputs: `<input type="text" aria-label="Search" ...>` (also fix duplicate `id="q"` — use `id="search-mobile"` and `id="search-desktop"`)
- Mobile nav search link: `<a href="/search" aria-label="Search">`
- Mobile nav login link: `<a href="/account/login" aria-label="Sign in to your account">`
- Slideshow previous: `<a class="flex-prev" aria-label="Previous slide">`
- Slideshow next: `<a class="flex-next" aria-label="Next slide">`
- Slideshow overlay links: add descriptive text or `aria-label` describing the destination (e.g., `aria-label="Shop all products"`)
- Facebook: `<a href="..." aria-label="Shop Local Color NYC on Facebook">`
- Pinterest: `<a href="..." aria-label="Shop Local Color NYC on Pinterest">`
- Instagram: `<a href="..." aria-label="Follow Local Color NYC on Instagram">`
- Newsletter submit: `<button type="submit" aria-label="Subscribe to our newsletter">`

---

### Remediation Roadmap

**Week 1 — Critical:**
- Add `aria-label` to all icon-only buttons: search buttons (mobile and desktop), newsletter submit button, mobile nav login link, mobile nav search link
- Fix the duplicate `id="q"` — rename the two search inputs to distinct IDs
- Add alt text to the store logo link image

**Week 2–3 — Serious:**
- Add `aria-label` to slideshow Previous/Next controls
- Add alt text to all three featured collection images and both hero slideshow image-only links
- Add `aria-label` to hero slide overlay links
- Add `aria-label` or visible label to email newsletter input
- Add `aria-label` to all three social icon links (Facebook, Pinterest, Instagram)
- Remove the empty `<h2>` heading from hero slide 2

**Month 2 — Moderate:**
- Fix footer attribution text contrast (3 links)
- Add `title` attributes to the two MailChimp popup iframes

---

### Technical Summary

- **Pages scanned:** 1
- **Total violations:** 30
- **Unique issue types:** 8
- **Most common issue:** 4.1.2 Name, Role, Value — unlabeled interactive elements (17 instances)
- **Principles affected:** Perceivable (11), Operable (2), Robust (17)
- **Root cause pattern:** Icon-only interactive elements throughout the Shopify theme have no accessible names, making the site largely unusable for screen reader and keyboard-only users
