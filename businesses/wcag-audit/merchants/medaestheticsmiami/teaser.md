# Website Accessibility Scan Preview
## Med Aesthetics Miami — medaestheticsmiami.com
**Scan Date:** March 15, 2026

---

### Overall Results
- **Pages Scanned:** 1 (homepage)
- **Total Issues Found:** 105
- **Critical/Error Issues:** 105

---

### Top 3 Issues Found (Preview)

**Issue 1: 27 Links With No Accessible Text**
- What's wrong: Twenty-seven anchor elements — including social media links for Facebook, Instagram, Pinterest, and YouTube — contain only icon images with `aria-hidden="true"`, meaning there is zero text available to a screen reader. The links exist but are effectively invisible to assistive technology.
- Where: Social media icon links in the sidebar and footer (`#eltd_social_icon_widget-17` and similar)
- Why it matters: Blind users navigating via keyboard or screen reader encounter these links but cannot determine where they lead, turning routine site navigation into a dead end.
- Legal risk: Inaccessible social and navigation links are a textbook ADA violation frequently cited in demand letters targeting healthcare and medical spa websites in Florida.

**Issue 2: Unlabeled Form Fields on the Contact/Booking Form**
- What's wrong: Eight text inputs, email fields, and other form controls — including those on the appointment/contact form — have no accessible label, relying only on placeholder text that disappears on focus.
- Where: Search field (`input[name="s"]`), email input on the contact form, and other booking-related inputs
- Why it matters: A potential patient or client who is blind cannot reliably fill out a booking form, effectively denying them access to services that sighted users can access without friction.
- Legal risk: Medical and aesthetic service providers are under heightened scrutiny because appointment booking is considered a core service; inaccessible booking flows are a well-established basis for ADA complaints.

**Issue 3: Low-Contrast Text Across the Site**
- What's wrong: Eighteen text elements fail the WCAG minimum contrast requirement of 4.5:1, including navigation elements and body copy. The actual contrast ratios recorded are as low as 1:1 — meaning text is effectively invisible against its background.
- Where: Navigation links, body text, and promotional copy throughout the homepage
- Why it matters: Users with low vision, color blindness, or age-related vision loss cannot read key content, including service descriptions and calls to action.
- Legal risk: Contrast failures affect a large segment of the population (an estimated 8 million Americans have some form of color vision deficiency) and are among the most straightforward violations to prove in court.

---

### What This Means for Med Aesthetics Miami
Florida ranks second nationally for ADA website lawsuits, and Miami-based businesses appear frequently in the case dockets. Medical aesthetics and wellness practices are an increasingly targeted sector because their services — consultations, bookings, treatment information — are classified as places of public accommodation. With 105 errors spanning links, forms, and contrast, medaestheticsmiami.com presents a meaningful and easily documented compliance gap.

---

*This is a preview showing 3 of 105 issues found. A full report with remediation steps for every issue is available.*


