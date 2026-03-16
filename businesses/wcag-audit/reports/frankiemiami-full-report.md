# WCAG Accessibility Scan Report
## Frankie Miami — https://www.frankiemiami.com
**Scan Date:** March 15, 2026
**Standard:** WCAG 2.1 Level AA
**Tool:** pa11y (htmlcs engine)

---

### Disclaimer
This report documents programmatically detectable accessibility issues found via automated scanning. Automated tools detect approximately 57% of WCAG 2.1 issues. Manual testing by an accessibility specialist is recommended for complete conformance assessment. This report does not constitute legal advice or guarantee ADA/EAA compliance.

---

### Executive Summary

The Frankie Miami homepage was scanned and returned **58 errors** — all WCAG 2.1 Level AA violations. The site is a Shopify-based fashion boutique, and its accessibility failures are heavily dominated by **color contrast issues**: 39 of the 58 errors are contrast failures affecting nearly every interactive and informational element on the page, including the entire navigation bar, all product price labels, the "Add to cart" button, the store address, all footer links, and the newsletter subscribe button. The entire site appears to render white or very light text on a white or near-white background (or vice versa), creating a sitewide contrast emergency rather than isolated failures.

The second major issue pattern is **16 SVG icons using `role="presentation"` while containing semantic child elements** — meaning the SVG markup sends conflicting signals to assistive technologies: it declares itself as decorative while embedding paths and shapes that screen readers may attempt to process as meaningful content.

There are also 2 additional structural issues: one unlabeled form input (the quantity field in the product add-to-cart form), and one duplicate form ID for the currency localization form.

The overall accessibility posture of this site is **poor**. The contrast failures affect essentially every element a shopper needs to interact with — navigation, products, pricing, and checkout initiation. A person using a screen magnifier, a user with low vision, or anyone viewing the site in bright sunlight will struggle to use this site. From an ADA risk perspective, the breadth of contrast failures (39 elements, touching navigation, product listings, and checkout) signals a systemic theme-level problem rather than isolated oversights. **Top 3 priorities: (1) Fix contrast on all text elements — the entire color scheme needs review. (2) Fix SVG `role="presentation"` errors on interactive icon elements. (3) Label the quantity input field.**

---

### Compliance Scorecard

| WCAG Principle | Guideline | Status | Issues Found |
|---|---|---|---|
| **1 — Perceivable** | 1.3.1 Info and Relationships (SVG semantics, form labels) | FAIL | 17 |
| **1 — Perceivable** | 1.4.3 Contrast Minimum | FAIL | 39 |
| **3 — Understandable** | (no specific failures detected) | PASS | 0 |
| **4 — Robust** | 4.1.1 Parsing (duplicate IDs) | FAIL | 1 |
| **4 — Robust** | 4.1.2 Name, Role, Value (unlabeled input) | FAIL | 1 |

---

### Issues by Severity

#### Critical Issues (39)

---

**Group A: Color contrast failures — 39 instances**

The site appears to use a near-white or very light color scheme that fails to provide sufficient contrast throughout. The contrast failures are not isolated to one section — they span the full page from header to footer.

**Navigation Bar (Header)**

| # | Issue | WCAG Criterion | Element | Location | Contrast Ratio | Impact |
|---|---|---|---|---|---|---|
| 1 | "ABOUT US" navigation link | 1.4.3 | `<a href="/pages/about-us-2" class="Heading u-h6">ABOUT US</a>` | Header — main nav, first link | 1:1 | Completely invisible |
| 2 | "CONTACT" navigation link | 1.4.3 | `<a href="/pages/contact-us" class="Heading u-h6">CONTACT</a>` | Header — main nav, second link | 1:1 | Completely invisible |
| 3 | "INSTAGRAM" navigation link | 1.4.3 | `<a href="http://www.instagram.com/frankiemiami" class="Heading u-h6">INSTAGRAM</a>` | Header — main nav, third link | 1:1 | Completely invisible |
| 4 | "NEW ARRIVALS" navigation link | 1.4.3 | `<a href="/collections/fall-winter" class="Heading u-h6">NEW ARRIVALS</a>` | Header — main nav, fourth link | 1:1 | Completely invisible |
| 5 | Site name "frankie." heading in header | 1.4.3 | `<span class="Heading u-h4">frankie. </span>` | Header — site name/logo text | 1:1 | Brand name is invisible |
| 6 | Currency selector button ("USD$") | 1.4.3 | `<button class="SelectButton Link Link--primary u-h8">USD$</button>` | Header — currency localization form | 1:1 | Cannot read or interact with currency selector |
| 7 | "Account" utility link | 1.4.3 | `<a href="/account" class="Heading Link Link--primary Text--subdued u-h8">Account</a>` | Header — utility nav, right side | 1:1 | Cannot find account link |
| 8 | "Search" utility link | 1.4.3 | `<a href="/search" class="Heading Link Link--primary Text--subdued u-h8" data-action="toggle-search">Search</a>` | Header — utility nav, right side | 1:1 | Cannot find search |
| 9 | "Cart" utility link | 1.4.3 | `<a href="/cart" class="Heading u-h6" data-action="open-drawer">Cart (…)</a>` | Header — utility nav, cart link | 1:1 | Cannot find cart link |
| 10 | Cart item count "0" | 1.4.3 | `<span class="Header__CartCount">0</span>` | Header — cart item count badge | 1:1 | Cannot see cart count |

**Note:** A contrast ratio of 1:1 means text color and background color are identical — the text is completely invisible. This is not a marginal failure; these elements are literally rendered invisible. This suggests the theme renders white text on a white background, or that a CSS conflict is zeroing out the color. The header background may be transparent, allowing a white page background to show through while the text is also white. Inspect the rendered header in Chrome DevTools to identify the actual computed color values.

**Product Grid / Featured Products**

| # | Issue | WCAG Criterion | Element | Location | Contrast Ratio | Impact |
|---|---|---|---|---|---|---|
| 11 | Product price "$220" | 1.4.3 | `<span class="ProductItem__Price Price Text--subdued">$220</span>` | Featured products grid — first product price | 2.71:1 | Low-vision users cannot read price |
| 12 | Product price "$180" | 1.4.3 | `<span class="ProductItem__Price Price Text--subdued">$180</span>` | Featured products grid — second product price | 2.71:1 | Cannot read price |
| 13 | Product price "$230" | 1.4.3 | Same pattern — third product | Featured products grid | 2.71:1 | Cannot read price |
| 14 | Product price "$360" | 1.4.3 | Same pattern — fourth product | Featured products grid | 2.71:1 | Cannot read price |
| 15 | Product price "$180" | 1.4.3 | Same pattern — fifth product | Featured products grid | 2.71:1 | Cannot read price |
| 16 | Product price "$190" | 1.4.3 | Same pattern — sixth product | Featured products grid | 2.71:1 | Cannot read price |
| 17 | Product price "$280" | 1.4.3 | Same pattern — seventh product | Featured products grid | 2.71:1 | Cannot read price |
| 18 | Product price "$495" | 1.4.3 | Same pattern — eighth product | Featured products grid | 2.71:1 | Cannot read price |

**Featured Product / Add to Cart Section**

| # | Issue | WCAG Criterion | Element | Location | Contrast Ratio | Impact |
|---|---|---|---|---|---|---|
| 19 | Featured product price "$360" in larger format | 1.4.3 | `<span class="ProductMeta__Price Price Text--subdued u-h4">$360</span>` | Featured product section | 2.71:1 | Cannot read price |
| 20 | "Add to cart" button text | 1.4.3 | `<span>Add to cart</span>` inside the Add to Cart button | Featured product — add to cart button | 2.71:1 | Button text is difficult to read |
| 21 | "View all products" button | 1.4.3 | `<a href="/collections/fall-winter" class="Button Button--primary">View all products</a>` | Featured products section — CTA button | 1:1 | Button is completely invisible |

**Newsletter Signup (Header Popup)**

| # | Issue | WCAG Criterion | Element | Location | Contrast Ratio | Impact |
|---|---|---|---|---|---|---|
| 22 | Newsletter "Subscribe" button | 1.4.3 | `<button class="Form__Submit Button Button--primary Button--full" type="submit">Subscribe</button>` | Newsletter signup popup (header area) | 1:1 | Button completely invisible |

**Footer**

| # | Issue | WCAG Criterion | Element | Location | Contrast Ratio | Impact |
|---|---|---|---|---|---|---|
| 23 | "Come visit us:" paragraph | 1.4.3 | `<p>Come visit us:</p>` | Footer — store address section | 2.71:1 | Cannot read store address intro |
| 24 | Store address line 1: "1891 Purdy Ave" | 1.4.3 | `<p>1891 Purdy Ave</p>` | Footer — store address | 2.71:1 | Cannot read physical address |
| 25 | Store address line 2: "Miami Beach, FL" | 1.4.3 | `<p>Miami Beach, FL</p>` | Footer — store address | 2.71:1 | Cannot read city/state |
| 26 | Store ZIP code: "33139" | 1.4.3 | `<p>33139</p>` | Footer — store address | 2.71:1 | Cannot read ZIP code |
| 27 | "About Us" footer link | 1.4.3 | `<a href="/pages/about-us" class="Link Link--primary">About Us</a>` | Footer — navigation links | 2.71:1 | Cannot read footer nav |
| 28 | "Shipping/Return Policy" footer link | 1.4.3 | `<a href="/pages/shipping-returns-policy" class="Link Link--primary">Shipping/Return Policy</a>` | Footer — navigation links | 2.71:1 | Cannot access policy |
| 29 | "Contact Us" footer link | 1.4.3 | `<a href="/pages/contact-us" class="Link Link--primary">Contact Us</a>` | Footer — navigation links | 2.71:1 | Cannot access contact |
| 30 | Newsletter description text in footer | 1.4.3 | `<p>Subscribe to receive updates…</p>` | Footer — newsletter signup section | 2.71:1 | Cannot read signup prompt |
| 31 | Footer newsletter "Subscribe" button | 1.4.3 | `<button type="submit" class="Form__Submit Button Button--primary">Subscribe</button>` | Footer — newsletter form | 1:1 | Subscribe button invisible |
| 32 | "ABOUT US" footer secondary nav | 1.4.3 | `<a href="/pages/about-us-2" class="Link Link--primary">ABOUT US</a>` | Footer — secondary nav column | 2.71:1 | Duplicate nav links, same contrast issue |
| 33 | "CONTACT" footer secondary nav | 1.4.3 | `<a href="/pages/contact-us" class="Link Link--primary">CONTACT</a>` | Footer — secondary nav column | 2.71:1 | Cannot read |
| 34 | "INSTAGRAM" footer secondary nav | 1.4.3 | `<a href="http://www.instagram.com/frankiemiami" class="Link Link--primary">INSTAGRAM</a>` | Footer — secondary nav column | 2.71:1 | Cannot read |
| 35 | "NEW ARRIVALS" footer secondary nav | 1.4.3 | `<a href="/collections/fall-winter" class="Link Link--primary">NEW ARRIVALS </a>` | Footer — secondary nav column | 2.71:1 | Cannot read |
| 36 | Currency selector button in footer ("USD$") | 1.4.3 | `<button class="SelectButton Link Link--primary u-h8">USD$</button>` | Footer — currency form | 2.71:1 | Cannot read |
| 37 | "Powered by Shopify" / POS credit text | 1.4.3 | `<p class="Footer__ThemeAuthor">…</p>` | Footer — attribution text | 2.71:1 | Cannot read (low priority) |
| 38 | "POS" link in attribution | 1.4.3 | `<a href="https://www.shopify.com/pos...">POS</a>` | Footer — attribution | 2.71:1 | Cannot read |
| 39 | "Ecommerce by Shopify" link | 1.4.3 | `<a href="https://www.shopify.com...">Ecommerce by Shopify</a>` | Footer — attribution | 2.71:1 | Cannot read |

**How to fix:** This is a sitewide color scheme problem. The Shopify theme uses a color palette where key text colors are insufficiently dark or are white-on-white due to a CSS conflict. The remediation approach depends on the root cause:

**Option A — Dark footer, light header (likely cause):** The footer has a dark background and the text is intended to be light. The 2.71:1 ratio suggests the footer text color is a medium gray rather than white. Change footer text from its current light gray to pure white (`#ffffff`) — that will achieve approximately 8.5:1 against a dark background.

**Option B — White elements with missing background color:** The 1:1 ratio items (header nav, site name, subscribe buttons) suggest the text color and background are the same. Check the Shopify theme's color settings in the Customizer (Online Store > Customize > Theme settings > Colors). Look for "Accent" or "Navigation" color settings that may be set to white against a white header background.

**Specific CSS targets to fix:**
- `.Heading.u-h4`, `.Heading.u-h6` — navigation and logo text
- `.ProductItem__Price.Text--subdued` — product prices
- `.Button--primary` — all primary action buttons
- `.Link--primary` — all links in header and footer
- `.Header__CartCount` — cart badge number
- `.Text--subdued` — general subdued text color

Target contrast ratios: minimum 4.5:1 for normal text, 3:1 for large text (18px+ or 14px bold+).

---

#### Serious Issues (16)

---

**Group B: SVG elements with `role="presentation"` but containing semantic child content — 16 instances**

| # | Issue | WCAG Criterion | Element | Location | Impact |
|---|---|---|---|---|---|
| 1 | Mobile hamburger menu SVG icon | 1.3.1 F92,ARIA4 | `<svg class="Icon Icon--nav" role="presentation">` | Header — mobile menu open button | `role="presentation"` removes the element from the accessibility tree, but its path children may be processed by some screen readers |
| 2 | Desktop hamburger menu SVG icon | 1.3.1 F92,ARIA4 | `<svg class="Icon Icon--nav-desktop" role="presentation">` | Header — desktop menu toggle | Same issue |
| 3 | Header search icon (mobile) | 1.3.1 F92,ARIA4 | `<svg class="Icon Icon--search" role="presentation">` | Header — search button area | Same |
| 4 | Header search icon (desktop) | 1.3.1 F92,ARIA4 | `<svg class="Icon Icon--search-desktop" role="presentation">` | Header — search button area | Same |
| 5 | Header cart icon (mobile) | 1.3.1 F92,ARIA4 | `<svg class="Icon Icon--cart" role="presentation">` | Header — cart link | Same |
| 6 | Header cart icon (desktop) | 1.3.1 F92,ARIA4 | `<svg class="Icon Icon--cart-desktop" role="presentation">` | Header — cart link | Same |
| 7 | Currency dropdown arrow SVG (header form) — first instance | 1.3.1 F92,ARIA4 | `<svg class="Icon Icon--select-arrow" role="presentation">` | Header — currency selector | Same |
| 8 | Currency dropdown arrow SVG (header form) — second instance | 1.3.1 F92,ARIA4 | `<svg class="Icon Icon--select-arrow" role="presentation">` | Header — currency selector (second occurrence) | Same |
| 9 | Product variant selector dropdown arrow — first | 1.3.1 F92,ARIA4 | `<svg class="Icon Icon--select-arrow" role="presentation">` | Featured product section — size selector | Same |
| 10 | Product variant selector dropdown arrow — second | 1.3.1 F92,ARIA4 | `<svg class="Icon Icon--select-arrow" role="presentation">` | Featured product section — color/style selector | Same |
| 11 | Product variant selector arrow (quantity area) | 1.3.1 F92,ARIA4 | `<svg class="Icon Icon--select-arrow" role="presentation">` | Featured product — quantity/options area | Same |
| 12 | Quantity decrease (minus) icon | 1.3.1 F92,ARIA4 | `<svg class="Icon Icon--minus" role="presentation">` | Featured product — quantity stepper, minus button | Same |
| 13 | Quantity increase (plus) icon | 1.3.1 F92,ARIA4 | `<svg class="Icon Icon--plus" role="presentation">` | Featured product — quantity stepper, plus button | Same |
| 14 | Newsletter popup close icon | 1.3.1 F92,ARIA4 | `<svg class="Icon Icon--close" role="presentation">` | Newsletter popup — close button | Same |
| 15 | Instagram social icon in footer | 1.3.1 F92,ARIA4 | `<svg class="Icon Icon--instagram" role="presentation">` | Footer — Instagram social link icon | Same |
| 16 | Footer currency selector dropdown arrow | 1.3.1 F92,ARIA4 | `<svg class="Icon Icon--select-arrow" role="presentation">` | Footer — currency localization form | Same |

**How to fix:** Replace `role="presentation"` with `aria-hidden="true"` on all decorative SVG icon elements. The WCAG failure here is that `role="presentation"` suppresses the element's own role but not the roles of its children, creating inconsistent behavior across screen readers. `aria-hidden="true"` removes the entire subtree (SVG + all children) from the accessibility tree, which is the correct approach for decorative icons.

Also add `focusable="false"` to prevent Internet Explorer from focusing SVGs:
```html
<!-- WRONG: -->
<svg class="Icon Icon--nav" role="presentation" viewBox="...">

<!-- CORRECT: -->
<svg class="Icon Icon--nav" aria-hidden="true" focusable="false" viewBox="...">
```

This is a theme-level fix. In Shopify, locate the icon SVG snippets (likely in `snippets/icon-nav.liquid`, `snippets/icon-cart.liquid`, etc.) and update the `role="presentation"` attribute to `aria-hidden="true"` on each. The fix may only need to be made to a handful of snippet files that are reused throughout the theme.

---

#### Moderate Issues (2)

---

**Group C: Quantity input field has no accessible name — 1 instance (flagged under 2 criteria)**

| # | Issue | WCAG Criterion | Element | Location | Impact |
|---|---|---|---|---|---|
| 1a | Quantity text input has no accessible name | 4.1.2 H91.InputText.Name | `<input type="text" class="QuantitySelector__CurrentQuantity" name="quantity" value="1">` | Featured product section — quantity stepper input | Screen reader cannot announce "Quantity" when user focuses this field |
| 1b | Same input has no label element | 1.3.1 F68 | Same element | Same location | Fails both Name/Role/Value and Info & Relationships criteria |

**How to fix:** Add a visually hidden label for the quantity field:
```html
<label for="quantity-input" class="visually-hidden">Quantity</label>
<input type="text" id="quantity-input" class="QuantitySelector__CurrentQuantity" name="quantity" value="1">
```
Or use `aria-label` directly on the input: `<input type="text" aria-label="Product quantity" name="quantity" value="1">`.

---

**Group D: Duplicate form ID — 1 instance**

| # | Issue | WCAG Criterion | Element | Location | Impact |
|---|---|---|---|---|---|
| 1 | Two `<form>` elements share the ID `localization_form_header` | 4.1.1 Parsing | `<form id="localization_form_header">` | Header — currency/language localization form (appears twice in header markup) | IDs must be unique; duplicate IDs can cause JavaScript form handling to target the wrong form and confuse screen reader form navigation |

**How to fix:** In the Shopify theme, the header localization form appears to be rendered twice (once for mobile, once for desktop). Give each form a unique ID: `id="localization_form_header_desktop"` and `id="localization_form_header_mobile"`. Update any JavaScript or CSS that references `#localization_form_header` to use the new unique IDs or a shared class selector.

---

### Remediation Roadmap

**Week 1 — Critical (Color Contrast — Sitewide):**
- Open the Shopify theme Customizer (Online Store > Customize) and navigate to Theme Settings > Colors. Review all color assignments. Look specifically for any color combination where text and background are white/near-white simultaneously.
- Use Chrome DevTools "Inspect" on the navigation links to see the computed text color and background. Fix the CSS root cause.
- Target files: `assets/theme.css` or `assets/application.css` — update the following CSS classes:
  - `.Heading`, `.u-h4`, `.u-h6` — navigation and logo
  - `.Button--primary` — all primary buttons (Add to Cart, Subscribe, View All Products)
  - `.ProductItem__Price.Text--subdued` and `.ProductMeta__Price.Text--subdued` — product prices
  - `.Link--primary` — all link elements in header and footer
  - Footer text colors (`#section-footer p`, `#section-footer a`)
- After each change, validate contrast using the WebAIM Contrast Checker.

**Week 2 — Serious (SVG Icons):**
- Locate all SVG snippet files (search the theme codebase for `role="presentation"`).
- Replace every instance with `aria-hidden="true" focusable="false"`.
- Files likely affected: `snippets/icon-nav.liquid`, `snippets/icon-cart.liquid`, `snippets/icon-search.liquid`, `snippets/icon-close.liquid`, `snippets/icon-instagram.liquid`, `snippets/icon-select-arrow.liquid`, `snippets/icon-minus.liquid`, `snippets/icon-plus.liquid`.

**Month 2 — Moderate:**
- Add a `<label>` or `aria-label="Product quantity"` to the quantity stepper input field in the featured product section.
- Fix the duplicate `localization_form_header` ID by appending `_desktop` and `_mobile` to the two form instances and updating associated JavaScript.

**Ongoing:**
- After fixing the contrast issues, re-run an automated scan to verify all 39 contrast failures are resolved.
- Audit the collection page, product detail page, and checkout — color contrast issues in the theme will manifest on all pages.
- Add `aria-hidden` as a theme standard for all future icon SVGs.

---

### Technical Summary
- **Pages scanned:** 1 (homepage — https://www.frankiemiami.com)
- **Total violations:** 58
- **All issue types:** error (58 errors, 0 warnings, 0 notices)
- **Unique violation types:** 5
- **Most common violation:** 1.4.3 Contrast Minimum — 39 instances affecting navigation, product prices, buttons, footer text, and CTAs
- **Second most common:** 1.3.1 / SVG role="presentation" with semantic children — 16 instances
- **Platform:** Shopify (Timber/Slate-based theme)
- **WCAG Principles affected:** Perceivable, Robust
- **Estimated remediation effort:** Medium (1–3 developer days: the contrast fix requires diagnosing the CSS root cause, which may be complex due to theme structure; the SVG fix is straightforward)
- **Highest risk area:** Entire color scheme — with 10 header elements invisible (1:1 contrast), the site's navigation is completely inaccessible to low-vision users. This also represents a general UX problem affecting sighted users with certain display configurations.
- **Notable finding:** A 1:1 contrast ratio (text = background color) affects the site name, all navigation links, and the primary CTA buttons. This is unusual and suggests a theme color configuration error rather than a deliberate design choice.
