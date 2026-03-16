# Website Accessibility Scan Preview
## Frankie Miami — frankiemiami.com
**Scan Date:** March 15, 2026

---

### Overall Results
- **Pages Scanned:** 1 (homepage)
- **Total Issues Found:** 58
- **Critical/Error Issues:** 58

---

### Top 3 Issues Found (Preview)

**Issue 1: Navigation and Header Text Invisible to Screen Readers (1:1 Contrast)**
- What's wrong: Every primary navigation link — "ABOUT US," "CONTACT," "INSTAGRAM," "NEW ARRIVALS" — and the brand name "frankie." in the header all fail contrast at a ratio of 1:1, meaning the text color matches the background color exactly. These elements are visually styled (likely white on white or black on black during certain scroll states) and completely unreadable without CSS.
- Where: Main header navigation (`#section-header > div > div:nth-child(1) > nav > ul > li > a`) and brand logo text
- Why it matters: A user with low vision, or any user who browses with custom stylesheets or high-contrast mode, finds the entire site navigation invisible — effectively locking them out of every page.
- Legal risk: Navigation inaccessibility is among the most cited deficiencies in ADA website lawsuits against fashion boutiques in Florida, particularly for Shopify-hosted stores.

**Issue 2: Product Prices Unreadable — Insufficient Contrast on All Price Labels**
- What's wrong: Every product price displayed on the homepage ($220, $180, $230, $360, etc.) renders at a contrast ratio of 2.71:1 — well below the 4.5:1 minimum. The "Add to cart" button text also fails at 2.71:1.
- Where: Product grid pricing (`#block-b83f7ebb-49a4-4442-93dd-2b0f93846630`), featured product price, and "Add to cart" button
- Why it matters: Low-vision shoppers cannot read product prices or confirm the cart action — two of the most fundamental pieces of information in an e-commerce transaction. This effectively bars a segment of users from completing a purchase.
- Legal risk: Inaccessible pricing information in an online store has been successfully argued as a denial of equal goods and services under Title III, especially when it affects the purchase flow.

**Issue 3: 16 SVG Icons Marked as Presentational but Containing Semantic Children**
- What's wrong: Sixteen SVG icons — including the cart icon, search icon, hamburger menu icon, and social media icon — are marked with `role="presentation"`, telling assistive technology to ignore them. However, they contain child elements with semantic meaning (paths, groups), violating WCAG 1.3.1.
- Where: Header cart icon, search icon, hamburger menu button, Instagram icon in footer (`#section-header`, `#section-footer`)
- Why it matters: Screen reader users who expect to hear "Cart (0 items)" or "Search" when navigating the header instead encounter silence — the most critical interactive elements on the page are functionally hidden.
- Legal risk: Improperly hidden interactive controls are a structural WCAG failure that courts have accepted as clear evidence of non-compliance in retail ADA cases.

---

### What This Means for Frankie Miami
Frankie Miami is a Miami Beach boutique selling premium fashion ($180–$495 price points) — a profile that fits the typical plaintiff attorney target precisely: a desirable brand, online sales capability, and a site that systematically excludes users with disabilities. Florida is the second-most active state for ADA website litigation, and Miami Beach businesses appear regularly in the Southern District of Florida case dockets. The widespread contrast failures affect not just aesthetics but core commerce functionality.

---

*This is a preview showing 3 of 58 issues found. A full report with remediation steps for every issue is available.*

*Full Accessibility Scan Report — $299*
*Includes: All 58 issues documented, plain-English fix instructions, priority remediation roadmap, compliance scorecard*

*Reply to this email to get started.*
