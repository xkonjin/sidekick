---
name: delegation-planner
description: "Structure a delegation: what to hand off, to whom, how to brief them, checkpoints, and failure handling. Trigger when the user says 'how to delegate', 'hand this off', 'who should own this', or 'I need to let go of'."
---

# Delegation Planner

Structures a clean handoff: the right owner, a proper brief, checkpoints that don't become micromanagement, and a plan for what happens if it goes wrong.

## Process

### Step 1: Load Context

- `sidekick/context/team-directory.md` - Team roster, skills, current focus per person
- `sidekick/context/current-priorities.md` - What's active and what the user should stay focused on

### Step 2: Clarify the Task

If not specified, ask:

- What is the task or responsibility you want to hand off?
- Why now — is this a permanent delegation or a one-time handoff?
- What does a good outcome look like?
- Do you have someone in mind, or do you need help identifying the right person?

### Step 3: Build the Delegation Plan

Follow the output format below.

### Step 4: Save Output

Write to `sidekick/outputs/delegation-plan-[task]-[DATE].md`

## Output Format

```markdown
# Delegation Plan: [Task]

**Date:** [DATE] | **Delegating to:** [Name] | **Type:** Permanent / One-time / Time-boxed

## What Is Being Delegated

[Clear description of the task, scope, and boundaries. What is included and what is not.]

## Why This Person

[Rationale: skills match, development opportunity, capacity, proximity to the work]

## How to Brief Them

### Context to Share

- [Background they need to understand the work]
- [Decisions already made that constrain the work]

### The Ask

[Specific outcome expected, with success criteria]

### Resources and Access

- [Tools, files, contacts, or permissions they'll need]

## Checkpoints

| Date / Milestone | What to review                  | Format                                   |
| ---------------- | ------------------------------- | ---------------------------------------- |
| [Date]           | [Progress check or deliverable] | [Async update / Brief sync / Review doc] |

## If It Goes Wrong

- **If they're stuck:** [What you want them to do — come to you, check with X, try Y first]
- **If quality is off:** [How you'll flag it without taking it back prematurely]
- **If deadline is at risk:** [Escalation path]

## What You're Letting Go Of

[Be explicit about what you are no longer doing. This prevents double-ownership and drift.]
```

## After This Skill

| Next skill            | When                                                         | How to load                                                               |
| --------------------- | ------------------------------------------------------------ | ------------------------------------------------------------------------- |
| one-on-one-prep       | To brief the person formally in a 1:1                        | Read `skill-packs/people-management/skills/mgmt-one-on-one-prep.md`       |
| team-capacity-planner | If this delegation is part of a broader capacity rebalancing | Read `skill-packs/people-management/skills/mgmt-team-capacity-planner.md` |

## Rules

- Surface assumptions. People situations have more unknowns than data problems.
- Never assume someone has capacity without checking. Flag if team-directory data is insufficient to assess.
- The "why this person" section must be grounded in actual information — not a guess based on their title.
- Checkpoints should be light enough to not become micromanagement. Default to async unless the stakes warrant a sync.
- The "what you're letting go of" section is not optional. Ambiguous ownership is a delegation failure mode.
