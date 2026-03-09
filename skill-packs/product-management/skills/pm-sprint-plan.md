---
name: pm-sprint-plan
description: "Build a sprint plan: goal, capacity, story selection, risk assessment."
---

Produces a sprint plan grounded in team capacity and current priorities. Surfaces risks before the sprint starts, not during.

## Context Loading

1. Read `sidekick/context/current-priorities.md` - sprint goal must connect to a top priority
2. Read `sidekick/context/team-directory.md` - identify team members and their roles
3. Read `sidekick/context/communication-style.md` - match output tone

Ask before generating:

- What sprint number / dates?
- Who is on the team and what is their capacity (any PTO, interviews, on-call)?
- What is the backlog source (Linear, Jira, Notion, paste here)?
- What is the team's typical velocity?

## Process

1. **Set the sprint goal** - one sentence tied to a current priority
2. **Assess capacity** - total available points/hours after accounting for absences
3. **Select stories** - prioritize by goal alignment, then dependency order, then quick wins
4. **Identify risks** - what could derail this sprint?
5. **Define done** - what does a successful sprint look like?

## Output Format

```markdown
# Sprint [N] Plan

**Dates:** [start] - [end]
**Goal:** [One sentence. What does the team achieve and why does it matter?]

## Team Capacity

| Person | Role   | Days available | Notes                   |
| ------ | ------ | -------------- | ----------------------- |
| [name] | [role] | [N]            | [PTO, interviews, etc.] |

**Total capacity:** [points or hours]
**Committed:** [planned points] | **Buffer:** [remaining - good to hold ~20%]

## Committed Stories

| Story   | Points | Owner  | Dependency        |
| ------- | ------ | ------ | ----------------- |
| [title] | [pts]  | [name] | [blocker or none] |

## Stretch (if ahead of pace)

| Story   | Points | Owner  |
| ------- | ------ | ------ |
| [title] | [pts]  | [name] |

## Risks

| Risk   | Likelihood | Impact | Mitigation |
| ------ | ---------- | ------ | ---------- |
| [risk] | H/M/L      | H/M/L  | [plan]     |

## Definition of Done

- [ ] All committed stories merged and deployed to staging
- [ ] QA signed off on acceptance criteria
- [ ] [any sprint-specific conditions]
```

## Rules

- Sprint goal must be a single sentence. If it needs two sentences, the scope is too broad.
- Always hold 15-20% buffer capacity. Never commit 100%.
- Never commit a story with an unresolved upstream dependency
- If velocity data is unavailable, note it and use conservative estimates
