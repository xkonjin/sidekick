---
name: energy-audit
description: "Analyse where the user's time and energy is going, identify drains and misallocations, and surface recovery opportunities. Trigger when the user says 'I'm burned out', 'energy audit', 'what's draining me', 'where does my time go', or 'feeling overwhelmed'."
---

# Energy Audit

Maps how you are actually spending time and energy against what matters. Identifies drains, misallocations, and recovery opportunities. Produces an honest snapshot — not a motivational exercise.

## Process

### Step 1: Load Context

- `sidekick/context/about-me.md` - Role, working style, what energises vs drains
- `sidekick/context/current-priorities.md` - What is supposed to matter right now
- `sidekick/TASKS.md` - What tasks are live (if it exists)
- Calendar data — ask the user to share recent week(s) if calendar tools are not connected

### Step 2: Clarify the Scope

Ask if not already clear:

- Are you looking at the last week, last month, or a specific period?
- Is the main issue time (capacity), energy (what's draining you emotionally or cognitively), or both?
- Are there specific areas you already suspect are the problem?

### Step 3: Build the Audit

Follow the output format below.

### Step 4: Save Output

Write to `sidekick/outputs/energy-audit-[DATE].md`

## Output Format

```markdown
# Energy Audit — [DATE]

**Period covered:** [Week / Month / Other] | **Source:** Calendar / TASKS.md / Recollection

## Time Allocation vs Priority Alignment

| Category    | Estimated time % | Priority level                    | Verdict                          |
| ----------- | ---------------- | --------------------------------- | -------------------------------- |
| [Work area] | [%]              | High / Med / Low / Not a priority | Aligned / Misallocated / Unknown |

## Energy Drains

| Item                       | Type                                         | Impact           | Addressable?         |
| -------------------------- | -------------------------------------------- | ---------------- | -------------------- |
| [Task / meeting / dynamic] | Time sink / Cognitive load / Emotional drain | High / Med / Low | Yes / No / Partially |

## Misallocations

[Specific instances where time is going to low-priority work while high-priority work is stalled]

## Recovery Opportunities

- [What could be cut, delegated, or deferred with low cost]
- [What could shift to a lower-energy time of day or format]

## Data Gaps

- [Areas where there was insufficient information to assess — flagged rather than guessed]

## Recommended Focus Shifts

| From               | To                           | How                                     |
| ------------------ | ---------------------------- | --------------------------------------- |
| [Current activity] | [Priority it should replace] | [Delegation / cut / defer / time-block] |
```

## After This Skill

| Next skill         | When                                                           | How to load                                                      |
| ------------------ | -------------------------------------------------------------- | ---------------------------------------------------------------- |
| delegation-planner | If specific tasks should be handed off to reclaim capacity     | Read `skill-packs/eq-navigation/skills/eq-delegation-planner.md` |
| context-refresh    | If priorities feel stale and need re-examination before acting | Read `skills/context-refresh/SKILL.md`                           |

## Rules

- Surface assumptions. People situations have more unknowns than data problems.
- Do not fabricate time estimates. If calendar data is not available, ask the user to provide rough allocations before building the audit.
- Burnout signals are real but not diagnostic. This skill produces a planning document, not a clinical assessment.
- Recovery opportunities should be concrete (specific task, meeting, or commitment) not generic advice.
- Flag data gaps explicitly rather than filling them with guesses.
