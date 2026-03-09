---
name: career-compass
description: "Map current skills vs desired role, identify gaps, and suggest prioritized learning actions. Trigger when the user says 'career planning', 'where am I going', 'career path', 'skills gap', or 'what should I learn'."
---

# Career Compass

Builds a clear picture of where you are, where you're going, and what's in the way. Produces a skills gap map with prioritized learning actions grounded in your actual work patterns, not generic frameworks.

## Process

### Step 1: Load Context

Read these files:

- `sidekick/context/about-me.md` - Current role, background, stated aspirations
- `sidekick/context/current-priorities.md` - What's being worked on (signals actual skill use)
- `sidekick/context/working-preferences.md` - How they prefer to learn and develop (if it exists)
- `sidekick/memory/confidence-flags.md` - Areas of recurring uncertainty - these are gap signals (if it exists)

### Step 2: Clarify Direction

If not specified, ask:

- What role or position are you aiming toward? (title, scope, or type of work)
- What's the timeframe? (6 months, 1 year, 3 years)
- Are there specific skills or gaps you already know about?

Skip questions if the user's message already answers them.

### Step 3: Build the Map

**Current skills:** Infer from about-me.md and current-priorities.md. What does the work require? What gets flagged in confidence-flags.md?

**Target role requirements:** Based on the stated direction, what skills and experiences does that role typically require?

**Gap analysis:** Cross-reference. Where are the clear gaps? Where are the hidden gaps (things the user doesn't know they'll need)?

**Learning priorities:** Rank gaps by: (1) how much they'd unblock the target role and (2) how quickly they can be addressed.

### Step 4: Generate Output

Save to `sidekick/memory/career-compass.md`.

```markdown
# Career Compass

**Updated:** [date] | **Current role:** [role] | **Target:** [target role or direction]
**Horizon:** [timeframe]

## Where I Am Now

**Strengths (evidence-based):**

- [Skill]: [how it shows up in current work]
- [Skill]: [evidence]

**Known gaps (from confidence-flags.md):**

- [Area]: [pattern observed]

---

## Where I'm Going

**Target:** [specific role, scope, or type of work]

**What that role requires:**

- [Requirement 1]
- [Requirement 2]
- [Requirement 3]

---

## Gap Map

| Skill / Experience | Current Level                   | Required Level                | Gap Size               | Priority |
| ------------------ | ------------------------------- | ----------------------------- | ---------------------- | -------- |
| [skill]            | [beginner / developing / solid] | [developing / solid / expert] | [big / medium / small] | [H/M/L]  |

---

## Learning Plan

### Priority 1: [Biggest gap]

- **Why it matters:** [how this gap shows up in the target role]
- **How to close it:** [specific action - project, course, mentorship, practice]
- **Signal of progress:** [how you'll know you're improving]

### Priority 2: [Next gap]

[Same structure]

---

## Revisit Signals

- Review this when: confidence-flags.md adds a new category, a role change happens, or at each annual review.
```

## After This Skill

| If...                                                   | Suggest...                             |
| ------------------------------------------------------- | -------------------------------------- |
| The gap map surfaces identity or role clarity questions | Read `skills/context-refresh/SKILL.md` |

## Rules

- Strengths must be evidence-based, not self-reported. Pull from what the work actually shows.
- Gap size is relative to the target. A skill that's "fine for now" may still be a gap for the target role.
- Learning plan must be specific. "Read more" is not a plan. A named resource with a feedback loop is.
- Never fabricate. If you can't find it, say so.
