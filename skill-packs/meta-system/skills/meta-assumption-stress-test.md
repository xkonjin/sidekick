---
name: meta-assumption-stress-test
description: "Systematically attack a plan to find fragile assumptions and blind spots. Trigger when the user says 'stress test this', 'challenge my thinking', 'devil's advocate', 'what am I missing', or 'blind spots'."
---

# Assumption Stress Test

Adversarial review of a plan, decision, or belief. The goal is to find what would break it before reality does. Surfaces fragile assumptions, missing evidence, and failure modes the user hasn't considered.

## Process

### Step 1: Load Context

Read these files:

- `sidekick/memory/decisions.md` - Prior decisions that the plan depends on (if it exists)
- `sidekick/memory/confidence-flags.md` - Known areas of uncertainty to probe harder (if it exists)

### Step 2: Identify the Target

If not specified, ask:

- What should be stress-tested? (a plan, a decision, a belief, a strategy)

If the user has already described it, take it directly from their message. Don't ask again.

### Step 3: Run the Attack

Be genuinely adversarial. Softball critiques are useless.

Work through each attack vector:

**Fragile assumptions:** What does the plan assume to be true that hasn't been verified? If that assumption is wrong, what breaks?

**Missing evidence:** What claims are made without data? What would change the conclusion if the data showed something different?

**Optimism bias:** Where is the plan assuming best-case? What's the realistic case? What's the bad case?

**Second-order effects:** What happens next after the plan succeeds? Any unintended consequences?

**Counterarguments:** What's the strongest case AGAINST this plan? Not a strawman - the actual best argument an intelligent opponent would make.

**Failure modes:** If this fails in 6 months, what's the most likely reason? Distinguish recoverable from fatal failures.

### Step 4: Generate Output

Save to `sidekick/outputs/stress-test-[topic]-[DATE].md`.

```markdown
# Stress Test: [Plan / Decision / Topic]

**Date:** [date]

## Fragile Assumptions

| Assumption | Evidence for it | What breaks if it's wrong | Severity |
|------------|-----------------|--------------------------|----------|
| [assumption] | [evidence or "none"] | [consequence] | [Fatal / Recoverable / Minor] |

## Missing Evidence

- [Claim]: no data backing this. Would need [specific data] to validate.

## Where the Plan Is Optimistic

| Area | Best case (assumed) | Realistic case | Bad case |
|------|--------------------|-|----------|
| [area] | [assumption] | [realistic] | [downside] |

## Strongest Counterargument

[The most compelling case AGAINST this plan, stated as its advocate would state it - not softened.]

## Failure Modes

| Failure | Probability | Recoverable? | Early signal |
|---------|-------------|--------------|--------------|
| [how it fails] | [H/M/L] | [Yes / No] | [what to watch for] |

## What Would Change Your Mind

- [Specific piece of evidence or event that would invalidate this plan]
- [Another one]

## Verdict

[Overall: is this plan ready to execute, needs more validation on specific points, or has a fatal flaw?]
```

## After This Skill

| If... | Suggest... |
|-------|-----------|
| A key decision needs to be re-examined based on this | Read `skills/decision-log/SKILL.md` |
| Multiple futures need to be mapped from this uncertainty | Read `skill-packs/strategy-planning/skills/strat-scenario-planner.md` |

## Rules

- Be genuinely adversarial. If every criticism feels mild, the stress test failed.
- Flag assumptions with no evidence separately from assumptions with weak evidence. Both are problems, but different kinds.
- Distinguish recoverable from fatal failure modes. A plan can survive recoverable failures; fatal ones should stop the plan.
- The strongest counterargument must be stated as a proponent would state it, not as a strawman.
- Never fabricate. If you can't find it, say so.
