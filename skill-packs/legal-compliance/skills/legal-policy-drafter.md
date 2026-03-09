---
name: policy-drafter
description: "Draft an internal policy or process document. Trigger when the user says 'draft a policy', 'write policy', 'internal policy', or 'process document'."
---

# Policy Drafter

Writes internal policies and process documents: clear purpose, defined scope, specific rules, exceptions, enforcement, and a built-in review schedule.

## Process

### Step 1: Load Context

Read:

- `sidekick/context/about-me.md` - Understand the organization and the user's role (sets authority and tone)
- `sidekick/memory/decisions.md` - Check if this policy formalizes a prior decision
- `sidekick/context/team-directory.md` - Identify the right policy owner and approver
- `sidekick/context/communication-style.md` - Match writing style (if it exists)

### Step 2: Clarify the Policy

Ask if not specified:

- What is the policy topic? (data handling, expense approvals, remote work, incident response, etc.)
- Who does it apply to? (all staff, a specific team, contractors)
- What behavior is this policy meant to establish or prevent?
- Who needs to approve it before it goes live?
- When does it take effect?

### Step 3: Draft the Policy

Structure the policy using the sections below. Be specific — vague policies are ignored.

### Step 4: Output and Save

Save to `sidekick/outputs/policy-[name]-[DATE].md`.

```markdown
# [Policy Name]

**Version:** 1.0 | **Effective date:** [date]
**Owner:** [name from team-directory] | **Approver:** [name]
**Applies to:** [who this covers]
**Next review:** [date — typically 12 months from effective date]

## Purpose

[1-2 sentences. What this policy is for and what problem it addresses.]

## Scope

**In scope:** [Who and what this policy covers, specifically]
**Out of scope:** [Explicit exclusions — prevents ambiguity]

## Definitions

| Term   | Meaning                     |
| ------ | --------------------------- |
| [term] | [plain language definition] |

## Policy Rules

1. [Specific, actionable rule — no ambiguity about what is required]
2. [Specific, actionable rule]
3. [Specific, actionable rule]

## Exceptions

[Who can grant exceptions, under what conditions, and how they must be documented. If no exceptions are permitted, state that explicitly.]

## Enforcement

[What happens when this policy is violated. Be specific about consequences and who decides them.]

## Responsibilities

| Role             | Responsibility                               |
| ---------------- | -------------------------------------------- |
| [Role or person] | [What they are responsible for under policy] |

## Review Schedule

This policy is reviewed [annually / after each significant incident / on [trigger event]]. The owner is responsible for scheduling the review and updating the version number.

## Change Log

| Version | Date   | Change                 |
| ------- | ------ | ---------------------- |
| 1.0     | [date] | Initial policy created |
```

## After This Skill

- **decision-log** — log the policy approval decision and effective date → Read `skills/decision-log/SKILL.md`

## Rules

- Every rule must be specific enough that two people would agree on whether it's been followed.
- "Exceptions process" section is mandatory. Policies without exception handling breed workarounds.
- Enforcement must be concrete. "Appropriate action may be taken" is not enforcement.
- Never draft a policy that formalizes something still under debate. Confirm the decision is made first.
- The review schedule is not optional. A policy with no review date becomes outdated and ignored.
