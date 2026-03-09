---
name: annual-review
description: "Synthesize the year's work into a narrative review covering accomplishments, decisions, lessons, and forward implications. Trigger when the user says 'annual review', 'year in review', or 'yearly planning'."
---

# Annual Review

Turns a year of scattered outputs into a coherent narrative: what was built, what was learned, what patterns emerged, and what that means for next year.

## Process

### Step 1: Load Context

Read these files:

- `sidekick/context/about-me.md` - Identity and role context for framing the review
- `sidekick/context/current-priorities.md` - What the year was supposed to be about
- `sidekick/context/working-preferences.md` - Formatting preferences (if it exists)
- `sidekick/memory/decisions.md` - Key decisions made during the year (if it exists)
- `sidekick/memory/confidence-flags.md` - Areas of recurring uncertainty or error (if it exists)
- `sidekick/memory/projects/` - Completed and in-progress project files

### Step 2: Clarify Scope

If not specified, ask:

- Which year?
- Is this personal, professional, or both?
- Should it include forward-looking planning or just look back?

Skip questions if the user's message already answers them.

### Step 3: Synthesize the Year

**Accomplishments:** What shipped, launched, or closed? Pull from projects and weekly outputs if available.

**Decisions:** What were the 3-5 most consequential decisions? What was the reasoning and what resulted?

**Misses:** What didn't happen that was supposed to? What got deprioritized, cancelled, or stalled?

**Patterns:** What shows up repeatedly in confidence-flags.md? What types of work went well vs. poorly?

**Relationships:** Who did you work most closely with? Who had the most influence on outcomes?

**Surprises:** What turned out differently than expected, in either direction?

### Step 4: Generate Output

Save to `sidekick/outputs/annual-review-[YEAR].md`.

```markdown
# Annual Review: [YEAR]

**Written:** [date] | **Role during this year:** [role from about-me.md]

## The Year in One Paragraph

[3-5 sentences. Honest characterization of what the year was, not just a highlights reel.]

## What Got Done

| Project / Initiative | Outcome                                           | Quarter |
| -------------------- | ------------------------------------------------- | ------- |
| [name]               | [shipped / stalled / cancelled + one-line result] | [Q#]    |

## Consequential Decisions

| Decision   | Reasoning | Outcome         |
| ---------- | --------- | --------------- |
| [decision] | [why]     | [what happened] |

## What Didn't Happen

- [Item that was planned but didn't ship or land - and why]

## Patterns

**Went well:** [recurring strength]
**Went poorly:** [recurring gap or error pattern]

## Lessons

1. [Lesson extracted from a specific experience, not a platitude]
2. [Lesson]
3. [Lesson]

## Implications for Next Year

- [What this review suggests you should do differently]
- [What to stop, start, or continue]
```

## After This Skill

| If...                                         | Suggest...                                                          |
| --------------------------------------------- | ------------------------------------------------------------------- |
| Ready to translate this into next year's plan | Read `skill-packs/strategy-planning/skills/strat-quarterly-plan.md` |

## Rules

- "The Year in One Paragraph" must be honest, not a PR statement. If the year was hard, say so.
- Lessons must be specific. "Communicate better" is not a lesson. "Follow up after every cross-team dependency within 48 hours" is.
- Never fabricate accomplishments. If no output exists for a claimed achievement, flag it.
- Never fabricate. If you can't find it, say so.
