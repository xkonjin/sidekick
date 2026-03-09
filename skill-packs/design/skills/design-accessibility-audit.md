---
name: accessibility-audit
description: "WCAG 2.1 AA accessibility audit. Trigger when the user says 'accessibility check', 'a11y audit', 'WCAG', 'is this accessible', 'screen reader check', or 'accessibility review'."
---

# Accessibility Audit

You are conducting a WCAG 2.1 AA compliance audit. Every finding must include severity, the specific WCAG criterion it violates, and a concrete fix. No abstract recommendations.

## Context Loading

Before auditing, read:

- `sidekick/context/about-me.md` — understand the product type (web, mobile, internal tool)
- `sidekick/context/current-priorities.md` — understand launch timelines and what's critical
- `sidekick/context/communication-style.md` — match output format to preferences

## Severity Classification

| Severity | Meaning                                                                  |
| -------- | ------------------------------------------------------------------------ |
| Critical | Blocks access entirely for users with disabilities. Fix before shipping. |
| High     | Significantly impairs use. Fix before launch.                            |
| Medium   | Creates friction. Fix in next sprint.                                    |
| Low      | Minor deviation. Fix when touching the component.                        |

## Audit Checklist

### 1. Contrast Ratios (WCAG 1.4.3, 1.4.11)

- Normal text: minimum 4.5:1
- Large text (18px+/bold 14px+): minimum 3:1
- UI components and focus indicators: minimum 3:1
- Flag any color combinations that look marginal — provide the exact ratio if measurable

### 2. Text Alternatives (WCAG 1.1.1)

- Every non-decorative image has meaningful alt text
- Icons used as buttons have aria-label or visually hidden text
- Complex charts/graphs have text descriptions

### 3. Keyboard Navigation (WCAG 2.1.1, 2.1.2)

- All interactive elements reachable by Tab
- No keyboard traps (can always navigate away)
- Custom components (dropdowns, modals, date pickers) implement correct ARIA patterns
- Logical tab order matches visual reading order

### 4. Focus Indicators (WCAG 2.4.7, 2.4.11)

- Visible focus ring on all interactive elements
- Focus indicator has at least 3:1 contrast against adjacent colors
- Not suppressed globally with `outline: none` without a custom replacement

### 5. Screen Reader Compatibility (WCAG 1.3.1, 4.1.2)

- Semantic HTML used where possible (button, nav, main, h1-h6)
- ARIA roles only where native HTML is insufficient
- Dynamic content updates announced via live regions
- Form inputs have associated labels (not just placeholder text)

### 6. Error Handling (WCAG 3.3.1, 3.3.2, 3.3.3)

- Errors identified in text (not just color)
- Error messages describe what's wrong and how to fix it
- Required fields marked and announced to screen readers

### 7. Motion & Animation (WCAG 2.3.3)

- Animations can be paused or disabled
- No flashing content (more than 3 times/second)
- Respects `prefers-reduced-motion`

## Output Format

```
## Accessibility Audit: [Screen/Component/Flow]

### Summary
| Severity | Count |
|----------|-------|
| Critical |       |
| High     |       |
| Medium   |       |
| Low      |       |

### Findings

**Critical**
- [Element/Location]: [Issue] | WCAG [criterion] | Fix: [specific action]

**High**
- [Element/Location]: [Issue] | WCAG [criterion] | Fix: [specific action]

**Medium**
- [Element/Location]: [Issue] | WCAG [criterion] | Fix: [specific action]

**Low**
- [Element/Location]: [Issue] | WCAG [criterion] | Fix: [specific action]

### Passed
- [Items that are correctly implemented — only list if genuinely passing]

### Cannot Evaluate
- [Items requiring live testing or screen reader verification]
```

## Rules

- Every finding cites a specific WCAG criterion (e.g., 1.4.3, 2.1.1)
- Never guess at contrast ratios — if you can't measure, flag for manual check
- Do not mark something as passing if it hasn't been verified
- If evaluating from screenshots only, be explicit about what requires code inspection
