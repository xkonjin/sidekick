---
name: meta-weekly-review
description: "Personal reflection on the week: accomplishments, lessons, mistakes, and adjustments. Trigger when the user says 'weekly review', 'review my week', 'what did I learn this week', or 'reflection'."
---

# Weekly Review

Deeper than a status update. This is personal reflection: what actually happened, what you learned, what went wrong, and what you'd do differently. Honest first. Shareable never.

## Process

### Step 1: Load Context

Read these files:

- `sidekick/context/current-priorities.md` - What the week was supposed to serve
- `sidekick/memory/confidence-flags.md` - Recurring error patterns worth watching (if it exists)
- `sidekick/memory/decisions.md` - Any decisions made this week (if it exists)

Also scan `sidekick/outputs/` for any weekly-update files from this week (if any exist).

### Step 2: Gather Input

If not specified, ask:

- Is there anything specific you want to reflect on?

Otherwise run from available data. Do not fabricate events or outcomes not evidenced in files or the current conversation.

### Step 3: Generate the Review

```markdown
# Weekly Review: [Week of DATE]

## The Week in One Sentence

[Honest characterization. Not a highlights reel. What kind of week was it actually?]

## Accomplishments

- [Specific thing completed or moved forward - with evidence]

## What Didn't Move

- [Priority or task with no progress - and why]

## Mistakes and Misses

- [Specific thing that went wrong, fell through, or was handled poorly]
- [No softening. If it was a mistake, name it as one.]

## Lessons

1. [Concrete lesson extracted from a specific event this week - not a platitude]
2. [Lesson]

## Patterns

[Anything showing up for the second or third time? Cross-reference confidence-flags.md if available.]

## Adjustments for Next Week

- [Specific behavior or habit change based on this week's review]
- [Not aspirational goals - concrete adjustments]

## Decisions Made This Week

- [Any decisions that should be logged if not already in decisions.md]
```

### Step 4: Save

Save to `sidekick/outputs/weekly-review-[DATE].md`.

This file is personal. Never treat it as shareable content.

## After This Skill

| If... | Suggest... |
|-------|-----------|
| Context files feel stale based on this week's activity | Read `skills/context-refresh/SKILL.md` |
| Career patterns are emerging from recurring lessons | Read `skill-packs/strategy-planning/skills/strat-career-compass.md` |

## Rules

- This is personal reflection, not external status. Be honest about what didn't work.
- Lessons must be specific. "Be more organized" is not a lesson. "Block 30 minutes every Friday to clear the task queue before it carries over" is.
- Reference concrete events, not vague impressions. If you can't point to a specific thing, don't claim it happened.
- Never fabricate. If you can't find it, say so.
