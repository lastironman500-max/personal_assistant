# WCAG Accessibility Scan Report
## Saved by the Dress — savedbythedress.com
**Scan Date:** March 15, 2026
**Standard:** WCAG 2.1 Level AA
**Tool:** pa11y (htmlcs engine)

---

### Disclaimer
This report documents programmatically detectable accessibility issues found via automated scanning. Automated tools detect approximately 57% of WCAG 2.1 issues. Manual testing by an accessibility specialist is recommended for complete conformance assessment. This report does not constitute legal advice or guarantee ADA/EAA compliance.

---

### Executive Summary

Saved by the Dress returned 25 accessibility violations, placing it in the middle of the five businesses audited. The site's issues are dominated by a single, concentrated problem: 17 product card "crossed-out price" images in the featured collection section are missing alt attributes entirely. These images visually indicate that items are on sale (a strikethrough overlay on the original price), but without alt text, screen reader users have no way to know a price has been struck through or that a sale is in progress. This is a meaningful loss of shopping information.

Beyond the product images, the site has four social media footer icons that function as links but carry no accessible name — a Facebook, Instagram, TikTok, and Pinterest icon link that screen readers cannot describe. Two localization forms (for selecting country/language in the toolbar and footer) lack submit buttons, which means keyboard-only users may be unable to apply localization changes. A PayPal analytics iframe and a tooltip close button round out the issue list.

The top three priorities are: (1) add `alt=""` (empty alt for decorative) or descriptive alt text to all 17 sale overlay images, (2) add `aria-label` attributes to the four social media footer links, and (3) add a submit button to both localization forms so keyboard users can submit country/language selections.

---

### Compliance Scorecard

| WCAG Principle | Status | Issues |
|---|---|---|
| Perceivable (1.x) | Fail | 21 |
| Operable (2.x) | Fail | 1 |
| Understandable (3.x) | Fail | 2 |
| Robust (4.x) | Fail | 1 |

---

### Issues by Severity

#### Error Issues — 25 Total

---

**PERCEIVABLE — Missing Alt Text on Product Sale Images (17 issues)**

| # | Issue | WCAG Criterion | Element | Impact |
|---|---|---|---|---|
| 1 | Product card 1, sale overlay image 1 — "crossed-out" price indicator missing alt text | 1.1.1 Non-text Content | Sale price strikethrough overlay, product 1 | Serious — sale status not communicated to screen reader users |
| 2 | Product card 1, sale overlay image 2 — missing alt text | 1.1.1 | Sale price strikethrough overlay, product 1 | Serious |
| 3 | Product card 1, sale overlay image 3 — missing alt text | 1.1.1 | Sale price strikethrough overlay, product 1 | Serious |
| 4 | Product card 2, sale overlay image 1 — missing alt text | 1.1.1 | Sale price strikethrough overlay, product 2 | Serious |
| 5 | Product card 2, sale overlay image 2 — missing alt text | 1.1.1 | Sale price strikethrough overlay, product 2 | Serious |
| 6 | Product card 2, sale overlay image 3 — missing alt text | 1.1.1 | Sale price strikethrough overlay, product 2 | Serious |
| 7 | Product card 3, sale overlay image 1 — missing alt text | 1.1.1 | Sale price strikethrough overlay, product 3 | Serious |
| 8 | Product card 3, sale overlay image 2 — missing alt text | 1.1.1 | Sale price strikethrough overlay, product 3 | Serious |
| 9 | Product card 3, sale overlay image 3 — missing alt text | 1.1.1 | Sale price strikethrough overlay, product 3 | Serious |
| 10 | Product card 4, sale overlay image 1 — missing alt text | 1.1.1 | Sale price strikethrough overlay, product 4 | Serious |
| 11 | Product card 4, sale overlay image 2 — missing alt text | 1.1.1 | Sale price strikethrough overlay, product 4 | Serious |
| 12 | Product card 4, sale overlay image 3 — missing alt text | 1.1.1 | Sale price strikethrough overlay, product 4 | Serious |
| 13 | Product card 4, sale overlay image 4 — missing alt text | 1.1.1 | Sale price strikethrough overlay, product 4 | Serious |
| 14 | Product card 5, sale overlay image 1 — missing alt text | 1.1.1 | Sale price strikethrough overlay, product 5 | Serious |
| 15 | Product card 5, sale overlay image 2 — missing alt text | 1.1.1 | Sale price strikethrough overlay, product 5 | Serious |
| 16 | Product card 5, sale overlay image 3 — missing alt text | 1.1.1 | Sale price strikethrough overlay, product 5 | Serious |
| 17 | Instagram footer link image missing alt text describing the link destination | 1.1.1 / 1.3.1 | Footer Instagram icon image used as link | Serious |

**Note on the sale overlay images:** All 17 missing-alt images are the same file (`cross-out.png`) — a strikethrough graphic used to visually indicate an item is on sale at a reduced price. The violation repeats once per sale badge per product, and multiple badges can appear on a single product card.

**How to fix (sale overlay images):** The `cross-out.png` image is purely decorative in the sense that the sale information should already be communicated textually (via price comparison numbers). If the original price and sale price are both displayed as text nearby, add `alt=""` to make the strikethrough image decorative: `<img class="crossed-out" src="cross-out.png" alt="">`. This tells screen readers to skip the image. If the sale badge is the *only* indicator of a sale (no text comparison), use `alt="Sale"` or `alt="On sale"` instead.

---

**PERCEIVABLE — Social Link Images Without Alt Text (3 issues)**

| # | Issue | WCAG Criterion | Element | Impact |
|---|---|---|---|---|
| 18 | Footer Instagram social link — image has no alt text describing the link | 1.1.1 / 1.3.1 | Footer Instagram link | Serious |
| 19 | Footer Facebook social link — image has no alt text describing the link | 1.1.1 / 1.3.1 | Footer Facebook link | Serious |
| 20 | Footer TikTok social link — image has no alt text describing the link | 1.1.1 / 1.3.1 | Footer TikTok link | Serious |
| 21 | Footer Pinterest social link — image has no alt text describing the link | 1.1.1 / 1.3.1 | Footer Pinterest link | Serious |

**How to fix:** For each social media link in the footer, add descriptive alt text to the image that conveys the link destination. Examples:
- Instagram link: `<img src="..." alt="Follow Saved by the Dress on Instagram">`
- Facebook link: `<img src="..." alt="Follow Saved by the Dress on Facebook">`
- TikTok link: `<img src="..." alt="Follow Saved by the Dress on TikTok">`
- Pinterest link: `<img src="..." alt="Follow Saved by the Dress on Pinterest">`

---

**UNDERSTANDABLE — Forms Without Submit Buttons (2 issues)**

| # | Issue | WCAG Criterion | Element | Impact |
|---|---|---|---|---|
| 22 | The toolbar localization form (country/currency selector) has no submit button | 3.2.2 On Input | Localization dropdown in toolbar | Serious — keyboard users cannot submit the form |
| 23 | The footer localization form (country/currency selector) has no submit button | 3.2.2 | Localization dropdown in footer | Serious |

**How to fix:** Both localization forms currently use JavaScript to auto-submit when a select element changes, but they have no fallback submit button for keyboard users or those with JavaScript disabled. Add a visually styled submit button to each form. If you want it to appear only when JavaScript is unavailable, you can hide it via CSS and show it conditionally. At minimum, add: `<button type="submit">Apply</button>` (or `Update country`) inside each `<form>` element. This is a Shopify localization form and may require editing the `localization.liquid` or equivalent template snippet.

---

**OPERABLE — Unlabeled Iframe (1 issue)**

| # | Issue | WCAG Criterion | Element | Impact |
|---|---|---|---|---|
| 24 | PayPal analytics/offers iframe has no title attribute | 2.4.1 Bypass Blocks | PayPal embedded iframe (analytics) | Moderate |

**How to fix:** This iframe is injected by the PayPal script embedded in the page. If you have access to configure it, add `title="PayPal payment options"`. If the iframe is purely for analytics and carries no user-visible content, add both `title="PayPal analytics"` and `aria-hidden="true"` to remove it from the accessibility tree.

---

**ROBUST — Unlabeled Interactive Element (1 issue)**

| # | Issue | WCAG Criterion | Element | Impact |
|---|---|---|---|---|
| 25 | A tooltip close button has no accessible name (contains only a hidden SVG icon) | 4.1.2 Name, Role, Value | Tooltip dismiss button | Serious — screen reader users cannot identify or activate the close button |

**How to fix:** Add an `aria-label` to the tooltip close button: `<button class="tool-tip__close" aria-label="Close tooltip" data-tool-tip-close="">`. The SVG inside already has `aria-hidden="true"` and `focusable="false"`, so the button itself needs a text alternative.

**Also note:** The footer "Back to top" anchor (`<a title="Back to top">`) has no `href` attribute and no link content. This means it is not keyboard-focusable and has no accessible name beyond the `title` attribute (which is unreliable). Convert it to a `<button>` element with `aria-label="Back to top"`, or ensure the `<a>` has both an `href` attribute (e.g., `href="#top"`) and visible or ARIA label text.

---

### Remediation Roadmap

**Week 1 — Critical:**
- Add `alt=""` (decorative) or `alt="Sale"` to all 17 `crossed-out.png` sale badge images — this single template change resolves 17 of the 25 violations
- Add `aria-label` or image alt text to all four footer social links (Instagram, Facebook, TikTok, Pinterest)
- Add `aria-label="Close tooltip"` to the tooltip close button

**Week 2–3 — Serious:**
- Add a submit button to both localization forms (toolbar and footer) so keyboard users can apply country/language changes
- Fix the "Back to top" footer anchor — convert to a `<button>` or add `href="#top"` and a label

**Month 2 — Moderate:**
- Add `title="PayPal payment options"` to the PayPal analytics iframe

---

### Technical Summary

- **Pages scanned:** 1
- **Total violations:** 25
- **Unique issue types:** 6
- **Most common issue:** 1.1.1 Non-text Content — missing alt attributes (20 instances)
- **Principles affected:** Perceivable (21), Operable (1), Understandable (2), Robust (1)
- **Root cause concentration:** 17 of 25 violations are the same `cross-out.png` sale badge image repeated across product cards — a one-line template fix resolves them all
