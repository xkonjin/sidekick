---
name: negotiation-prep
description: "Prepare for a negotiation: map interests, define BATNA, plan concessions, and rehearse opening positions. Trigger when the user says 'negotiation prep', 'how to negotiate', 'salary negotiation', 'contract negotiation', or 'prep for negotiation'."
---

# Negotiation Prep

Structures negotiation preparation: clarifies what you want, what they want, where the zone of agreement is, and what to do if it falls apart.

## Process

### Step 1: Load Context

Read:

- `sidekick/context/team-directory.md` - Context on the other party if internal
- `sidekick/context/communication-style.md` - Your default approach (if it exists)
- `sidekick/memory/decisions.md` - Prior decisions that set constraints or precedents

### Step 2: Clarify the Negotiation

Ask if not specified:

- What are you negotiating? (contract, salary, scope, timeline, budget, partnership)
- Who is the other party? What is their role and relationship to you?
- What is your ideal outcome?
- What is the minimum you would accept (walk-away point)?
- What do you think the other side wants?
- What is your deadline or decision point?
- What leverage do you have? What leverage do they have?

### Step 3: Build the Prep Sheet

Follow the output format below.

### Step 4: Save Output

Write to `sidekick/outputs/negotiation-prep-[topic]-[DATE].md`

## Output Format

```markdown
# Negotiation Prep: [Topic]

**Date:** [DATE] | **Other party:** [Name / Role] | **Deadline:** [Date or event]

## Your Position

| Element          | Detail                                     |
| ---------------- | ------------------------------------------ |
| Ideal outcome    | [Best case]                                |
| Acceptable range | [What you'd be satisfied with]             |
| Walk-away point  | [The minimum — below this, you leave]      |
| BATNA            | [Best Alternative to Negotiated Agreement] |

## Their Position (Best Guess)

| Element         | Detail                                           |
| --------------- | ------------------------------------------------ |
| Likely goal     | [What they probably want]                        |
| Constraints     | [What limits them — budget, authority, timeline] |
| Pressure points | [What they need from you or from this deal]      |
| Their BATNA     | [What they do if this falls through]             |

## Zone of Possible Agreement

[Where your acceptable range overlaps with their likely acceptable range. If no overlap is visible, note that and identify what would need to change.]

## Concession Strategy

| Priority | What you could give           | What you'd want in return |
| -------- | ----------------------------- | ------------------------- |
| 1        | [Low-cost concession for you] | [High-value ask]          |
| 2        | [Medium-cost concession]      | [Medium-value ask]        |
| 3        | [Last resort concession]      | [Must-have in return]     |

## Opening Move

[Recommended opening position and framing. Should be ambitious but credible.]

## Watch For

- [Tactics the other side might use]
- [Emotional triggers to manage]
- [Information gaps that could change the picture]

## If It Stalls

[What to do if the negotiation reaches an impasse. Options: reframe, escalate, take a break, invoke BATNA.]
```

## After This Skill

| Next skill             | When                                                 | How to load                                                          |
| ---------------------- | ---------------------------------------------------- | -------------------------------------------------------------------- |
| difficult-conversation | If the negotiation involves a sensitive relationship | Read `skill-packs/eq-navigation/skills/eq-difficult-conversation.md` |
| email-drafter          | To draft the opening message or follow-up            | Read `skill-packs/automation/skills/auto-email-drafter.md`           |
| decision-log           | To log the outcome once the negotiation concludes    | Read `skills/decision-log/SKILL.md`                                  |

## Rules

- BATNA must be defined before the negotiation. Without a walk-away point, you have no leverage.
- Label all assumptions about the other party's position explicitly. You are guessing; own it.
- Concessions should be ordered by cost to you, not by importance to them.
- Never recommend dishonesty, withholding material facts, or manipulative tactics.
- If the user has no BATNA and no leverage, say so directly rather than inventing false confidence.
