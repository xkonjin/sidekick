---
name: pm-retro
description: "Run a sprint or project retrospective: went well, went wrong, actions, themes."
---

Produces a structured retrospective with categorized findings and concrete follow-through actions. Turns team frustration into systemic improvement.

## Context Loading

1. Read `sidekick/context/team-directory.md` - know who the participants are
2. Read `sidekick/context/communication-style.md` - match output style
3. If a previous retro exists in `sidekick/outputs/`, read it to check if prior actions were completed

Ask before generating:

- What sprint or project is this retro for?
- Who participated?
- Input format: will participants share their notes here, or should I generate a template for async collection first?

## Process

1. **Collect input** - gather what went well, what went wrong, and what's still confusing
2. **Cluster themes** - group related items to avoid 20 separate action items for one root cause
3. **Prioritize** - not all problems are equally worth fixing. What has the highest leverage?
4. **Draft actions** - specific, owned, time-bound. No vague "improve communication" items.
5. **Check prior actions** - were last retro's actions completed? If not, escalate or drop them.

## Output Format

```markdown
# Retrospective: [Sprint N / Project Name]

**Date:** [date] | **Facilitator:** [name] | **Team:** [names]

## What Went Well

- [Item] - [why it worked, what to repeat]
- [Item]

## What Went Wrong

- [Item] - [root cause if known]
- [Item]

## Themes

| Theme                       | Items grouped | Priority |
| --------------------------- | ------------- | -------- |
| [e.g. Communication gaps]   | [3 items]     | High     |
| [e.g. Unclear requirements] | [2 items]     | Medium   |

## Action Items

| Action            | Owner  | Due    | Success looks like     |
| ----------------- | ------ | ------ | ---------------------- |
| [specific action] | [name] | [date] | [what done looks like] |

## Prior Actions Review

| Action (from [prev retro date]) | Status                       | Notes     |
| ------------------------------- | ---------------------------- | --------- |
| [action]                        | Done / In progress / Dropped | [context] |

## Carry Forward

[Anything that needs escalation, a decision from leadership, or longer-term tracking]
```

## Rules

- Actions must have an owner and a due date. Unowned actions don't get done.
- "Improve X" is not an action. "By [date], [name] will do [specific thing] to improve X" is.
- Never list more than 5 action items. If there are more, force prioritization.
- Prior actions review is mandatory if a previous retro exists. Accountability matters.
- Themes section prevents action item explosion - look for patterns before writing actions.
