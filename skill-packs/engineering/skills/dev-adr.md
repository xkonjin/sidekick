---
name: adr
description: "Write an Architecture Decision Record. Trigger when the user says 'architecture decision', 'ADR', 'document this decision', 'record why we chose X', or 'write up this technical choice'."
---

# Architecture Decision Record (ADR)

Documents a significant architectural decision so future engineers understand what was decided, why, and what was rejected.

## Process

### Step 1: Load Context

Read:

- `sidekick/context/working-preferences.md` - Formatting preferences (if it exists)
- `sidekick/memory/decisions.md` - Check if this decision is already tracked

### Step 2: Gather Information

Ask if not provided in the trigger:

- What is the decision being made?
- What problem does it solve?
- What alternatives were considered?
- Why was this option chosen over the others?
- What are the known downsides or tradeoffs?
- Who is involved or affected?
- Is this reversible? At what cost?

### Step 3: Write the ADR

```markdown
# ADR-[NUMBER]: [Short title — decision made, not problem]

**Date:** [YYYY-MM-DD]
**Status:** [Proposed / Accepted / Deprecated / Superseded by ADR-XXX]
**Deciders:** [Names or roles]

## Context

[What situation or constraint forced this decision? What were the forces at play?
Be specific. A future reader should understand the problem without needing external docs.]

## Decision

[What was decided. State it directly. "We will use X" not "X was considered".]

## Consequences

**Positive:**

- [What gets better as a result]

**Negative:**

- [What gets worse or harder]

**Neutral:**

- [What changes but is neither better nor worse]

## Alternatives Considered

| Option     | Why Rejected              |
| ---------- | ------------------------- |
| [Option A] | [Specific reason it lost] |
| [Option B] | [Specific reason it lost] |

## Notes

[Anything else relevant: links to discussion, related ADRs, review date if time-bound]
```

### Step 4: Save and Cross-Reference

- Save to `sidekick/memory/decisions.md` or a dedicated ADR directory if one exists
- If this supersedes an earlier decision, note it in both records
- Ask the user where to save the file

## Rules

- Title should state the decision, not the problem: "Use PostgreSQL for primary storage" not "Database selection"
- Be honest about downsides. A one-sided ADR is useless.
- Do not inflate the alternatives section with options that were never seriously considered
- If you don't know why an alternative was rejected, say so rather than guessing
