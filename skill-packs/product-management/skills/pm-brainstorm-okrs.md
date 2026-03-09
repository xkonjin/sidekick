---
name: pm-brainstorm-okrs
description: "Draft company or team OKRs with measurable key results and initiatives."
---

Produces a structured OKR set: one or more objectives, 2-4 key results each, and concrete initiatives. Forces measurability from the start.

## Context Loading

1. Read `sidekick/context/current-priorities.md` - OKRs must align with stated priorities
2. Read `sidekick/context/team-directory.md` - identify the right owners per KR
3. Read `sidekick/context/communication-style.md` - match output style

Ask before generating:

- What level are these OKRs? (company, team, personal)
- What time period? (Q1, H1, annual)
- What are the 2-3 biggest bets for this period?
- Are there company-level OKRs these need to ladder into?

## Process

1. **Identify the objectives** - ambitious, qualitative, directional. Not metrics.
2. **Draft key results** - measurable outcomes, not outputs. Each KR has a baseline and a target.
3. **Assign initiatives** - what work drives each KR? Keep this brief (headline only).
4. **Stress-test** - ask: if all KRs hit, does the objective feel achieved? If yes, good. If not, missing a KR.
5. **Check alignment** - do these OKRs connect to current priorities?

## Output Format

```markdown
# OKRs: [Team / Company] - [Period]

---

## Objective 1: [Ambitious, inspiring direction]

**Why this matters:** [1 sentence on strategic rationale]

| Key Result                                    | Baseline   | Target   | Owner  |
| --------------------------------------------- | ---------- | -------- | ------ |
| KR1: [metric increases/decreases from X to Y] | [X]        | [Y]      | [name] |
| KR2: [metric]                                 | [baseline] | [target] | [name] |
| KR3: [metric]                                 | [baseline] | [target] | [name] |

**Initiatives driving this objective:**

- [Initiative 1]
- [Initiative 2]

---

## Objective 2: [Next objective]

[Same structure]

---

## Alignment check

| OKR | Maps to priority | Maps to company OKR         |
| --- | ---------------- | --------------------------- |
| O1  | [priority name]  | [company OKR if applicable] |
```

## Rules

- Key results are outcomes (users, revenue, NPS, time), never outputs (launched, shipped, completed)
- Every KR needs a numeric baseline. "Increase X" with no baseline is not a KR.
- Maximum 4 objectives per period. If more exist, force prioritization.
- Initiatives are not KRs. Keep them separate.
- Flag any KR where baseline data doesn't exist - needs measurement setup first.
