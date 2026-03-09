---
name: sales-proposal-builder
description: "Build a structured proposal or SOW outline. Trigger when the user says 'write proposal', 'draft proposal', 'SOW', or 'scope of work'."
---

Produces a proposal outline covering executive summary, problem, solution, scope, timeline, pricing, and terms. Always shows draft for approval before finalizing.

## Process

### Step 1: Load Context

Read these files before proceeding:

- `sidekick/context/current-priorities.md` - confirm this deal aligns with active focus
- `sidekick/context/team-directory.md` - identify the internal deal owner and any relevant stakeholders
- `sidekick/memory/deals/[company].md` - load deal history, contacts, and prior commitments (if it exists)
- `sidekick/memory/decisions.md` - check for any decisions made with this prospect (if it exists)

### Step 2: Clarify the Proposal

If the user hasn't specified, ask:

- What is the scope of work?
- What is the pricing approach? (fixed fee / retainer / usage-based / TBD)
- What is the proposed timeline or start date?

Skip questions if the user's message already answers them.

### Step 3: Draft the Proposal Outline

Produce the proposal outline in the format below. Flag any sections with missing inputs rather than inventing content.

### Step 4: Show for Approval

Present the draft and ask: "Any sections to adjust before I finalize this?"

Never finalize without explicit user approval. Flag any commitments in the proposal text.

### Step 5: Save Output

Write to `sidekick/outputs/proposal-[company]-[DATE].md`.

## Output Format

```markdown
# Proposal: [Company Name]

**Date:** [DATE] | **Prepared by:** [User name] | **Valid until:** [date or TBD]

## Executive Summary

[2-3 sentences: who this is for, what we're proposing, and the primary value delivered]

## Problem Statement

[What we understand their challenge to be, in their language]

## Proposed Solution

[What we're offering and why it addresses their specific situation]

## Scope of Work

### In Scope

- [Deliverable 1]
- [Deliverable 2]

### Out of Scope

- [Explicitly excluded to prevent scope creep]

## Timeline

| Milestone   | Target Date | Notes          |
| ----------- | ----------- | -------------- |
| [Milestone] | [date]      | [dependencies] |

## Pricing

| Item        | Price    | Notes   |
| ----------- | -------- | ------- |
| [line item] | [amount] | [basis] |

**Total:** [amount] | **Payment terms:** [terms]

## Terms

- [Key term 1]
- [Key term 2]

## Next Steps

1. [Action] — [Owner] — [Date]
```

## After This Skill

- **email-drafter** — draft the cover email when sending this proposal → Read `skill-packs/automation/skills/auto-email-drafter.md`
- **sales-deal-tracker** — update the deal stage to Proposal → Read `skill-packs/sales-revenue/skills/sales-deal-tracker.md`

## Rules

- Never include pricing without explicit confirmation from the user.
- Flag any commitments made in the proposal text: "This commits you to X."
- Out of scope section is mandatory. Force the user to define what this isn't.
- Always show draft for approval before finalizing.
- Never fabricate pricing, terms, or legal language.
