# WCAG Accessibility Scan Report
## NYC Restaurant Group (NYCRG) — nycrg.com
**Scan Date:** March 15, 2026
**Standard:** WCAG 2.1 Level AA
**Tool:** pa11y (htmlcs engine)

---

### Disclaimer
This report documents programmatically detectable accessibility issues found via automated scanning. Automated tools detect approximately 57% of WCAG 2.1 issues. Manual testing by an accessibility specialist is recommended for complete conformance assessment. This report does not constitute legal advice or guarantee ADA/EAA compliance.

---

### Note on the Site's Own Accessibility Acknowledgment
NYCRG's website contains a self-disclosure acknowledging that its accessibility is "a work in progress." This is a good-faith statement, but it does not confer legal protection under the ADA or provide relief from a claim of inaccessibility. Documenting an intent to improve accessibility — without a published remediation timeline and measurable progress — is insufficient. The issues found in this scan are concrete and fixable; the remediation roadmap below provides a clear path to meaningful improvement.

---

### Executive Summary

NYCRG returned 14 accessibility violations — the fewest of the five businesses audited — making it the site closest to baseline compliance. However, the nature of the issues is significant: multiple elements have duplicate IDs, which is a foundational HTML validity problem that causes assistive technologies to behave unpredictably when users interact with the reservations flow and email signup forms. The reservations and email signup buttons — the site's two most important conversion points — each appear twice in the DOM with duplicate IDs, meaning a screen reader or browser traversing the page by ID will reference the wrong element.

Additionally, an ARIA misuse issue — a `role="presentation"` applied to a list containing meaningful slide content — actively strips semantic information away from the image gallery carousel, preventing screen readers from knowing the gallery is a navigable list of items. The reCAPTCHA hidden textarea, an unlabeled iframe, and duplicate form error message IDs round out the violations.

The site's self-reported "work in progress" status is a good starting point, but the current violations directly impair users who rely on assistive technology to make a reservation — the site's core conversion goal. Top priorities are: (1) fix all duplicate IDs across the reservations and email signup buttons and form error messages, (2) remove the `role="presentation"` from the gallery carousel list, and (3) address the reCAPTCHA textarea label.

---

### Compliance Scorecard

| WCAG Principle | Status | Issues |
|---|---|---|
| Perceivable (1.x) | Fail | 3 |
| Operable (2.x) | Fail | 1 |
| Understandable (3.x) | Pass | 0 |
| Robust (4.x) | Fail | 10 |

---

### Issues by Severity

#### Error Issues — 14 Total

---

**ROBUST — Duplicate ID Attributes (9 issues)**

| # | Issue | WCAG Criterion | Element | Impact |
|---|---|---|---|---|
| 1 | `id="reservations-button"` is used on two separate elements — the sticky nav "Make a Reservation" button and the in-page CTA button | 4.1.1 Parsing | Reservations CTA buttons (nav and in-page) | Critical — assistive technologies cannot distinguish between the two reservation buttons |
| 2 | `id="reservations-button"` duplicate — second instance | 4.1.1 | In-page reservations button | Critical |
| 3 | `id="email-signup-button"` is used on two separate elements — the sticky nav email signup and the callout section email signup | 4.1.1 | Email signup buttons (nav and callout) | Critical — same problem as reservations button |
| 4 | `id="email-signup-button"` duplicate — second instance | 4.1.1 | Callout email signup button | Critical |
| 5 | `id="email-error"` is used on two separate inline error message elements in the newsletter signup form | 4.1.1 | Email validation error message | Serious — if JavaScript uses `getElementById` to show/hide this error, only one of the two will respond |
| 6 | `id="email-error"` duplicate — second instance | 4.1.1 | Email validation error message (duplicate) | Serious |
| 7 | `id="firstname-error"` is duplicated in the reservations form | 4.1.1 | First name validation error message | Serious |
| 8 | `id="lastname-error"` is duplicated in the reservations form | 4.1.1 | Last name validation error message | Serious |
| 9 | `id="phonenumber-error"` is duplicated in the reservations form | 4.1.1 | Phone number validation error message | Serious |

**How to fix (button IDs):** The reservations button and email signup button each appear to be rendered in two locations — likely a sticky/floating navigation bar and a main content section. Give each instance a unique ID:
- Sticky nav reservations button: `id="reservations-button-nav"`
- In-page reservations CTA: `id="reservations-button-main"`
- Sticky nav email signup: `id="email-signup-button-nav"`
- Callout email signup: `id="email-signup-button-main"`

Update any JavaScript or CSS selectors that reference these IDs to use the new names. If the buttons are generated by a reservation widget (e.g., BentoBox or similar), contact the vendor to request unique ID generation for multiple button instances.

**How to fix (form error message IDs):** If the reservations form and email signup form both share error message elements with the same IDs, it suggests the same form component is being rendered twice on the page. Each instance should generate unique IDs, typically by appending a form instance number: `id="email-error-1"`, `id="email-error-2"`, etc. If these forms are managed by a third-party booking or CRM widget, report this as a bug to the vendor.

---

**ROBUST — Unlabeled Form Field (2 issues)**

| # | Issue | WCAG Criterion | Element | Impact |
|---|---|---|---|---|
| 10 | The reCAPTCHA hidden textarea has no accessible name | 4.1.2 Name, Role, Value | reCAPTCHA response textarea (hidden) | Serious — screen readers will announce this field without any label |
| 11 | The reCAPTCHA hidden textarea is not labeled via any mechanism | 1.3.1 Info and Relationships | reCAPTCHA response textarea | Serious |

**How to fix:** This hidden textarea is injected by Google's reCAPTCHA v2 script and is not meant to be visible or directly interacted with by users. Add `aria-hidden="true"` to the element so screen readers skip it entirely. This can be done via JavaScript after the reCAPTCHA widget loads: `document.getElementById('g-recaptcha-response-100000').setAttribute('aria-hidden', 'true')`. Add this to your site's JavaScript bundle or an inline script at the bottom of the page.

---

**OPERABLE — Unlabeled Iframe (1 issue)**

| # | Issue | WCAG Criterion | Element | Impact |
|---|---|---|---|---|
| 12 | A hidden iframe near the bottom of the page has no title attribute | 2.4.1 Bypass Blocks | Hidden iframe (likely reCAPTCHA or tracking) | Moderate |

**How to fix:** Add a `title` attribute to the iframe. If it is a utility frame with no user-facing content, use `title="reCAPTCHA security frame"` and add `aria-hidden="true"`. If it is a tracking or analytics iframe, use `title="Analytics frame"` and `aria-hidden="true"`.

---

**PERCEIVABLE — ARIA Misuse in Gallery (2 issues)**

| # | Issue | WCAG Criterion | Element | Impact |
|---|---|---|---|---|
| 13 | The gallery image carousel `<ul>` has `role="presentation"` but contains list items with meaningful semantic content (images, captions) | 1.3.1 Info and Relationships | Image gallery carousel list | Serious — screen readers are told the list is decorative, but its contents are navigable content |
| 14 | A gallery carousel `<li>` slide item also has `role="presentation"`, stripping its list item semantics while it contains an active, visible content panel | 1.3.1 | Gallery carousel active slide | Serious |

**How to fix:** The `role="presentation"` attribute is being used incorrectly here. It is intended for elements that exist purely for visual layout with no meaningful structure (like a table used for layout). A gallery carousel with navigable slides is not presentational — each slide is a meaningful item.

Remove `role="presentation"` from both the `<ul class="slick-track">` and the individual `<li class="slick-slide">` elements. If the Slick carousel library is adding these attributes automatically, check the Slick configuration options for `accessibility: true` (which should be the default) and ensure it is not being overridden. The Slick carousel library has built-in accessibility support when configured correctly.

Additionally, since the `<li>` has `aria-hidden="false"` (correct for the active slide), removing the `role="presentation"` will allow screen readers to properly navigate the gallery using list navigation commands.

---

### Remediation Roadmap

**Week 1 — Critical:**
- Fix all duplicate IDs on the reservations and email signup buttons — contact your BentoBox (or equivalent) platform vendor to request unique ID generation when the same widget is rendered multiple times on a page; in the meantime, apply a JavaScript post-render patch to rename duplicate IDs
- Fix duplicate form error message IDs (`email-error`, `firstname-error`, `lastname-error`, `phonenumber-error`) — same vendor escalation or JS patch approach

**Week 2–3 — Serious:**
- Remove `role="presentation"` from the image gallery carousel `<ul>` and active `<li>` elements
- Add `aria-hidden="true"` to the reCAPTCHA hidden textarea
- Add `title` attribute to the hidden iframe

**Month 2 — Ongoing:**
- Conduct manual accessibility testing of the full reservation flow, as duplicate IDs may be masking additional issues that automated tools cannot detect
- Publish a concrete accessibility improvement timeline on the site's accessibility statement page, replacing the general "work in progress" language with specific milestones

---

### Technical Summary

- **Pages scanned:** 1
- **Total violations:** 14
- **Unique issue types:** 5
- **Most common issue:** 4.1.1 Parsing — duplicate ID attributes (9 instances)
- **Principles affected:** Perceivable (3), Operable (1), Robust (10)
- **Site context:** NYCRG acknowledges accessibility is "a work in progress." The duplicate ID issues concentrated in the reservations widget suggest a third-party platform component is the root cause and should be escalated to the vendor as a bug report
