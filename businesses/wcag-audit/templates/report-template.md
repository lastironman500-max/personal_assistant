# WCAG Accessibility Scan Report Template

> This template is populated by the Writer Agent (Claude) for each client scan.
> Placeholders are marked with `{{VARIABLE_NAME}}`.

---

```
================================================================================
                    AUTOMATED WCAG ACCESSIBILITY SCAN REPORT
================================================================================

Prepared for:    {{CLIENT_COMPANY_NAME}}
Website:         {{CLIENT_WEBSITE_URL}}
Scan Date:       {{SCAN_DATE}}
Report ID:       {{REPORT_ID}}
Prepared by:     {{BRAND_NAME}}

Scan Scope:      {{PAGES_SCANNED}} pages | WCAG 2.2 Level AA
Standard:        WCAG 2.1 / 2.2 Level AA (ADA Title III benchmark)
Scanner:         axe-core (industry standard, used by Google, Microsoft, BBC)
AI Analysis:     Claude — plain-English interpretation + remediation guidance

================================================================================
```

---

## IMPORTANT DISCLAIMER

**This report is an automated accessibility scan, not a full manual audit or legal compliance certification.**

This automated analysis detects approximately 57% of potential WCAG 2.1 issues using axe-core, the industry-standard accessibility testing engine. The remaining 43% of potential issues — including screen reader reading order, cognitive accessibility, focus trap detection, meaningful alt text quality, and custom widget behavior — require manual testing with assistive technologies.

This report:
- IS a technical scan identifying programmatically-detectable accessibility barriers
- IS NOT a legal opinion, compliance certification, or guarantee of ADA/Section 508/EAA conformance
- IS NOT a substitute for manual testing by accessibility experts
- IS NOT a guarantee against legal action

The findings should be used as a starting point for accessibility remediation. We recommend a manual expert audit for complete WCAG conformance assessment.

AI (Claude by Anthropic) was used to generate the narrative descriptions, remediation guidance, and priority assessments in this report.

---

## 1. Executive Summary

### Overall Compliance Posture

```
Overall Compliance Score:        {{COMPLIANCE_SCORE}} / 100
WCAG 2.1 Level AA Status:       {{CONFORMANCE_STATUS}}
Pages Scanned:                   {{PAGES_SCANNED}}
Total Violations Found:          {{TOTAL_VIOLATIONS}}
  Critical:                      {{CRITICAL_COUNT}}
  Serious:                       {{SERIOUS_COUNT}}
  Moderate:                      {{MODERATE_COUNT}}
  Minor:                         {{MINOR_COUNT}}
Needs Manual Review:             {{INCOMPLETE_COUNT}} items
Scan Duration:                   {{SCAN_DURATION}}
```

### Risk Assessment

**Risk Level: {{RISK_LEVEL}}**

{{RISK_NARRATIVE}}

> Based on current ADA lawsuit trends (4,500+ federal suits projected for 2025, 77% targeting ecommerce), websites with {{CRITICAL_COUNT}} critical violations are in the highest-risk category for demand letters and litigation. The average ADA web settlement ranges from $25,000-$75,000 plus $15,000-$50,000 in legal fees.

### Top 3 Issues Requiring Immediate Action

1. **[{{ISSUE_1_SEVERITY}}] {{ISSUE_1_NAME}}** — {{ISSUE_1_SUMMARY}} (affects {{ISSUE_1_PAGES}} pages)
2. **[{{ISSUE_2_SEVERITY}}] {{ISSUE_2_NAME}}** — {{ISSUE_2_SUMMARY}} (affects {{ISSUE_2_PAGES}} pages)
3. **[{{ISSUE_3_SEVERITY}}] {{ISSUE_3_NAME}}** — {{ISSUE_3_SUMMARY}} (affects {{ISSUE_3_PAGES}} pages)

---

## 2. Compliance Scorecard

### WCAG 2.1 Criterion-by-Criterion Status

| Criterion | Description | Level | Status | Violations |
|-----------|-------------|-------|--------|------------|
| 1.1.1 | Non-text Content | A | {{STATUS_1_1_1}} | {{COUNT_1_1_1}} |
| 1.2.1 | Audio-only and Video-only | A | {{STATUS_1_2_1}} | {{COUNT_1_2_1}} |
| 1.2.2 | Captions (Prerecorded) | A | {{STATUS_1_2_2}} | {{COUNT_1_2_2}} |
| 1.2.3 | Audio Description or Media Alternative | A | {{STATUS_1_2_3}} | {{COUNT_1_2_3}} |
| 1.3.1 | Info and Relationships | A | {{STATUS_1_3_1}} | {{COUNT_1_3_1}} |
| 1.3.2 | Meaningful Sequence | A | {{STATUS_1_3_2}} | {{COUNT_1_3_2}} |
| 1.3.3 | Sensory Characteristics | A | {{STATUS_1_3_3}} | {{COUNT_1_3_3}} |
| 1.3.4 | Orientation | AA | {{STATUS_1_3_4}} | {{COUNT_1_3_4}} |
| 1.3.5 | Identify Input Purpose | AA | {{STATUS_1_3_5}} | {{COUNT_1_3_5}} |
| 1.4.1 | Use of Color | A | {{STATUS_1_4_1}} | {{COUNT_1_4_1}} |
| 1.4.2 | Audio Control | A | {{STATUS_1_4_2}} | {{COUNT_1_4_2}} |
| 1.4.3 | Contrast (Minimum) | AA | {{STATUS_1_4_3}} | {{COUNT_1_4_3}} |
| 1.4.4 | Resize Text | AA | {{STATUS_1_4_4}} | {{COUNT_1_4_4}} |
| 1.4.5 | Images of Text | AA | {{STATUS_1_4_5}} | {{COUNT_1_4_5}} |
| 1.4.10 | Reflow | AA | {{STATUS_1_4_10}} | {{COUNT_1_4_10}} |
| 1.4.11 | Non-text Contrast | AA | {{STATUS_1_4_11}} | {{COUNT_1_4_11}} |
| 1.4.12 | Text Spacing | AA | {{STATUS_1_4_12}} | {{COUNT_1_4_12}} |
| 1.4.13 | Content on Hover or Focus | AA | {{STATUS_1_4_13}} | {{COUNT_1_4_13}} |
| 2.1.1 | Keyboard | A | {{STATUS_2_1_1}} | {{COUNT_2_1_1}} |
| 2.1.2 | No Keyboard Trap | A | {{STATUS_2_1_2}} | {{COUNT_2_1_2}} |
| 2.1.4 | Character Key Shortcuts | A | {{STATUS_2_1_4}} | {{COUNT_2_1_4}} |
| 2.2.1 | Timing Adjustable | A | {{STATUS_2_2_1}} | {{COUNT_2_2_1}} |
| 2.2.2 | Pause, Stop, Hide | A | {{STATUS_2_2_2}} | {{COUNT_2_2_2}} |
| 2.3.1 | Three Flashes or Below Threshold | A | {{STATUS_2_3_1}} | {{COUNT_2_3_1}} |
| 2.4.1 | Bypass Blocks | A | {{STATUS_2_4_1}} | {{COUNT_2_4_1}} |
| 2.4.2 | Page Titled | A | {{STATUS_2_4_2}} | {{COUNT_2_4_2}} |
| 2.4.3 | Focus Order | A | {{STATUS_2_4_3}} | {{COUNT_2_4_3}} |
| 2.4.4 | Link Purpose (In Context) | A | {{STATUS_2_4_4}} | {{COUNT_2_4_4}} |
| 2.4.5 | Multiple Ways | AA | {{STATUS_2_4_5}} | {{COUNT_2_4_5}} |
| 2.4.6 | Headings and Labels | AA | {{STATUS_2_4_6}} | {{COUNT_2_4_6}} |
| 2.4.7 | Focus Visible | AA | {{STATUS_2_4_7}} | {{COUNT_2_4_7}} |
| 2.5.1 | Pointer Gestures | A | {{STATUS_2_5_1}} | {{COUNT_2_5_1}} |
| 2.5.2 | Pointer Cancellation | A | {{STATUS_2_5_2}} | {{COUNT_2_5_2}} |
| 2.5.3 | Label in Name | A | {{STATUS_2_5_3}} | {{COUNT_2_5_3}} |
| 2.5.4 | Motion Actuation | A | {{STATUS_2_5_4}} | {{COUNT_2_5_4}} |
| 3.1.1 | Language of Page | A | {{STATUS_3_1_1}} | {{COUNT_3_1_1}} |
| 3.1.2 | Language of Parts | AA | {{STATUS_3_1_2}} | {{COUNT_3_1_2}} |
| 3.2.1 | On Focus | A | {{STATUS_3_2_1}} | {{COUNT_3_2_1}} |
| 3.2.2 | On Input | A | {{STATUS_3_2_2}} | {{COUNT_3_2_2}} |
| 3.2.3 | Consistent Navigation | AA | {{STATUS_3_2_3}} | {{COUNT_3_2_3}} |
| 3.2.4 | Consistent Identification | AA | {{STATUS_3_2_4}} | {{COUNT_3_2_4}} |
| 3.3.1 | Error Identification | A | {{STATUS_3_3_1}} | {{COUNT_3_3_1}} |
| 3.3.2 | Labels or Instructions | A | {{STATUS_3_3_2}} | {{COUNT_3_3_2}} |
| 3.3.3 | Error Suggestion | AA | {{STATUS_3_3_3}} | {{COUNT_3_3_3}} |
| 3.3.4 | Error Prevention (Legal, Financial, Data) | AA | {{STATUS_3_3_4}} | {{COUNT_3_3_4}} |
| 4.1.1 | Parsing | A | {{STATUS_4_1_1}} | {{COUNT_4_1_1}} |
| 4.1.2 | Name, Role, Value | A | {{STATUS_4_1_2}} | {{COUNT_4_1_2}} |
| 4.1.3 | Status Messages | AA | {{STATUS_4_1_3}} | {{COUNT_4_1_3}} |

**Status Legend:** PASS | FAIL | NEEDS REVIEW | NOT TESTED

---

## 3. Issue-by-Issue Breakdown

> Issues are ordered by severity (Critical first) then by number of affected pages.

### Issue {{ISSUE_NUMBER}}: {{ISSUE_TITLE}}

| Field | Detail |
|-------|--------|
| **axe-core Rule ID** | `{{AXE_RULE_ID}}` |
| **WCAG Criterion** | {{WCAG_CRITERION}} — {{WCAG_CRITERION_NAME}} |
| **Conformance Level** | {{WCAG_LEVEL}} |
| **Severity** | {{SEVERITY}} |
| **Pages Affected** | {{AFFECTED_PAGE_COUNT}} of {{PAGES_SCANNED}} pages |
| **Elements Affected** | {{ELEMENT_COUNT}} instances |

**What This Means (Plain English):**

{{PLAIN_ENGLISH_DESCRIPTION}}

**Who Is Impacted:**

{{USER_IMPACT_DESCRIPTION}}

**Legal Risk Context:**

{{LEGAL_RISK_CONTEXT}}

**Affected Pages:**

| Page URL | Element | HTML Snippet |
|----------|---------|-------------|
| {{PAGE_URL_1}} | {{ELEMENT_SELECTOR_1}} | `{{HTML_SNIPPET_1}}` |
| {{PAGE_URL_2}} | {{ELEMENT_SELECTOR_2}} | `{{HTML_SNIPPET_2}}` |

**How to Fix:**

{{REMEDIATION_NARRATIVE}}

Before (broken):
```html
{{CODE_BEFORE}}
```

After (fixed):
```html
{{CODE_AFTER}}
```

**Estimated Fix Effort:** {{EFFORT_LEVEL}} ({{EFFORT_TIME_ESTIMATE}})

**Verification:** {{VERIFICATION_STEPS}}

---

*[Repeat Issue block for each violation found]*

---

## 4. Priority Matrix

### Impact vs. Effort Quadrant

```
                    LOW EFFORT                    HIGH EFFORT
                    (< 1 hour)                    (> 4 hours)
              ┌─────────────────────┬─────────────────────┐
  HIGH        │                     │                     │
  IMPACT      │    FIX NOW          │    PLAN SPRINT      │
  (Critical/  │                     │                     │
   Serious)   │ {{FIX_NOW_ITEMS}}   │ {{PLAN_SPRINT_ITEMS}}│
              │                     │                     │
              ├─────────────────────┼─────────────────────┤
  LOW         │                     │                     │
  IMPACT      │    QUICK WINS       │    BACKLOG          │
  (Moderate/  │                     │                     │
   Minor)     │ {{QUICK_WIN_ITEMS}} │ {{BACKLOG_ITEMS}}   │
              │                     │                     │
              └─────────────────────┴─────────────────────┘
```

### Fix-First List (High Impact + Low Effort)

| Priority | Issue | Fix Time | Impact |
|----------|-------|----------|--------|
| 1 | {{PRIORITY_1_ISSUE}} | {{PRIORITY_1_TIME}} | {{PRIORITY_1_IMPACT}} |
| 2 | {{PRIORITY_2_ISSUE}} | {{PRIORITY_2_TIME}} | {{PRIORITY_2_IMPACT}} |
| 3 | {{PRIORITY_3_ISSUE}} | {{PRIORITY_3_TIME}} | {{PRIORITY_3_IMPACT}} |
| 4 | {{PRIORITY_4_ISSUE}} | {{PRIORITY_4_TIME}} | {{PRIORITY_4_IMPACT}} |
| 5 | {{PRIORITY_5_ISSUE}} | {{PRIORITY_5_TIME}} | {{PRIORITY_5_IMPACT}} |

---

## 5. Remediation Roadmap

### Phase 1: Critical Fixes (Week 1)

These issues create the highest legal exposure and should be addressed immediately.

| Issue | WCAG | Affected Pages | Est. Time | Developer Action |
|-------|------|---------------|-----------|-----------------|
| {{PHASE1_ISSUE_1}} | {{PHASE1_WCAG_1}} | {{PHASE1_PAGES_1}} | {{PHASE1_TIME_1}} | {{PHASE1_ACTION_1}} |
| {{PHASE1_ISSUE_2}} | {{PHASE1_WCAG_2}} | {{PHASE1_PAGES_2}} | {{PHASE1_TIME_2}} | {{PHASE1_ACTION_2}} |
| {{PHASE1_ISSUE_3}} | {{PHASE1_WCAG_3}} | {{PHASE1_PAGES_3}} | {{PHASE1_TIME_3}} | {{PHASE1_ACTION_3}} |

### Phase 2: Serious Fixes (Week 2-3)

These issues significantly degrade the experience for users with disabilities.

| Issue | WCAG | Affected Pages | Est. Time | Developer Action |
|-------|------|---------------|-----------|-----------------|
| {{PHASE2_ISSUE_1}} | {{PHASE2_WCAG_1}} | {{PHASE2_PAGES_1}} | {{PHASE2_TIME_1}} | {{PHASE2_ACTION_1}} |
| {{PHASE2_ISSUE_2}} | {{PHASE2_WCAG_2}} | {{PHASE2_PAGES_2}} | {{PHASE2_TIME_2}} | {{PHASE2_ACTION_2}} |

### Phase 3: Moderate and Minor Fixes (Week 3-4)

These issues should be addressed for best-practice compliance.

| Issue | WCAG | Affected Pages | Est. Time | Developer Action |
|-------|------|---------------|-----------|-----------------|
| {{PHASE3_ISSUE_1}} | {{PHASE3_WCAG_1}} | {{PHASE3_PAGES_1}} | {{PHASE3_TIME_1}} | {{PHASE3_ACTION_1}} |

### Total Estimated Remediation Effort

| Phase | Issues | Est. Hours | Priority |
|-------|--------|-----------|----------|
| Phase 1 (Critical) | {{PHASE1_COUNT}} | {{PHASE1_HOURS}} | Immediate |
| Phase 2 (Serious) | {{PHASE2_COUNT}} | {{PHASE2_HOURS}} | Within 2 weeks |
| Phase 3 (Moderate/Minor) | {{PHASE3_COUNT}} | {{PHASE3_HOURS}} | Within 4 weeks |
| **Total** | **{{TOTAL_ISSUES}}** | **{{TOTAL_HOURS}}** | |

---

## 6. What This Scan Cannot Detect

Automated tools detect approximately 57% of WCAG issues. The following categories require manual testing with assistive technologies and are NOT covered by this report:

| Category | Why Automation Fails | Recommendation |
|----------|---------------------|----------------|
| Screen reader reading order | Requires actual assistive technology testing | Test with NVDA (free) or VoiceOver |
| Cognitive accessibility | Requires understanding of user intent | Manual UX review |
| Focus trap detection | Requires keyboard navigation simulation | Manual keyboard testing |
| Meaningful alt text quality | axe confirms alt exists; cannot assess meaning | Human review of all alt text |
| Error recovery in forms | Requires form submission testing | Manual form testing |
| Timing/animation issues | Requires interaction with time-based media | Manual observation |
| Custom widget behavior | Non-native UI requires AT testing | Manual screen reader testing |
| PDF/document accessibility | Outside browser DOM scope | Separate PDF audit |

**Recommended next step:** Commission a manual expert audit to cover the remaining 43% of potential issues. We can connect you with certified accessibility specialists.

---

## 7. Next Steps

1. **Immediate (This Week):** Address all Critical severity issues listed in Phase 1 of the Remediation Roadmap
2. **Short-term (2 Weeks):** Complete Phase 2 (Serious) fixes
3. **Medium-term (1 Month):** Complete Phase 3 and schedule a re-scan to verify fixes
4. **Ongoing:** Consider monthly monitoring to catch regressions introduced by code changes
5. **Recommended:** Engage a manual accessibility expert for the 43% of issues automated tools cannot detect

---

## Report Metadata

| Field | Value |
|-------|-------|
| Report generated | {{GENERATION_TIMESTAMP}} |
| axe-core version | {{AXE_VERSION}} |
| WCAG standard tested | WCAG 2.1 / 2.2 Level AA |
| AI model (per-page) | Claude Haiku 4.5 |
| AI model (summary) | Claude Sonnet 4.6 |
| Scanner false positive rate | <8% (Deque published benchmark) |
| Detection coverage | ~57% of WCAG issues by volume |

---

**{{BRAND_NAME}}** | {{BRAND_WEBSITE}} | {{BRAND_EMAIL}}

*This report was generated using automated scanning tools and AI analysis. It is provided for informational purposes only and does not constitute legal advice or a guarantee of regulatory compliance.*
