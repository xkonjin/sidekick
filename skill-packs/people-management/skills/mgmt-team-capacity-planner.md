---
name: team-capacity-planner
description: "Map current team capacity against upcoming work to surface gaps and inform task assignment."
---

Produces a capacity snapshot: who has bandwidth, who is overloaded, and what work is at risk. Uses rough estimates — flags where data is insufficient rather than inventing precision.

## Context Loading

1. Read `sidekick/context/team-directory.md` - load the team roster and current focus areas per person
2. Read `sidekick/context/current-priorities.md` - understand what work is coming next
3. Search `sidekick/outputs/` for recent task lists, sprint plans, or prior capacity docs

## Process

1. **Load the roster** - list every team member from team-directory with their current role and focus.
2. **Map commitments** - for each person, identify: known recurring obligations, active projects, upcoming deadlines.
3. **Estimate utilization** - rough buckets: Available (under-committed), Healthy (on track), At risk (nearing capacity), Overloaded (needs relief).
4. **Surface gaps** - what upcoming work has no clear owner? What priorities are uncovered?
5. **Save output** - write to `sidekick/outputs/team-capacity-[DATE].md`

## Output Format

```markdown
# Team Capacity Snapshot — [DATE]

## Roster

| Person | Role   | Current load                    | Status                                     | Notes               |
| ------ | ------ | ------------------------------- | ------------------------------------------ | ------------------- |
| [Name] | [Role] | [Active projects / commitments] | Available / Healthy / At risk / Overloaded | [Anything relevant] |

## Upcoming Work

| Work item | Priority     | Est. effort  | Current owner        | Capacity status                |
| --------- | ------------ | ------------ | -------------------- | ------------------------------ |
| [item]    | High/Med/Low | [rough size] | [name or unassigned] | Covered / At risk / Unassigned |

## Gaps

- [Specific work item or priority with no clear owner or insufficient bandwidth]

## Recommendations

- [Who should take what, or what should be deferred / descoped]

## Data Gaps

- [People or work items where information was insufficient to assess]
```

## After This Skill

- **mgmt-hiring-brief** — if a capacity gap is structural and recurring, not a short-term crunch → Read `skill-packs/people-management/skills/mgmt-hiring-brief.md`
- **weekly-update** — capacity snapshot informs the weekly planning section → Read `skills/weekly-update/SKILL.md`

## Rules

- Estimates are rough. Label everything as estimates. Do not present this as precise resource tracking.
- Flag data gaps explicitly. If someone's workload is unknown, say so — don't assume.
- Never use this document to micromanage individuals. It is a planning tool for the manager.
- Unassigned high-priority work is always a flag, not a footnote.
