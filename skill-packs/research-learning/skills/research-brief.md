---
name: research-brief
description: "Frame a research question rigorously: decompose it, surface what's known, list open questions, and define a synthesis framework. Trigger when the user says 'research this', 'deep dive on', 'what do we know about', or 'help me think through'."
---

# Research Brief

Scopes research before diving in. Separates what's known from what's open, and specifies what decision the research serves.

## Process

### Step 1: Load Context

Read these files before starting:

- `sidekick/context/current-priorities.md` - confirm the research connects to an active priority
- `sidekick/memory/glossary.md` (if it exists) - check if key terms are already defined
- `sidekick/memory/knowledge/` (if any exist) - avoid duplicating research already filed

### Step 2: Clarify

Ask for anything not already provided:

- What is the research question?
- What decision does this research inform?
- Are there constraints? (time, scope, what sources are available)

Skip questions if the user's message already answers them.

### Step 3: Draft the Research Brief

```markdown
# Research Brief: [Topic]

**Created:** [DATE] | **Decision it informs:** [Decision]

## Core Question

[The single most important question this research must answer]

## Sub-Questions

1. [Sub-question 1 — decomposed from core question]
2. [Sub-question 2]
3. [Sub-question 3]

## What We Know (and Source Reliability)

| Fact / Assumption                   | Source              | Reliability          |
| ----------------------------------- | ------------------- | -------------------- |
| [Known fact 1]                      | [Source]            | High / Medium / Low  |
| [Known fact 2]                      | [Source]            | High / Medium / Low  |
| [Assumption we're treating as fact] | [Why we believe it] | Low — needs checking |

## Open Questions

- [Unanswered question 1 — what we need to find out]
- [Unanswered question 2]
- [Unanswered question 3]

## Sources to Check

- [Source type 1 — e.g., industry reports, competitor sites]
- [Source type 2 — e.g., internal data, prior research]
- [Source type 3]

## Synthesis Framework

[How will we know when we have enough? What format will the output take? (brief, memo, decision, recommendation)]

## Out of Scope

- [What this research will NOT cover — prevents rabbit holes]
```

### Step 4: Save

Save to `sidekick/outputs/research-[topic]-[DATE].md`.

## After This Skill

| Condition                                    | Suggestion                                                                             |
| -------------------------------------------- | -------------------------------------------------------------------------------------- |
| Research produces findings worth filing      | **knowledge-base** → `skill-packs/research-learning/skills/research-knowledge-base.md` |
| Research leads to a decision                 | **decision-log** → `skills/decision-log/SKILL.md`                                      |
| Research involves reading a specific article | **reading-digest** → `skill-packs/research-learning/skills/research-reading-digest.md` |

## Rules

- Separate facts from opinions in the "What We Know" section — mislabeling assumptions as facts corrupts the research
- Always note source reliability; undated, unattributed claims get Low reliability by default
- Scope the research explicitly — state what's out of scope to prevent the brief from expanding indefinitely
- Never fabricate sources or known facts; mark as "unknown — to be researched" if not confirmed
