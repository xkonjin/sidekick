---
name: difficult-conversation
description: "Structure a difficult, sensitive, or confrontational conversation with context, goals, likely perspectives, opening lines, and exit strategies. Trigger when the user says 'difficult conversation', 'how do I say', 'sensitive topic', 'awkward situation', or 'tough talk'."
---

# Difficult Conversation

Structures any confrontation, negotiation, or sensitive situation before you walk into it. More nuanced than SBI feedback — covers ambiguous situations, power dynamics, and conversations where the outcome is uncertain.

## Process

### Step 1: Load Context

Read these files before building the plan:

- `sidekick/context/team-directory.md` - Context on the other person: role, relationship, history
- `sidekick/context/communication-style.md` - Your default tone and approach (if it exists)
- `sidekick/memory/relationship-map.md` - Prior relationship signals, any known tensions (if it exists)

### Step 2: Clarify the Situation

Ask the user for any context not already available:

- Who is this with and what is the relationship?
- What happened, or what is the issue you need to address?
- What outcome do you want from this conversation?
- What are you worried might go wrong?

Do not infer answers to these questions. Ask if they are not provided.

### Step 3: Build the Conversation Plan

Follow the output format below.

### Step 4: Save Output

Write to `sidekick/outputs/conversation-prep-[topic]-[DATE].md`

## Output Format

```markdown
# Conversation Prep: [Topic]

**Date:** [DATE] | **With:** [Name / Role] | **Setting:** [In person / Video / Async]

## Context

[1-2 sentences: what happened and why this conversation is necessary]

## Your Goal

[What you want to be true after this conversation ends — specific, not vague]

## Their Likely Perspective

[What they may be thinking or feeling — label this as your best guess, not fact]
**Uncertainty:** [What you don't know about their view that could change your approach]

## Opening Lines

[2-3 options for how to start. Vary tone: direct, softer, question-led]

1. [Option 1]
2. [Option 2]
3. [Option 3]

## Key Points to Make

1. [Core message — keep to three maximum]
2. [Second point]
3. [Third point]

## Questions to Ask

- [Question that invites their perspective without escalating]
- [Question that moves toward resolution]

## If It Goes Off Track

- **If they get defensive:** [Suggested response or pivot]
- **If they shut down:** [Suggested response or pivot]
- **If it escalates beyond the topic:** [How to refocus or pause]

## Exit Strategies

- **Good outcome:** [What you say to close cleanly]
- **Neutral outcome:** [How to leave it open without losing ground]
- **Bad outcome:** [How to exit without burning the relationship]
```

## After This Skill

| Next skill       | When                                                                          | How to load                                                          |
| ---------------- | ----------------------------------------------------------------------------- | -------------------------------------------------------------------- |
| feedback-session | If this is primarily a performance or behavior issue that fits SBI            | Read `skill-packs/people-management/skills/mgmt-feedback-session.md` |
| meeting-prep     | If this conversation is happening in a scheduled meeting with other attendees | Read `skill-packs/automation/skills/auto-meeting-prep.md`            |

## Rules

- Surface assumptions. People situations have more unknowns than data problems.
- Never claim to know the other person's motivations or feelings with certainty. Label all perspective-taking as conjecture.
- Ask the user for context rather than inferring interpersonal dynamics from thin signals.
- This is planning material only. Never share externally.
- If the user describes a situation involving HR, legal, or safety concerns, flag that professional guidance may be warranted.
