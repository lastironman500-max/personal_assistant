# Website Accessibility Scan Preview
## Marcella NYC — marcellanyc.com
**Scan Date:** March 15, 2026

---

### Overall Results
- **Pages Scanned:** 1 (homepage)
- **Total Issues Found:** 62
- **Critical/Error Issues:** 62

---

### Top 3 Issues Found (Preview)

**Issue 1: 47 Duplicate ID Attributes Breaking Screen Reader Navigation**
- What's wrong: Forty-seven HTML elements share duplicate `id` values — including `item-slw`, `image-clickable`, and `image-block-link` — repeated across every product category and navigation item. Screen readers and assistive technology use IDs to jump between sections; when IDs are duplicated, navigation breaks unpredictably.
- Where: All navigation links (`#item-slw`), category image links (`#image-clickable`, `#image-block-link`) throughout the homepage product grid
- Why it matters: Users navigating the site via keyboard or switch device may land on the wrong product, skip sections entirely, or encounter infinite loops — making the shopping experience unusable.
- Legal risk: Structural HTML errors that break assistive technology navigation are a core WCAG 4.1.1 violation and increasingly cited in lawsuits against Shopify-based fashion retailers.

**Issue 2: 9 Product and Promotional Images Missing Alt Text**
- What's wrong: Nine images — including hero banner images, promotional video poster frames, and footer logos — have no `alt` attribute. Screen readers skip them entirely, leaving blind shoppers without any description of featured products or promotions.
- Where: Hero banner section, pillar section video thumbnails, cart/account icons in the checkout modal, Inc. 5000 footer logo
- Why it matters: For a fashion brand where visual presentation is central to the purchase decision, blind users cannot access information about featured items, current promotions, or brand credibility markers like the Inc. 5000 recognition.
- Legal risk: E-commerce sites with missing product image alt text are a well-documented target for ADA demand letters; New York's SDNY and EDNY courts see dozens of such filings each month.

**Issue 3: Empty CTA Link and Broken Anchor Reference**
- What's wrong: A hero banner call-to-action link (`<a href="/collections/sale">`) contains no text content, making it invisible to screen readers. Additionally, a wishlist link references an anchor (`#swym-wishlist`) that does not exist on the page.
- Where: Homepage hero banner CTA; wishlist anchor button (`#notepad-anchor-title`)
- Why it matters: A blind user trying to activate the primary promotional offer or save a wishlist item encounters silent, broken controls — core shopping actions that sighted users complete with a single click.
- Legal risk: Broken and empty interactive controls directly violate WCAG 2.4.1 and 4.1.2, and are among the clearest-cut violations to establish in an ADA complaint.

---

### What This Means for Marcella NYC
As a New York City-based fashion retailer with a Shopify storefront, Marcella NYC sits squarely in the highest-risk category for ADA website litigation. New York generates the majority of e-commerce accessibility lawsuits nationally, and fashion/apparel brands are among the most frequently named defendants. The 47 duplicate ID errors alone indicate a structural template issue that likely extends across interior pages as well.

---

*This is a preview showing 3 of 62 issues found. A full report with remediation steps for every issue is available.*


