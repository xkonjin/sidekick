---
name: budget-tracker
description: "Update and review a living budget tracker. Trigger when the user says 'budget status', 'spending update', 'are we on budget', or 'budget review'."
---

# Budget Tracker

Maintains a living budget: category-level allocated vs spent, burn rate, and forward projections. Flags overage and unallocated spend before it becomes a problem.

## Process

### Step 1: Load Context

Read:

- `sidekick/memory/projects/*.md` - Identify active projects and their spending scope
- `sidekick/memory/decisions.md` - Check for budget decisions or approved variances
- `sidekick/memory/budget.md` - Load existing budget if it exists; update rather than replace

### Step 2: Identify Scope

If not specified, ask:

- What period does this cover? (monthly, quarterly, annual, project-based)
- What categories or cost centers are included?
- What is the total budget envelope?
- Is this an update to an existing tracker or a new one?

If updating, ask the user for new spending data since the last update.

### Step 3: Build or Update the Tracker

Calculate for each category:

- **Allocated** — budget assigned to this category
- **Spent** — confirmed spend to date
- **Committed** — approved but not yet invoiced
- **Remaining** — Allocated minus (Spent + Committed)
- **Burn rate** — average monthly spend at current trajectory
- **Projected EOQ/EOY** — if burn rate holds, where will this land?

### Step 4: Write and Save

Write to `sidekick/memory/budget.md`. If the file exists, update the current period data and append to the Change Log.

```markdown
# Budget Tracker

**Period:** [Q1 2026 / FY2026 / Project name]
**Last updated:** [date]
**Total budget:** [amount]

## Summary

| Status          | Amount    |
| --------------- | --------- |
| Total budget    | [amount]  |
| Spent           | [amount]  |
| Committed       | [amount]  |
| Remaining       | [amount]  |
| Burn rate       | [$/month] |
| Projected total | [amount]  |

**Budget health:** [On track / At risk / Over budget]

## Category Breakdown

| Category   | Allocated | Spent    | Committed | Remaining | Status                    |
| ---------- | --------- | -------- | --------- | --------- | ------------------------- |
| [Category] | [amount]  | [amount] | [amount]  | [amount]  | On track / At risk / Over |

## Flags

- [Category or line item that needs attention, with specific concern]

## Change Log

| Date   | Change                             |
| ------ | ---------------------------------- |
| [date] | [What was updated and by how much] |
```

## After This Skill

- **vendor-evaluator** — evaluate a new vendor spend against remaining budget → Read `skill-packs/finance-ops/skills/finance-vendor-evaluator.md`

## Rules

- Never estimate spend. Only record confirmed amounts or ask the user to supply them.
- Committed spend (approved but not invoiced) must be tracked separately from actual spend.
- Flag any category at 80%+ of allocation as "At risk" — not just those already over.
- If no prior budget.md exists and no budget data is provided, ask before creating a blank tracker.
- Budget health summary must reflect the worst-performing category, not just the overall total.
