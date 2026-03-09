---
name: compliance-checklist
description: "Generate a compliance checklist for a specific regulation or standard and map requirements against current state. Trigger when the user says 'compliance check', 'regulatory requirements', 'GDPR check', 'SOC 2', or 'data privacy'."
---

# Compliance Checklist

Maps the requirements of a specific regulation or standard (GDPR, SOC 2, HIPAA, ISO 27001, etc.) against current state. Produces a gap analysis with ownership and remediation priorities.

## Process

### Step 1: Load Context

Read:

- `sidekick/memory/projects/*.md` - Understand the scope of systems and data in play
- `sidekick/memory/decisions.md` - Check for prior compliance decisions or deferred items

### Step 2: Identify Scope

If not specified, ask:

- Which regulation or standard? (GDPR, CCPA, SOC 2 Type I/II, HIPAA, ISO 27001, PCI DSS, other)
- What is in scope? (specific product, service, data type, geography)
- What is the target date or audit deadline?
- Is this a first assessment or a re-check of known gaps?

### Step 3: Generate the Checklist

For the specified standard, enumerate the key requirement categories and map current state to each.

**Compliance status values:**

- **Met** — requirement is fully satisfied with evidence
- **Partial** — requirement is partially addressed, gaps remain
- **Gap** — requirement is not addressed
- **N/A** — requirement does not apply to this scope

### Step 4: Output the Checklist

Save to `sidekick/outputs/compliance-[standard]-[DATE].md`.

```markdown
# Compliance Checklist: [Standard / Regulation]

**Date:** [date] | **Scope:** [product / system / geography]
**Audit deadline:** [date or "None"]

## Summary

| Status  | Count |
| ------- | ----- |
| Met     | [n]   |
| Partial | [n]   |
| Gap     | [n]   |
| N/A     | [n]   |

**Overall readiness:** [percentage met or partial out of applicable requirements]

## Requirements

| Requirement        | Category   | Status  | Evidence / Notes                    | Owner  | Priority     |
| ------------------ | ---------- | ------- | ----------------------------------- | ------ | ------------ |
| [Requirement name] | [Category] | Met     | [Where evidence lives]              | [name] | -            |
| [Requirement name] | [Category] | Partial | [What's done and what's missing]    | [name] | High/Med/Low |
| [Requirement name] | [Category] | Gap     | [What needs to be built or adopted] | [name] | High/Med/Low |

## Gap Remediation Plan

| Gap                | Action Required        | Owner  | Effort       | Due    |
| ------------------ | ---------------------- | ------ | ------------ | ------ |
| [Requirement name] | [Specific remediation] | [name] | High/Med/Low | [date] |

## Open Questions

- [Question requiring clarification before assessment can be finalized]
```

## After This Skill

- **blocker-audit** — surface any compliance gaps that are actively blocking a project or launch → Read `skill-packs/automation/skills/auto-blocker-audit.md`

## Rules

- Do not mark a requirement as "Met" unless there is evidence to support it. Ask the user to confirm.
- Partial credit is only valid when the gap portion is documented with specifics.
- Every gap must have a Priority rating. Unranked gaps do not get fixed.
- If the regulation or standard is outside your training data or the scope is highly specialized, say so and recommend external counsel.
- Scope section is mandatory. Compliance without defined scope is meaningless.
