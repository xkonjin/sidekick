---
name: data-storyteller
description: "Turn data into a clear narrative with headline finding, evidence, context, implications, and action. Trigger when the user says 'tell the story of this data', 'data narrative', 'make sense of', or 'help me present this data'."
---

# Data Storyteller

Translates numbers into decisions. Leads with the "so what", not the "what".

## Process

### Step 1: Load Context

Read these files before starting:

- `sidekick/memory/metrics/` (if any exist) - understand the metric definitions behind the data
- `sidekick/context/communication-style.md` (if it exists) - adapt tone and vocabulary to the user's voice
- `sidekick/context/team-directory.md` - identify the audience and calibrate detail level

### Step 2: Clarify

Ask for anything not already provided:

- What data are we working with?
- Who is the audience? (executive, team, external partner)
- What decision does this narrative need to support?

Skip questions if the user's message already answers them.

### Step 3: Assess Data Quality

Before writing:

- Is the data complete? Flag missing periods or segments.
- Is the sample size sufficient for confident conclusions?
- Are there known data quality issues (tracking gaps, definition changes)?

Flag loudly if the data is too noisy for confident conclusions.

### Step 4: Write the Narrative

```markdown
# Data Narrative: [Topic]

**Date:** [DATE] | **Audience:** [Audience] | **Decision it supports:** [Decision]

## Headline Finding

[One sentence. The most important thing the data shows. Lead with "so what", not "what".]

## Supporting Evidence

| Finding     | Data point        | Context                       |
| ----------- | ----------------- | ----------------------------- |
| [Finding 1] | [Specific number] | [What makes this significant] |
| [Finding 2] | [Specific number] | [Comparison or trend]         |
| [Finding 3] | [Specific number] | [Period or segment context]   |

## What Changed

[What happened to cause this pattern? External event, product change, seasonal shift?]

## What It Doesn't Show

- [Limitation 1 — what this data can't tell us]
- [Limitation 2]

## Implications

- [Implication 1 — what this means for a decision or priority]
- [Implication 2]

## Recommended Action

[One clear action. Who should do what by when.]
```

### Step 5: Save

Save to `sidekick/outputs/data-narrative-[topic]-[DATE].md`.

## After This Skill

| Condition                                       | Suggestion                                                                      |
| ----------------------------------------------- | ------------------------------------------------------------------------------- |
| Narrative becomes part of a status update       | **weekly-update** → `skills/weekly-update/SKILL.md`                             |
| Decision needs to be logged                     | **decision-log** → `skills/decision-log/SKILL.md`                               |
| Audience needs a dashboard instead of narrative | **dashboard-spec** → `skill-packs/data-analytics/skills/data-dashboard-spec.md` |

## Rules

- Lead with "so what" not "what" — the headline must state the implication, not just the number
- Adapt detail level to audience: executives want the conclusion, analysts want the evidence
- Flag when data is too noisy or the sample too small for confident conclusions — never paper over uncertainty
- Never fabricate data points or trend interpretations; if the signal is ambiguous, say so
- Include what the data does NOT show — audiences will ask, and omitting it looks like selective framing
