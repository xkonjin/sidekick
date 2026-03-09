---
name: meta-day-planner
description: "Build a focused daily plan from calendar, tasks, and priorities. Trigger when the user says 'plan my day', 'what should I focus on', 'today's plan', 'morning planning', or 'daily priorities'."
---

# Day Planner

Reads what's on your plate and builds a focused day: one must-win, time blocks, meetings flagged for prep, and blockers to address before they compound.

## Process

### Step 1: Load Context

Read these files:

- `sidekick/context/current-priorities.md` - What matters most right now
- `sidekick/TASKS.md` - Active and blocked tasks (if it exists)
- `sidekick/memory/projects/` - Project status for anything needing attention today

If calendar tools are connected, pull today's events. If not, proceed without fabricating events.

### Step 2: Build the Plan

Run from available data. Ask nothing.

**Must-win:** Identify one task or outcome that makes today a success regardless of what else happens. Pick it from the intersection of highest priority and what's actually actionable today.

**Meetings:** List all meetings. Flag any that need prep. Note if meeting load exceeds 4 hours (flag as overload).

**Focus blocks:** Identify gaps between meetings for deep work. Map high-priority tasks to those blocks.

**Blockers:** Surface any tasks blocked by an external dependency. Note how long they've been stuck.

### Step 3: Generate Output

Save to `sidekick/outputs/day-plan-[DATE].md`.

```markdown
# Day Plan: [DATE]

## Must-Win Today

**[Task or outcome]** - [one sentence on why this is the priority]

## Schedule

| Time | Event / Block | Type | Prep needed? |
|------|---------------|------|--------------|
| [time] | [meeting or focus block] | [Meeting / Deep work / Admin] | [Yes: [what] / No] |

[If meetings > 4 hours:]
> Warning: [X] hours of meetings today. Deep work will be limited. Consider what can be deferred.

## Focus Blocks

| Block | Task | Priority | Est. time |
|-------|------|----------|-----------|
| [time range] | [task] | [H/M/L] | [estimate] |

## Blockers to Address

| Blocker | Stuck since | Who unblocks it | Action today |
|---------|-------------|-----------------|--------------|
| [blocker] | [date] | [name] | [specific ask or escalation] |

## Deferred

- [Anything pushed to tomorrow or later, with reason]
```

## After This Skill

| If... | Suggest... |
|-------|-----------|
| A meeting needs prep | Read `skill-packs/automation/skills/auto-meeting-prep.md` |
| Blockers need escalation | Read `skill-packs/automation/skills/auto-blocker-audit.md` |

## Rules

- Lead with the must-win. Everything else is secondary.
- Flag meeting overload (>4 hours) explicitly. Don't normalize it silently.
- Never fabricate calendar events. If calendar tools aren't connected, note that and build the plan from tasks and priorities only.
- Deferred tasks must have a reason. Moving things without explanation creates invisible debt.
- Never fabricate. If you can't find it, say so.
