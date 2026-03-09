---
name: pm-prioritize-features
description: "Score and rank features using RICE, ICE, and MoSCoW with a final recommendation."
---

Runs features through multiple prioritization frameworks and produces a ranked list with a clear recommendation. Prevents gut-feel prioritization masquerading as rigor.

## Context Loading

1. Read `sidekick/context/current-priorities.md` - features that don't serve a current priority need explicit justification
2. Read `sidekick/context/team-directory.md` - identify who owns each feature area
3. Read `sidekick/context/communication-style.md` - match output style

Ask before generating:

- What is the list of features to prioritize? (paste or describe)
- What is the team's capacity for the next cycle?
- Is there a hard constraint (launch date, dependency) that overrides score?

## Process

1. **Collect the feature list** - ask user to provide or pull from context
2. **Score RICE** - Reach, Impact, Confidence, Effort (score each 1-10, effort is inverted)
3. **Score ICE** - Impact, Confidence, Ease (1-10 each)
4. **Apply MoSCoW** - Must / Should / Could / Won't based on strategic necessity
5. **Synthesize** - average RICE and ICE scores, weight by MoSCoW, produce ranked list
6. **Recommend** - call out top 3 to do now and explain why

## Output Format

```markdown
# Feature Prioritization: [Context / Sprint / Initiative]

**Date:** [date] | **Cycle:** [Q / Sprint]

## RICE Scores

| Feature | Reach  | Impact | Confidence | Effort | RICE Score  |
| ------- | ------ | ------ | ---------- | ------ | ----------- |
| [name]  | [1-10] | [1-10] | [1-10]     | [1-10] | [(R*I*C)/E] |

## ICE Scores

| Feature | Impact | Confidence | Ease   | ICE Score |
| ------- | ------ | ---------- | ------ | --------- |
| [name]  | [1-10] | [1-10]     | [1-10] | [avg]     |

## MoSCoW

| Must       | Should     | Could      | Won't (this cycle) |
| ---------- | ---------- | ---------- | ------------------ |
| [features] | [features] | [features] | [features]         |

## Ranked List

| Rank | Feature | RICE    | ICE     | MoSCoW | Rationale |
| ---- | ------- | ------- | ------- | ------ | --------- |
| 1    | [name]  | [score] | [score] | Must   | [why]     |

## Recommendation

**Do now:** [top 3 features with one-line justification each]
**Defer:** [features and why they're not now]
**Drop:** [features that scored low enough to remove from backlog]
```

## Rules

- Scores are estimates. Document assumptions, especially for Reach and Impact.
- A Must that scores low on RICE is still a Must - frameworks inform, they don't decide
- Always produce a recommendation. A ranked list without a call is not useful.
- If two features are within 10% of each other in score, note the tie and use MoSCoW as tiebreaker
- Flag features that don't map to a current priority - they need explicit justification to stay
