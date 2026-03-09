---
name: cs-qbr-builder
description: "Build a Quarterly Business Review outline for a customer. Trigger when the user says 'QBR prep', 'quarterly business review', or 'customer review'."
---

Produces a QBR structure covering value delivered, usage metrics, milestones hit, upcoming plans, and expansion opportunities. Leads with outcomes, not features.

## Process

### Step 1: Load Context

Read these files before proceeding:

- `sidekick/memory/accounts/[customer].md` - load account health, contacts, and history (if it exists)
- `sidekick/context/team-directory.md` - identify account owner and sponsor contacts
- `sidekick/outputs/` - scan for prior QBR docs or meeting notes for this customer (if it exists)

### Step 2: Clarify the QBR Scope

If the user hasn't specified, ask:

- Which customer is this QBR for?
- What are the key metrics or value outcomes you want to highlight?

Skip questions if the user's message already answers them.

### Step 3: Build the QBR Outline

Produce the structure below. Flag any sections with missing data rather than inventing numbers.

Check for commitments made in prior QBRs — surface any that are unresolved.

### Step 4: Save Output

Write to `sidekick/outputs/qbr-[customer]-[DATE].md`.

## Output Format

```markdown
# QBR: [Customer Name] — [Quarter]

**Date:** [DATE] | **Account owner:** [Name] | **Customer sponsor:** [Name, Title]

## Agenda

1. Progress against goals set last quarter
2. Value delivered
3. Usage and adoption
4. Upcoming milestones
5. Open items and next steps

## Progress Against Last Quarter's Goals

| Goal              | Status         | Notes           |
| ----------------- | -------------- | --------------- |
| [goal from prior] | Hit/Missed/N/A | [what happened] |

## Value Delivered

- [Outcome 1 — quantified if possible]
- [Outcome 2]

## Usage & Adoption

| Metric   | Last Quarter | This Quarter | Trend        |
| -------- | ------------ | ------------ | ------------ |
| [metric] | [value]      | [value]      | Up/Down/Flat |

## Upcoming Milestones

| Milestone   | Target Date | Owner  |
| ----------- | ----------- | ------ |
| [milestone] | [date]      | [name] |

## Expansion Opportunities

- [Opportunity with rationale — only if genuine fit]

## Open Items

| Item   | Owner  | Due    |
| ------ | ------ | ------ |
| [item] | [name] | [date] |
```

## After This Skill

- **cs-account-health** — update account health score after the QBR → Read `skill-packs/customer-success/skills/cs-account-health.md`
- **meeting-processor** — process the QBR meeting notes → Read `skills/meeting-processor/SKILL.md`

## Rules

- Lead with value delivered, not product features or roadmap announcements.
- Flag any commitments made in the prior QBR that remain unresolved.
- Never fabricate usage metrics or business outcomes. State "data unavailable" where needed.
- Expansion opportunities should only appear if there is genuine fit — not as a default upsell section.
