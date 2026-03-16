# Website Accessibility Scan Preview
## YAL New York — yalnewyork.com
**Scan Date:** March 15, 2026

---

### Overall Results
- **Pages Scanned:** 1 (homepage)
- **Total Issues Found:** 132
- **Critical/Error Issues:** 132

---

### Top 3 Issues Found (Preview)

**Issue 1: Unlabeled Form Fields**
- What's wrong: The search bar and other input fields on the homepage have no accessible label — they rely solely on placeholder text, which disappears when a user starts typing and is never read aloud by screen readers.
- Where: Search input field (`input[name="search1"]`) and multiple form inputs throughout the page
- Why it matters: Blind and low-vision users relying on screen readers receive no information about what to type into these fields, making key site functions unusable.
- Legal risk: Inaccessible form inputs are among the most cited violations in ADA Title III website lawsuits filed in New York federal courts.

**Issue 2: Buttons With No Accessible Name**
- What's wrong: Seven button elements — including the main navigation toggle — have no text or aria-label, so they are completely invisible to assistive technology.
- Where: Navigation bar button (`#nav-bar-btn`) and six additional buttons across the page
- Why it matters: Keyboard and screen reader users cannot activate these buttons, locking them out of core navigation and interactive features.
- Legal risk: Non-operable interactive controls are a direct WCAG 2.1 AA violation and a primary basis for demand letters targeting retail and e-commerce sites in New York.

**Issue 3: 35 Images Missing Alt Text**
- What's wrong: Thirty-five images across the homepage have no `alt` attribute, meaning screen readers either skip them silently or read out raw filenames — both of which create a confusing and degraded experience.
- Where: Product images, promotional banners, and decorative images site-wide
- Why it matters: For a visually-driven apparel brand, images communicate product identity. Blind shoppers receive none of that information, making informed purchasing impossible.
- Legal risk: Missing image alt text is the single most common WCAG violation cited in accessibility demand letters against fashion and retail brands.

---

### What This Means for YAL New York
YAL New York operates in one of the most litigation-active states in the country — New York accounts for roughly 65% of all ADA website lawsuits filed nationally each year. As a fashion e-commerce brand, the site is a direct target: retail and apparel sites are among the top three most-sued categories. With 132 errors spanning forms, navigation, and product imagery, the exposure is broad and the fixes are well-defined.

---

*This is a preview showing 3 of 132 issues found. A full report with remediation steps for every issue is available.*

*Full Accessibility Scan Report — $299*
*Includes: All 132 issues documented, plain-English fix instructions, priority remediation roadmap, compliance scorecard*

*Reply to this email to get started.*
