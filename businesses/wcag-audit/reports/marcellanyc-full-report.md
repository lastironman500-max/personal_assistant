# WCAG Accessibility Scan Report
## Marcella NYC — https://www.marcellanyc.com
**Scan Date:** March 15, 2026
**Standard:** WCAG 2.1 Level AA
**Tool:** pa11y (htmlcs engine)

---

### Disclaimer
This report documents programmatically detectable accessibility issues found via automated scanning. Automated tools detect approximately 57% of WCAG 2.1 issues. Manual testing by an accessibility specialist is recommended for complete conformance assessment. This report does not constitute legal advice or guarantee ADA/EAA compliance.

---

### Executive Summary

The Marcella NYC homepage was scanned and returned **62 errors** — all WCAG 2.1 Level AA violations. The site is built on Shopify, and the issue profile is strongly shaped by one systemic architectural problem: **47 elements sharing duplicate HTML IDs** (`id="item-slw"`, `id="image-clickable"`, and `id="image-block-link"`). These IDs appear to be assigned inside repeating Shopify section templates and collection grids, where the theme re-uses the same ID string for every item in a loop rather than generating unique identifiers per item.

Beyond the duplicate ID problem, there are **9 images missing alt text** (primarily video poster frames and footer/payment modal icons), **4 links with no accessible name** (social media icon links in the footer), and **1 color contrast failure** on the newsletter signup button. There is also one broken skip-link pointing to a wishlist anchor that does not exist on the page.

The overall accessibility posture of this site is **moderate**. The duplicate ID issue is the most severe in terms of volume, but it is largely a technical/structural failure that can be fixed in the Shopify theme templates — it does not individually block user interactions as severely as unlabeled forms would. The missing alt text on product-area images is the highest user-impact item. **Top 3 priorities: (1) Fix duplicate IDs in collection grid and navigation templates. (2) Add alt text to missing images. (3) Add accessible names to footer social links.**

---

### Compliance Scorecard

| WCAG Principle | Guideline | Status | Issues Found |
|---|---|---|---|
| **1 — Perceivable** | 1.1.1 Non-text Content (alt text on images) | FAIL | 9 |
| **1 — Perceivable** | 1.4.3 Contrast Minimum | FAIL | 1 |
| **2 — Operable** | 2.4.1 Bypass Blocks (broken skip link) | FAIL | 1 |
| **3 — Understandable** | (no specific failures detected) | PASS | 0 |
| **4 — Robust** | 4.1.1 Parsing (duplicate IDs) | FAIL | 47 |
| **4 — Robust** | 4.1.2 Name, Role, Value (empty links) | FAIL | 4 |

---

### Issues by Severity

#### Critical Issues (47)

---

**Group A: Duplicate HTML IDs throughout the page — 47 instances**

The Shopify theme generates repeating HTML elements in collection grids and navigation menus using static, hardcoded ID values. This means every product in a grid and every menu item in the navigation shares the same `id` attribute value as every other item of the same type.

| ID Value | Count | Location | Impact |
|---|---|---|---|
| `item-slw` | 12 | Navigation menus (desktop and mobile) — links to "NEW ARRIVALS", "BEST SELLERS", "MARCELLA ON YOU", "SHOP ALL" | IDs must be unique; duplicate IDs break `aria-labelledby`, `aria-describedby`, and anchor links. Screen readers and browsers may return only the first matching element. |
| `image-clickable` | 18 | Product/category image grid — each clickable image overlay link in the homepage collection tiles | Every "Shop Tops", "Shop Dresses", "Shop Shoes" image link shares this ID. |
| `image-block-link` | 17 | Product/category image grid — each text label link (e.g., "Tops", "Dresses", "Spring Sale") | Same as above — every text label link in the grid shares this ID. |

**Full list of `image-clickable` instances (18 links, all sharing one ID):**
1. `/collections/tops` — Tops
2. `/collections/dresses` — Dresses
3. `/collections/sale` — Spring Sale
4. `/collections/shoes` — Shoes
5. `/collections/belts` — Belts
6. `/collections/bags-and-purses` — Bags
7. `/collections/boleros` — Boleros
8. `/collections/best-of-spring` — Best Of Spring
9. `/collections/transitional-wardrobe-essentials` — Transitional Wardrobe Essentials
10. `/pages/styles` — Marcella On You (editorial page)
11. `/collections/the-white-edit` — White Edit
12. `/pages/about-us` — About Us
13. `/pages/design-philosophy` — Design Philosophy
14. `/pages/fabrics` — Fabrics
15. `/pages/sustainability-pledge` — Sustainability Pledge
16. `/collections/best-of-sale-storewide-spring-sale-2026` — Best Of Sale
17. `/collections/almost-gone-storewide-spring-sale-2026` — Almost Gone
18. `/collections/clearance-40-off-storewide-spring-sale-2026` — Deepest Discounts (Clearance)

**Full list of `item-slw` instances (12 nav links, sharing one ID):**
- Desktop nav: NEW ARRIVALS, BEST SELLERS, MARCELLA ON YOU, SHOP ALL
- Mobile nav: same 4 links duplicated

| # | Issue | WCAG Criterion | Element | Location | Impact |
|---|---|---|---|---|---|
| 1–47 | Duplicate `id` attribute values found on the web page | 4.1.1 Parsing | `id="item-slw"`, `id="image-clickable"`, `id="image-block-link"` | Navigation menus and homepage collection grid | Any `aria-labelledby`, `aria-describedby`, or in-page anchor that references these IDs will resolve to only the first match. Keyboard navigation via landmarks may malfunction. Screen reader virtual cursor behavior may be unpredictable. |

**How to fix:** In the Shopify theme's Liquid templates, update the ID attributes to include the item's unique identifier (e.g., loop index or handle):

For collection grid items, in the relevant `section.liquid` or `snippet` file, change:
```html
<!-- WRONG: -->
<a id="image-clickable" href="{{ collection.url }}">

<!-- CORRECT: -->
<a id="image-clickable-{{ collection.handle }}" href="{{ collection.url }}">
```

For navigation items:
```html
<!-- WRONG: -->
<a href="{{ link.url }}" id="item-slw">

<!-- CORRECT: -->
<a href="{{ link.url }}" id="nav-item-{{ forloop.index }}">
```

If the IDs are used in JavaScript, update the JS to use class selectors (`querySelectorAll('.image-clickable')`) instead of ID selectors (`getElementById`).

---

#### Serious Issues (13)

---

**Group B: Images missing alt text — 9 instances**

| # | Issue | WCAG Criterion | Element | Location | Impact |
|---|---|---|---|---|---|
| 1 | Hero banner video poster frame image has no alt | 1.1.1 | `<img src="...preview_images/2a7419220a2f4003873ab81ddc465921.thumbnail...">` | Hero banner section — first video poster | Screen readers encounter an unnamed image |
| 2 | Hero banner second video poster frame image has no alt | 1.1.1 | `<img src="...preview_images/2971f34cb3654dbf9e612c6a06c72242.thumbnail...">` | Hero banner section — second video poster | Screen readers encounter an unnamed image |
| 3 | Brand pillars section video poster frame has no alt | 1.1.1 | `<img src="...preview_images/b63e13102fc74820a6468e1bfb0a543c.thumbnail...">` | "Pillars" brand values section — video thumbnail | Unnamed image in brand content area |
| 4 | Shopping cart icon image in payment modal has no alt | 1.1.1 | `<img src=".../cart.svg">` in `#paymentModal` | Payment/checkout modal — cart step icon | Screen reader cannot identify this step indicator |
| 5 | Person/account icon image in payment modal has no alt | 1.1.1 | `<img src=".../person.svg">` in `#paymentModal` | Payment/checkout modal — account step icon | Screen reader cannot identify this step indicator |
| 6 | Pie chart / rewards icon in payment modal has no alt | 1.1.1 | `<img src=".../pie.svg">` in `#paymentModal` | Payment/checkout modal — rewards step icon | Screen reader cannot identify this step indicator |
| 7 | Inc. 5000 logo badge in footer (first instance) | 1.1.1 | `<img src=".../inc-5000-logo.png" width="81" height="81">` | Footer — first column, awards/badges area | Screen reader announces "image" with no description of the award |
| 8 | Inc. 5000 logo badge in footer (second instance) | 1.1.1 | `<img src=".../inc-5000-logo.png" width="81" height="81">` | Footer — fifth column, second awards area | Same as above — duplicate footer instance |
| 9 | Tracking pixel image has no alt | 1.1.1 | `<img src="https://lantern.roeye.com/track.php?fingerprint=...">` | Body — analytics tracking pixel | Should have `alt=""` to mark as decorative/functional |

**How to fix:**
- Video poster frames (items 1–3): These are decorative — the video conveys the content visually. Use `alt=""` to mark them as decorative so screen readers skip them. If the poster frame represents a meaningful visual (e.g., a model in a specific product), describe it: `alt="Model wearing Marcella summer dress in the hero banner"`.
- Payment modal icons (items 4–6): These are step indicators. Add descriptive alt text: `alt="Step 1: Shopping cart"`, `alt="Step 2: Account details"`, `alt="Step 3: Rewards"`.
- Inc. 5000 badges (items 7–8): `alt="Inc. 5000 — America's Fastest Growing Companies"`. Since it appears twice, one could be `alt=""` to avoid redundancy.
- Tracking pixel (item 9): `alt=""` — it is a 0x0 or 1x1 tracking image and carries no visual information.

---

**Group C: Empty anchor links (links with no accessible text) — 4 instances**

| # | Issue | WCAG Criterion | Element | Location | Impact |
|---|---|---|---|---|---|
| 1 | Facebook footer link contains only a hidden SVG | 4.1.2 | `<a href="https://www.facebook.com/marcellanyc/" class="social-icon"><svg aria-hidden="true">...</svg></a>` | Footer — social icons row | Screen reader announces link URL instead of "Facebook" |
| 2 | Pinterest footer link contains only a hidden SVG | 4.1.2 | `<a href="https://www.pinterest.com/marcella_nyc/" class="social-icon"><svg aria-hidden="true">...</svg></a>` | Footer — social icons row | Screen reader announces URL |
| 3 | Instagram footer link contains only a hidden SVG | 4.1.2 | `<a href="https://instagram.com/marcellanyc/" class="social-icon"><svg aria-hidden="true">...</svg></a>` | Footer — social icons row | Screen reader announces URL |
| 4 | Hero banner CTA link has no accessible text | 4.1.2 | `<a href="/collections/sale" class="bigpromo-cta-area"></a>` | Hero banner — promotional CTA overlay link | An empty link with a valid href; screen reader announces "link" with no purpose |

**How to fix:**
- Social icon links: Add `aria-label` to each anchor:
  ```html
  <a href="https://www.facebook.com/marcellanyc/" class="social-icon" aria-label="Marcella NYC on Facebook">
  <a href="https://www.pinterest.com/marcella_nyc/" class="social-icon" aria-label="Marcella NYC on Pinterest">
  <a href="https://instagram.com/marcellanyc/" class="social-icon" aria-label="Marcella NYC on Instagram">
  ```
- Hero banner CTA: Add descriptive text or an `aria-label`. If the link goes to the sale collection: `<a href="/collections/sale" class="bigpromo-cta-area" aria-label="Shop the Spring Sale collection">`.

---

**Group D: Color contrast failure — 1 instance**

| # | Issue | WCAG Criterion | Element | Location | Impact |
|---|---|---|---|---|---|
| 1 | Newsletter signup button text has a contrast ratio of 1:1 (invisible text) | 1.4.3 | `<button type="button" ... style="color: rgb(0, 0, 0); border-color: rgb(0, 0, 0); background: rgba(0,0,0,0);">` | Newsletter bar popup — subscribe button | The button text color and background color are effectively the same, making the button label invisible |

**How to fix:** The button uses a transparent background with black text (`color: rgb(0,0,0)`) and a black border — but the computed contrast is 1:1, which suggests the parent background may also be black or very dark, making the text invisible. Verify the actual rendered background and ensure the text color contrasts at 4.5:1 against it. If the background is black, change the button text to white: `color: #ffffff`. If the background is white, the black text is fine — but then the contrast scanner result suggests there's a background overlay obscuring this. Inspect in-browser to confirm the actual rendered state.

---

#### Moderate Issues (1)

---

**Group E: Broken skip link / anchor — 1 instance**

| # | Issue | WCAG Criterion | Element | Location | Impact |
|---|---|---|---|---|---|
| 1 | Skip link points to `#swym-wishlist` anchor that does not exist on the page | 2.4.1 G1,G123,G124.NoSuchID | `<a href="#swym-wishlist" class="swym-background-color" id="notepad-anchor-title" aria-label="My Wishlist">` | Page — Swym wishlist button in header area | The link claims to navigate to the wishlist panel but the target anchor is missing; keyboard users relying on this link to skip to wishlist content will find it broken |

**How to fix:** Ensure the wishlist panel or container has the ID `swym-wishlist` in the HTML: `<div id="swym-wishlist" ...>`. If the Swym app dynamically loads this, it may not be present on initial page load. In that case, either remove the anchor link until the panel loads, or use JavaScript to update the `href` once the wishlist widget initializes.

---

### Remediation Roadmap

**Week 1 — Critical (Duplicate IDs):**
- Open the Shopify theme code editor. Locate the Liquid templates responsible for collection grids (likely in `sections/` or `snippets/` files — look for templates generating `id="image-clickable"` and `id="image-block-link"`). Replace static IDs with dynamic IDs using `{{ forloop.index }}` or `{{ collection.handle }}`.
- Locate the navigation Liquid template generating `id="item-slw"`. Replace with `id="nav-item-{{ forloop.index }}"`. Update any CSS/JS that depends on `#item-slw`.
- This is a one-time theme fix that will resolve 47 of the 62 issues.

**Week 2 — Serious (Images & Links):**
- Add alt text to all 9 images: video poster frames (use `alt=""`), payment modal step icons (use descriptive labels), Inc. 5000 badge (use `alt="Inc. 5000 — America's Fastest Growing Companies"`), tracking pixel (use `alt=""`).
- Add `aria-label` attributes to the 3 footer social icon links (Facebook, Pinterest, Instagram).
- Add `aria-label="Shop the Spring Sale"` (or appropriate text) to the empty hero banner CTA link.

**Month 2 — Moderate & Minor:**
- Fix the newsletter button contrast issue — inspect the rendered button in a browser and ensure text color achieves 4.5:1 against its actual background.
- Investigate and fix the broken `#swym-wishlist` anchor. Check with Swym support if needed.

**Ongoing:**
- Audit additional pages (product detail pages, collection pages, checkout) — duplicate ID patterns in Liquid templates will likely manifest on other pages too.
- Establish a policy requiring alt text for all images uploaded through the Shopify admin media library.

---

### Technical Summary
- **Pages scanned:** 1 (homepage — https://www.marcellanyc.com)
- **Total violations:** 62
- **All issue types:** error (62 errors, 0 warnings, 0 notices)
- **Unique violation types:** 6
- **Most common violation:** 4.1.1 Parsing — duplicate `id` attribute values (47 instances, 3 distinct ID values repeated across navigation and collection grid templates)
- **Second most common:** 1.1.1 Non-text Content — missing alt text on images (9 instances)
- **Platform:** Shopify (custom/third-party theme with Liquid templating)
- **WCAG Principles affected:** Perceivable, Operable, Robust
- **Estimated remediation effort:** Low-to-medium (1–2 developer days; the duplicate ID fix is surgical but requires Shopify theme editing; image alt text is content work)
- **Highest risk area:** Duplicate IDs in Liquid templates — will propagate to all pages using the same collection grid section
