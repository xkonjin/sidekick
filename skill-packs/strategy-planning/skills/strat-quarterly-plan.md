---
name: quarterly-plan
description: "Build a full quarterly plan from priorities, projects, team capacity, and known deadlines. Trigger when the user says 'quarterly plan', 'Q2 planning', 'next quarter', or 'plan the quarter'."
---

# Quarterly Plan

Turns the quarter ahead into a concrete plan: priorities ranked, projects mapped to capacity, deadlines surfaced, and blockers identified before they hit.

## Process

### Step 1: Load Context

Read these files:

- `sidekick/context/current-priorities.md` - What's active and what should drive quarter focus
- `sidekick/context/team-directory.md` - Who's available and what they own
- `sidekick/context/working-preferences.md` - Preferred planning format (if it exists)
- `sidekick/memory/decisions.md` - Commitments and decisions that constrain the quarter (if it exists)
- `sidekick/memory/projects/` - Active project files for scope and status

### Step 2: Clarify Scope

If not specified, ask:

- Which quarter and year?
- Is this a personal plan, team plan, or both?
- Are there company-level OKRs or targets this needs to align to?
- Any fixed deadlines or commitments already locked in?

Skip questions if the user's message already answers them.

### Step 3: Map the Quarter

**Priorities:** Rank the stated priorities by strategic importance for this quarter. Flag any that are carry-overs from last quarter.

**Projects:** For each active project, assess: current phase, expected completion, owner, and dependencies.

**Capacity:** Cross-reference team-directory.md. Note known absences, part-time contributors, or overloaded people.

**Deadlines:** Surface any fixed dates from projects or decisions files. Sequence work backward from those dates.

**Risks:** Flag where capacity is thin relative to commitments, or where dependencies create schedule risk.

### Step 4: Generate Output

Save to `sidekick/outputs/quarterly-plan-[QUARTER]-[YEAR].md`.

```markdown
# Quarterly Plan: [Q#] [YEAR]

**Built:** [date] | **Covers:** [start date] to [end date]

## Top Priorities This Quarter

1. [Priority 1] - [why it ranks first]
2. [Priority 2] - [why it ranks second]
3. [Priority 3]

## Projects

| Project | Phase   | Owner   | Target Date | Dependencies   | Risk          |
| ------- | ------- | ------- | ----------- | -------------- | ------------- |
| [name]  | [phase] | [owner] | [date]      | [deps or none] | [risk or low] |

## Key Dates

| Date   | Event / Deadline | Priority it serves |
| ------ | ---------------- | ------------------ |
| [date] | [event]          | [priority]         |

## Capacity Notes

[Who is constrained, when, and how that affects sequencing]

## Open Questions

- [Things that need resolution before the quarter can proceed cleanly]

## What We're Not Doing This Quarter

- [Explicitly parked items - clarity on what's out of scope]
```

## After This Skill

| If...                                      | Suggest...                                                                |
| ------------------------------------------ | ------------------------------------------------------------------------- |
| OKRs need to be drafted alongside the plan | Read `skill-packs/product-management/skills/pm-brainstorm-okrs.md`        |
| Capacity planning needs more depth         | Read `skill-packs/people-management/skills/mgmt-team-capacity-planner.md` |

## Rules

- Sequence projects backward from fixed deadlines. Never forward-plan past a hard constraint.
- If stated priorities conflict with available capacity, flag it explicitly - don't silently deprioritize.
- "What we're not doing" section is mandatory. Clarity on out-of-scope prevents scope creep.
- Never fabricate. If you can't find it, say so.
