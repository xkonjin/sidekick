---
name: stakeholder-influence
description: "Map stakeholder interests and build a sequenced influence plan to get buy-in from resistant stakeholders. Trigger when the user says 'how do I convince', 'get buy-in', 'influence strategy', 'they keep saying no', or 'build support'."
---

# Stakeholder Influence

Produces a structured influence plan for a specific decision or initiative. Maps who needs to be convinced, what they care about, and the sequence and evidence most likely to move them.

## Process

### Step 1: Load Context

- `sidekick/context/team-directory.md` - Roles, reporting lines, known priorities per person
- `sidekick/memory/relationship-map.md` - Prior alignment signals, any known friction (if it exists)
- `sidekick/memory/decisions.md` - Prior decisions that may be precedents or blockers

### Step 2: Clarify the Ask

If not already specified, ask:

- What decision or initiative are you trying to get support for?
- Who are the key stakeholders that need to be convinced or informed?
- Who is already aligned? Who is the main resistance?
- What is the deadline or decision point?

### Step 3: Build the Influence Plan

Follow the output format below.

### Step 4: Save Output

Write to `sidekick/outputs/influence-plan-[topic]-[DATE].md`

## Output Format

```markdown
# Influence Plan: [Topic]

**Date:** [DATE] | **Decision point:** [Date or milestone] | **Goal:** [What you need them to agree to]

## Stakeholder Map

| Name   | Role   | Current stance                          | What they care about | Key concern                   | Influence lever                   |
| ------ | ------ | --------------------------------------- | -------------------- | ----------------------------- | --------------------------------- |
| [Name] | [Role] | Aligned / Neutral / Resistant / Unknown | [Their priorities]   | [What might make them say no] | [What's most likely to move them] |

## Sequence

[Who to talk to first, and why. Explain the logic: allies before skeptics, decision-maker last, etc.]

1. [Person] — [Why first] — [What to say]
2. [Person] — [Why second] — [What to say]

## Evidence to Prepare

- [Data point, precedent, or example most relevant to the key concerns]
- [Supporting material for the most resistant stakeholder]

## Who to Loop In

[Anyone whose endorsement would carry weight with the resistant parties — not just for info, but for social proof]

## Watch For

- [Known dynamic or tension that could derail the effort]
- [Stakeholder whose stance is uncertain but consequential]
```

## After This Skill

| Next skill    | When                                                              | How to load                                                |
| ------------- | ----------------------------------------------------------------- | ---------------------------------------------------------- |
| meeting-prep  | To prepare for the specific conversation with the key stakeholder | Read `skill-packs/automation/skills/auto-meeting-prep.md`  |
| email-drafter | To draft an outreach or pre-read message to a stakeholder         | Read `skill-packs/automation/skills/auto-email-drafter.md` |

## Rules

- Surface assumptions. People situations have more unknowns than data problems.
- Never claim to know a stakeholder's motivations with certainty. Label all stances as best guesses unless the user has confirmed them.
- If a stakeholder's position is unknown, mark it explicitly rather than guessing.
- Sequence logic should be explained, not just asserted.
- Do not treat influence as manipulation. Flag if a proposed approach involves withholding relevant information.
