# WCAG Accessibility Scan Report
## Shalman Dentistry — shalmandentistry.com
**Scan Date:** March 15, 2026
**Standard:** WCAG 2.1 Level AA
**Tool:** pa11y (htmlcs engine)

---

### Disclaimer
This report documents programmatically detectable accessibility issues found via automated scanning. Automated tools detect approximately 57% of WCAG 2.1 issues. Manual testing by an accessibility specialist is recommended for complete conformance assessment. This report does not constitute legal advice or guarantee ADA/EAA compliance.

---

### Executive Summary

Shalman Dentistry's website returned 22 accessibility violations, the second-lowest count in this audit. However, the severity of the issues is disproportionate to the count. The entire above-the-fold hero section — including the site headline "Welcome to Shalman Dentistry," the introductory paragraph about the practice, all three bullet points describing the dentist's credentials, and the "About Us" call-to-action button — has a 1:1 contrast ratio. This means the text color and background color are identical, rendering the entire hero section visually invisible to anyone relying on color contrast, including users with low vision, cataracts, or certain forms of color blindness.

The main navigation menu also fails contrast requirements entirely, with all seven navigation links ("About," "Services," "Dental Implants," "Invisalign," "Before & After," "Common Problems," "Contact") at 1:1 contrast. The practical impact is that the navigation bar may appear to users as an empty colored band with no discernible items.

Beyond contrast failures, the site has three empty anchor elements in the footer, an unlabeled Google Maps iframe, an unlabeled video iframe, and address block text in the footer that is nearly unreadable due to near-matching text and background colors. The top three priorities are: (1) fix the hero section contrast so all text is legible, (2) fix the navigation menu text contrast, and (3) address the empty/broken footer links.

---

### Compliance Scorecard

| WCAG Principle | Status | Issues |
|---|---|---|
| Perceivable (1.x) | Fail | 17 |
| Operable (2.x) | Fail | 2 |
| Understandable (3.x) | Pass | 0 |
| Robust (4.x) | Fail | 3 |

---

### Issues by Severity

#### Error Issues — 22 Total

---

**PERCEIVABLE — Color Contrast Failures: Navigation (7 issues)**

| # | Issue | WCAG Criterion | Element | Impact |
|---|---|---|---|---|
| 1 | "About" nav link has 1:1 contrast ratio — text is invisible against background | 1.4.3 Contrast (Minimum) | Main navigation "About" link | Critical — navigation is unusable |
| 2 | "Services" nav link has 1:1 contrast ratio | 1.4.3 | Main navigation "Services" link | Critical |
| 3 | "Dental Implants" nav link has 1:1 contrast ratio | 1.4.3 | Main navigation "Dental Implants" link | Critical |
| 4 | "Invisalign" nav link has 1:1 contrast ratio | 1.4.3 | Main navigation "Invisalign" link | Critical |
| 5 | "Before & After" nav link has 1:1 contrast ratio | 1.4.3 | Main navigation "Before & After" link | Critical |
| 6 | "Common Problems" nav link has 1:1 contrast ratio | 1.4.3 | Main navigation "Common Problems" link | Critical |
| 7 | "Contact" nav link has 1:1 contrast ratio | 1.4.3 | Main navigation "Contact" link | Critical |

**How to fix:** The navigation menu text color matches the menu background color exactly (1:1 ratio). In the site's CSS or theme settings, change the navigation link text color to a value with at least 4.5:1 contrast against the background. The scanner recommends `#767676` on a white background as a starting minimum; a dark color such as `#1a1a1a` or the practice's brand dark color against a light nav bar is preferable. Since all seven links share the same CSS rule, a single color change to the nav link selector will fix all seven violations.

---

**PERCEIVABLE — Color Contrast Failures: Hero Section (7 issues)**

| # | Issue | WCAG Criterion | Element | Impact |
|---|---|---|---|---|
| 8 | Hero `<h1>` "Welcome to Shalman Dentistry" heading has 1:1 contrast | 1.4.3 (G145, large text) | Page hero heading (h1) | Critical — primary page heading is invisible |
| 9 | Hero `<h1>` inner `<span>` text has 1:1 contrast | 1.4.3 | Hero heading span text | Critical |
| 10 | Hero introductory paragraph text has 1:1 contrast | 1.4.3 | Hero intro paragraph | Critical |
| 11 | Hero bullet point 1 (award-winning practice) has 1:1 contrast | 1.4.3 | Hero credentials list, item 1 | Critical |
| 12 | Hero bullet point 2 (continual learning) has 1:1 contrast | 1.4.3 | Hero credentials list, item 2 | Critical |
| 13 | Hero bullet point 3 (patient care commitment) has 1:1 contrast | 1.4.3 | Hero credentials list, item 3 | Critical |
| 14 | "About Us" hero call-to-action button text has 1:1 contrast | 1.4.3 | Hero CTA "About Us" button | Critical — primary CTA is invisible |

**How to fix:** The entire hero section's text is rendered in the same color as its background (likely white text on a white background, or dark text on dark image). Check the hero section's CSS and ensure:
- Heading text (`h1` and its `span`) uses a high-contrast color against the hero background
- Body copy and list items use at least 4.5:1 contrast
- The "About Us" button text uses at least 4.5:1 contrast against the button's background color

If the hero has a background image, add a semi-transparent dark overlay behind the text (e.g., `background: rgba(0,0,0,0.5)`) so white text achieves sufficient contrast regardless of the image content.

---

**PERCEIVABLE — Color Contrast Failures: Testimonials and Footer (3 issues)**

| # | Issue | WCAG Criterion | Element | Impact |
|---|---|---|---|---|
| 15 | Testimonial reviewer name "Ella Kotler" has 4.19:1 contrast (required: 4.5:1) | 1.4.3 | Testimonials section, reviewer name | Moderate — marginally below the 4.5:1 threshold |
| 16 | Testimonial reviewer name "Nick Miller" has 4.19:1 contrast | 1.4.3 | Testimonials section, reviewer name | Moderate |
| 17 | Footer address block text has 1.22:1 contrast (near-invisible against background) | 1.4.3 | Footer contact address | Critical — practice address is unreadable |

**How to fix (testimonial names):** The reviewer name text color (likely a teal/green brand color) is very close to meeting contrast — at 4.19:1, it needs only a small darkening. Change the text color to `#04838d` or darker to reach the 4.5:1 threshold. This is a very minor CSS adjustment.

**How to fix (footer address):** The footer address text (`<span class="village-content footer-address">`) has near-matching text and background colors at 1.22:1. Change the background or text color — the scanner suggests lightening the background to `#fdffff` or darkening the text. A practical fix is to set the address text to a dark color (e.g., `#333333`) that achieves strong contrast against whatever the footer background color is.

---

**OPERABLE — Unlabeled Iframes (2 issues)**

| # | Issue | WCAG Criterion | Element | Impact |
|---|---|---|---|---|
| 18 | Google Maps embedded iframe has no title attribute | 2.4.1 Bypass Blocks | Embedded Google Maps showing practice location | Moderate |
| 19 | Video embedded iframe has no title attribute | 2.4.1 | Embedded video iframe | Moderate |

**How to fix (Google Maps):** Add a descriptive `title` attribute to the Google Maps iframe: `<iframe src="https://www.google.com/maps/embed?..." title="Map showing Shalman Dentistry location at [address]">`. This helps screen reader users understand what the frame contains before deciding to enter it.

**How to fix (video iframe):** Add a title describing the video: `<iframe id="video-iframe" title="Shalman Dentistry — practice introduction video" ...>`. If the video is not yet loaded (the `src` attribute is empty at page load), ensure the title is set before or when the src is populated.

---

**ROBUST — Empty and Broken Links (3 issues)**

| # | Issue | WCAG Criterion | Element | Impact |
|---|---|---|---|---|
| 20 | Footer link 1 — anchor element with `href="#"` has no text content | 4.1.2 Name, Role, Value | Footer navigation link 1 | Serious — screen reader announces "link" with no destination or label |
| 21 | Footer link 2 — anchor element with `href="#"` has no text content | 4.1.2 | Footer navigation link 2 | Serious |
| 22 | Footer link 3 — anchor element with `href="#"` has no text content | 4.1.2 | Footer navigation link 3 | Serious |

**How to fix:** These three empty anchor elements (`<a href="#">`) in the footer likely represent placeholder links from a theme template that were never populated. Either:
- Remove them if they serve no purpose
- Fill them with meaningful text and a real destination URL (e.g., links to social media profiles or key site pages)
- If they are meant to be social media icons, add the icon image with descriptive alt text or an `aria-label` attribute

---

### Remediation Roadmap

**Week 1 — Critical:**
- Fix navigation menu text contrast — change all 7 nav link text colors to achieve at least 4.5:1 contrast (single CSS change covers all seven)
- Fix hero section text contrast — the heading, intro paragraph, bullet points, and "About Us" button are all invisible at 1:1; either fix the text color or add a dark overlay behind the text
- Fix footer address text contrast (1.22:1 is near-invisible)

**Week 2–3 — Serious:**
- Remove or populate the three empty `href="#"` footer links
- Add `title` attribute to the Google Maps iframe
- Add `title` attribute to the video iframe

**Month 2 — Moderate:**
- Darken the testimonial reviewer name color slightly to cross the 4.5:1 threshold (currently at 4.19:1)

---

### Technical Summary

- **Pages scanned:** 1
- **Total violations:** 22
- **Unique issue types:** 5
- **Most common issue:** 1.4.3 Color Contrast Minimum (17 instances)
- **Principles affected:** Perceivable (17), Operable (2), Robust (3)
- **Most severe pattern:** The entire navigation menu and hero section render text at 1:1 contrast — effectively invisible — meaning the primary purpose of the homepage (introducing the practice and enabling navigation) is inaccessible
