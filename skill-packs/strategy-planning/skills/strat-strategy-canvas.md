---
name: strategy-canvas
description: "Build a Playing to Win strategic canvas covering Where to Play, How to Win, Capabilities Required, and Management Systems. Trigger when the user says 'strategy canvas', 'strategic options', 'where to play', or 'how to win'."
---

# Strategy Canvas

Applies the Playing to Win framework to make strategic choices explicit. Forces answers to the two questions that matter: where you'll compete and how you'll win there.

## Process

### Step 1: Load Context

Read these files:

- `sidekick/context/about-me.md` - Role, organization, and what they're trying to achieve
- `sidekick/context/current-priorities.md` - What's being optimized for right now
- `sidekick/context/communication-style.md` - Match output style (if it exists)
- `sidekick/memory/competitors/` - Existing competitor profiles to inform the "how to win" section (if it exists)

### Step 2: Clarify Scope

If not specified, ask:

- Is this canvas for a product, a team, a business unit, or yourself personally?
- What time horizon? (1 year, 3 years, 5 years)
- Are there any strategic bets already made that this canvas should reflect?

Skip questions if the user's message already answers them.

### Step 3: Build the Canvas

Work through each layer of the Playing to Win cascade in sequence. Each choice constrains the next - don't skip ahead.

**Winning Aspiration:** What does winning look like? Not a mission statement - a concrete picture of success.

**Where to Play:** Which customers, channels, geographies, and product categories will you compete in? Equally important: where will you NOT play?

**How to Win:** What is the sustainable advantage in the chosen arenas? Cost leadership, differentiation, network effects, relationships - be specific.

**Capabilities Required:** What must be true about your capabilities to win in those arenas with that approach?

**Management Systems:** What processes, metrics, and structures reinforce the strategy?

### Step 4: Generate Output

Save to `sidekick/outputs/strategy-canvas-[DATE].md`.

```markdown
# Strategy Canvas

**Built:** [date] | **Scope:** [product / team / personal]
**Horizon:** [1 / 3 / 5 years]

---

## Winning Aspiration

[What does winning look like? Concrete and specific. Not "be the best" - what does that mean in practice?]

---

## Where to Play

**In scope:**

- Customer segment: [who specifically]
- Geography / market: [where]
- Product / service area: [what]
- Channel: [how you reach them]

**Explicitly out of scope:**

- [What you've decided NOT to pursue and why]

---

## How to Win

[The specific sustainable advantage you'll build in the arenas above. 2-3 sentences max.]

**Primary advantage:** [cost / differentiation / access / relationships / speed]
**Why it's defensible:** [what makes it hard to copy]

---

## Capabilities Required

| Capability   | Current State                   | Gap             | Priority |
| ------------ | ------------------------------- | --------------- | -------- |
| [capability] | [strong / developing / missing] | [what's needed] | [H/M/L]  |

---

## Management Systems

| Area      | What's needed to reinforce the strategy |
| --------- | --------------------------------------- |
| Metrics   | [What you'll measure]                   |
| Processes | [What you'll do regularly]              |
| Structure | [How you'll organize]                   |

---

## Strategic Bets

- [The 2-3 most consequential choices embedded in this canvas]
```

## After This Skill

| If...                                              | Suggest...                                                             |
| -------------------------------------------------- | ---------------------------------------------------------------------- |
| Competitive landscape needs deeper analysis        | Read `skill-packs/product-management/skills/pm-competitor-analysis.md` |
| Ready to turn this into a quarterly execution plan | Read `skill-packs/strategy-planning/skills/strat-quarterly-plan.md`    |

## Rules

- "Where to Play" without explicit out-of-scope is incomplete. Choices only matter if alternatives were rejected.
- "How to Win" must be specific to the arenas chosen. A generic advantage statement is not a strategy.
- Capabilities gap table is mandatory. Strategy without capability analysis is wishful thinking.
- Never fabricate. If you can't find it, say so.
