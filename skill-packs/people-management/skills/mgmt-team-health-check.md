---
name: team-health-check
description: "Assess team health across delivery, communication, blockers, engagement, and growth."
---

Produces a structured team health report with traffic light ratings per person and team-wide patterns. Designed for manager use — not for sharing with the team directly.

## Context Loading

1. Read `sidekick/context/team-directory.md` - load the full team roster
2. Read `sidekick/context/current-priorities.md` - understand what the team is working toward
3. Read `sidekick/context/communication-style.md` - match output style
4. Search `sidekick/outputs/` for a prior team-health doc - check if previous concerns were resolved

## Process

1. **Load the roster** - list every team member from team-directory.
2. **Scan recent signals** - for each person, check: meeting attendance, blockers raised, tasks completed, engagement in group discussions.
3. **Rate each dimension** - assess Green / Yellow / Red for the five dimensions below.
4. **Identify team-wide patterns** - what themes appear across multiple people?
5. **Save output** - write to `sidekick/outputs/team-health-[DATE].md`

## Output Format

```markdown
# Team Health Check — [DATE]

## Individual Signals

| Person | Delivery | Communication | Blockers | Engagement | Growth | Overall |
| ------ | -------- | ------------- | -------- | ---------- | ------ | ------- |
| [Name] | G/Y/R    | G/Y/R         | G/Y/R    | G/Y/R      | G/Y/R  | G/Y/R   |

## Team-Wide Patterns

- [Pattern observed across 2+ people]
- [Pattern observed across 2+ people]

## Flags

| Person | Flag                | Recommended action                  |
| ------ | ------------------- | ----------------------------------- |
| [Name] | [What was observed] | [e.g. Schedule 1:1, remove blocker] |

## Data Gaps

- [Person or dimension where data was insufficient to rate]

## Prior Health Check Review

[Were concerns from the last check resolved? What carried forward?]
```

## After This Skill

- **mgmt-one-on-one-prep** — for anyone flagged Yellow or Red → Read `skill-packs/people-management/skills/mgmt-one-on-one-prep.md`
- **mgmt-team-capacity-planner** — if delivery signals suggest a capacity issue → Read `skill-packs/people-management/skills/mgmt-team-capacity-planner.md`

## Rules

- Never share individual ratings or this document with the broader team. Patterns only, never names, in group settings.
- Green / Yellow / Red only. No invented scores or numeric ratings.
- Flag explicitly when data is insufficient — do not infer health from silence.
- Prior health check review is mandatory if a previous doc exists in outputs/.
