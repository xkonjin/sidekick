---
name: blocker-audit
description: "Scan for stalled items and blocked work. Trigger when the user says 'check blockers', 'what's stalled', 'blocker report', or 'what's blocked'."
---

# Blocker Audit

Surfaces what's stuck, how long it's been stuck, who's responsible, and whether it needs escalation.

## Process

### Step 1: Load Context

Read these files:

- `sidekick/TASKS.md` - Primary source for in-flight work and waiting-on items
- `sidekick/context/current-priorities.md` - Severity filter: blockers on top priorities rank higher
- `sidekick/context/team-directory.md` - Who owns the items blocking you

### Step 2: Scan for Blockers

**From TASKS.md**, identify items that are:

- Marked as "Waiting On" or "Blocked"
- In-progress tasks with no update logged in 3+ days
- Items assigned to someone else with no response noted

**From Messaging (if connected):** Scan Slack/Teams threads you've started that have gone unanswered for 3+ days.

**From Calendar (if connected):** Check for meetings that were supposed to produce decisions or outputs that haven't surfaced yet.

### Step 3: Classify by Severity

| Tier     | Condition                                     | Action          |
| -------- | --------------------------------------------- | --------------- |
| Critical | Blocking a top-priority item, stalled 7+ days | Escalate now    |
| High     | Blocking active work, stalled 3-6 days        | Follow up today |
| Low      | Minor dependency, stalled < 3 days            | Monitor         |

### Step 4: Output the Report

```markdown
# Blocker Audit - [Date]

## Critical (escalate now)

| Item | Blocked Since | Waiting On | Linked Priority | Recommended Action |
| ---- | ------------- | ---------- | --------------- | ------------------ |

## High (follow up today)

| Item | Blocked Since | Waiting On | Linked Priority | Recommended Action |
| ---- | ------------- | ---------- | --------------- | ------------------ |

## Low (monitoring)

| Item | Blocked Since | Waiting On |
| ---- | ------------- | ---------- |

## Summary

[X] blockers found. [Y] critical. [Z] linked to top priorities.
```

### Step 5: Recommend Next Actions

For each critical or high-severity blocker, suggest a specific action:

- Draft a follow-up message (offer to use email-drafter)
- Escalate to a named person from team-directory.md
- Remove the dependency by changing the approach

## Rules

- Only report on items you can find in connected sources. Don't guess.
- Tie every blocker back to a priority if possible. Decontextualized blockers are less useful.
- Never send follow-up messages without the user's explicit approval.
