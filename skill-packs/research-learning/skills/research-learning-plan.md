---
name: research-learning-plan
description: "Create a structured learning plan with milestones, resources, practice exercises, and time estimates. Trigger when the user says 'I need to learn', 'upskill plan', 'study plan', or 'how do I get better at'."
---

# Learning Plan

Builds a realistic path from current state to target proficiency. Starts with the smallest useful skill, not a curriculum dump.

## Process

### Step 1: Load Context

Read these files before starting:

- `sidekick/context/about-me.md` - role, background, and context that shapes what "proficiency" means
- `sidekick/memory/learning/` (if any exist) - check for existing plans on the same topic before starting fresh

### Step 2: Clarify

Ask for anything not already provided:

- What do you want to learn?
- What's your current level? (zero knowledge / some exposure / intermediate)
- What does "good enough" look like for your role?
- How much time can you invest per week?

Skip questions if the user's message already answers them.

### Step 3: Draft the Learning Plan

```markdown
# Learning Plan: [Skill or Topic]

**Created:** [DATE] | **Target proficiency:** [Description] | **Time budget:** [X hrs/week]

## Current Level

[Honest assessment based on what the user shared. Not flattering — accurate.]

## Why This Skill Matters

[How does this connect to the user's current role and priorities?]

## Milestones

| Milestone | Description                                  | Time estimate | Practice exercise               |
| --------- | -------------------------------------------- | ------------- | ------------------------------- |
| 1         | [Smallest useful capability — first outcome] | [X hrs]       | [Concrete exercise to prove it] |
| 2         | [Next level of capability]                   | [X hrs]       | [Exercise]                      |
| 3         | [Target proficiency marker]                  | [X hrs]       | [Exercise]                      |

## Resources

| Resource                   | Format        | Time required | Best for milestone |
| -------------------------- | ------------- | ------------- | ------------------ |
| [Book / course / resource] | [Book/Video/] | [X hrs]       | [Milestone N]      |

## Progress Markers

[How will you know you've hit each milestone? What can you do or produce that you couldn't before?]

## What to Do This Week

1. [First concrete action — small, achievable, this week]
2. [Second action]

## Review Date

[When to revisit this plan and update based on progress]
```

### Step 4: Save

Save to `sidekick/memory/learning/[topic-slug].md`.

## After This Skill

| Condition                                          | Suggestion                                                                             |
| -------------------------------------------------- | -------------------------------------------------------------------------------------- |
| Learning involves reading specific materials       | **reading-digest** → `skill-packs/research-learning/skills/research-reading-digest.md` |
| Learning connects to a career or strategy question | Suggest reviewing `sidekick/context/current-priorities.md` for alignment               |

## Rules

- Start with the smallest useful skill first — not the most impressive one
- Prefer practice over theory; each milestone must have a concrete exercise, not just "read about"
- Include honest time estimates; learning plans that underestimate time create guilt, not progress
- Never fabricate resources; if you're unsure a course exists, describe what to search for
- If an existing learning plan covers the same topic, update it rather than creating a duplicate
