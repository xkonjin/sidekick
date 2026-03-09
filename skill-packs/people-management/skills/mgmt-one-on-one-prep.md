---
name: one-on-one-prep
description: "Prepare a focused agenda for a 1:1 meeting with a direct report or peer."
---

Produces a one-page 1:1 agenda grounded in recent activity, open items, and priority alignment. Never fabricates context it doesn't have.

## Context Loading

1. Read `sidekick/context/team-directory.md` - identify the person: role, reporting line, current focus
2. Read `sidekick/context/current-priorities.md` - surface topics relevant to this person's work
3. Read `sidekick/context/communication-style.md` - match tone to how you run these meetings
4. Search `sidekick/outputs/` for prior 1:1 docs with this person - check for open carry-forward items

If the person isn't named, ask: "Who is this 1:1 with?" before starting.

## Process

1. **Identify the person** - confirm from team-directory. Note their role and current focus areas.
2. **Scan for open items** - search outputs/ for previous 1:1 docs. List any unresolved follow-ups.
3. **Gather recent signals** - look for this person in recent meeting notes, decisions, or task lists.
4. **Build the agenda** - structure around the five sections below.
5. **Save output** - write to `sidekick/outputs/one-on-one-[name]-[DATE].md`

## Output Format

```markdown
# 1:1 with [Name] — [DATE]

## Open Items from Last Time

- [Item] — status: [done / in progress / carry forward]

## Wins to Acknowledge

- [Specific thing they did well, with context]

## Topics to Discuss

| Topic   | Priority     | Who brings it |
| ------- | ------------ | ------------- |
| [topic] | High/Med/Low | You / Them    |

## Questions to Ask

- [Open question to understand their perspective]
- [Development or growth question]

## Development

- [Skill, growth area, or opportunity to mention]

## Next 1:1

**Date:** [next scheduled date] | **Carry forward:** [items to track]
```

## After This Skill

- **mgmt-feedback-session** — if a topic requires structured feedback delivery → Read `skill-packs/people-management/skills/mgmt-feedback-session.md`
- **mgmt-team-health-check** — if patterns across multiple 1:1s suggest a team-level issue → Read `skill-packs/people-management/skills/mgmt-team-health-check.md`

## Rules

- Never fabricate activity signals. If no prior data exists, ask the user to provide context.
- Keep the agenda to one page. If topics overflow, prioritize the top three.
- Open items from last time are mandatory if a prior 1:1 doc exists.
- Questions should invite dialogue, not yes/no answers.
