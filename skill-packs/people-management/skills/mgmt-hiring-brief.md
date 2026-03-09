---
name: hiring-brief
description: "Create a hiring brief for a new role: gap analysis, responsibilities, and 90-day success criteria."
---

Produces a structured hiring brief grounded in the actual team gap, not a recycled job title. Focuses on outcomes over credentials.

## Context Loading

1. Read `sidekick/context/team-directory.md` - understand current team composition and identify the gap
2. Read `sidekick/context/current-priorities.md` - confirm urgency and alignment to active priorities
3. Read `sidekick/context/communication-style.md` - match voice for any externally facing sections

If the role isn't described yet, ask: "What problem does this hire solve?" before starting.

## Process

1. **Define the gap** - ask: what is the team unable to do today, and why is a new hire the answer?
2. **Review team composition** - check team-directory for existing coverage. Flag if the role overlaps with someone already on the team.
3. **Check priority alignment** - is this hire tied to a current priority? If not, flag it.
4. **Draft the brief** - follow the output format below.
5. **Save output** - write to `sidekick/outputs/hiring-brief-[role]-[DATE].md`

## Output Format

```markdown
# Hiring Brief: [Role Title]

**Date:** [DATE] | **Hiring manager:** [Name] | **Target start:** [timeframe]

## Why We're Hiring

[2-3 sentences. What is the team unable to do? What breaks if we don't hire?]

## Team Context

[Where this role sits. Who they work with. What the team is focused on.]

## Responsibilities

- [Outcome-oriented responsibility, not task list]
- [5-7 items maximum]

## Must-Have Skills

- [Skill with rationale — why is this non-negotiable?]

## Nice-to-Have Skills

- [Skill that would accelerate ramp-up but isn't blocking]

## Success in 90 Days Looks Like

- [Specific, observable outcome by end of first 90 days]
- [Second outcome]
- [Third outcome]

## Open Questions

- [Anything unresolved: level, comp band, team structure]
```

## After This Skill

- **mgmt-team-capacity-planner** — to validate that the gap is structural, not a temporary crunch → Read `skill-packs/people-management/skills/mgmt-team-capacity-planner.md`
- **pm-stakeholder-map** — if this is a cross-functional role needing broad alignment → Read `skill-packs/product-management/skills/pm-stakeholder-map.md`

## Rules

- Focus on outcomes, not credentials. "5 years of experience" is not a requirement unless you can explain why.
- Flag if the role significantly overlaps with an existing team member's scope.
- Flag if the hire doesn't map to a current priority.
- Never include salary or compensation details in this document.
