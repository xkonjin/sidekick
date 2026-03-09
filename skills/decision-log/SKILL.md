---
name: decision-log
description: "Maintain the decision and assumption register. Activates on explicit logging ('log decision', 'record this', 'track assumption') AND on automatic detection when the user states a decision in conversation ('we decided', 'the plan is', 'we're going with', 'final answer is'). Also triggers on queries: 'what did we decide about', 'have we made a call on', 'remind me what we said about'. Works with voice: 'so the decision is...' or 'ok we're locking in...'."
---

# Decision Log

Maintains a living register of decisions made and assumptions being tracked. Prevents re-litigating settled decisions and catches when assumptions become invalid.

## Modes

### Mode 1: Log a New Decision

When the user wants to record a decision:

**Gather:**

- What was decided (specific, not vague)
- Who made or owns the decision
- Why this choice (rationale, not just conclusion)
- What alternatives were rejected (if known)
- What assumptions underpin this decision
- When to review (if time-bound)
- Source: where was this decided? (meeting, Slack, async)

**If source is a meeting,** check available meeting note tools for the exact wording. Don't fabricate.

**Format and append** to `sidekick/memory/decisions.md` under the appropriate category:

```
| D-[NEXT#] | [DATE] | [Decision] | [Owner] | [Rationale] | ACTIVE |
```

**Cross-reference:** Check existing decisions for contradictions. If the new decision contradicts or supersedes an old one:

- Mark the old decision as SUPERSEDED
- Link the new one
- Flag for the user: "This supersedes D-XXX. Confirming that's intentional?"

### Mode 2: Track a New Assumption

When the user wants to track an assumption:

**Gather:**

- What we're assuming is true
- Current evidence for or against
- What would prove this wrong (invalidation signal)
- When to review
- Any linked decisions that depend on this assumption

**Format and append** to the Assumptions Register in `sidekick/memory/decisions.md`:

```
| A-[NEXT#] | [Assumption] | [Evidence] | [Confidence] | [Invalidation signal] | [Review date] | ACTIVE |
```

### Mode 3: Query Existing Decisions

When the user asks "what did we decide about X":

1. Search `sidekick/memory/decisions.md` for the topic
2. If found, present the decision with its full context (rationale, alternatives, assumptions)
3. If not found, say so. Check meeting notes and Slack if available.
4. Check if the decision has a review date that's passed. If so, flag it.

### Mode 4: Assumption Invalidation

When new information contradicts a tracked assumption:

1. Update the assumption's status to INVALIDATED
2. Update the evidence field with the new information
3. Find ALL decisions linked to this assumption
4. Flag each linked decision: "Assumption A-XXX has been invalidated. Decision D-YYY depends on it. Review needed."
5. Present the full impact to the user

## Decision Aging

Decisions and assumptions have a shelf life. During any interaction with this skill:

1. Check for decisions with review dates in the past. Flag them: "Decision D-XXX is due for review."
2. Check for assumptions older than 30 days with no revalidation. Flag them: "Assumption A-XXX hasn't been checked in [X] days."
3. If 3+ decisions are stale, suggest a context refresh (unless you were just chained FROM context-refresh): "Several decisions are due for review. Want to do a full context refresh?" → Read `skills/context-refresh/SKILL.md`

## After This Skill

| If...                             | Suggest...                                                                   |
| --------------------------------- | ---------------------------------------------------------------------------- |
| Decision affects priorities       | "This might shift your priorities." → Read `skills/context-refresh/SKILL.md` |
| Decision contradicts existing one | "Want me to check for other impacts?" → Scan all memory files                |
| It's end of week                  | "Want this in your weekly update?" → Read `skills/weekly-update/SKILL.md`    |
| Assumption needs testing          | "How will you know if this assumption is wrong?" → Add invalidation signal   |

## Rules

- Never fabricate decisions. If you can't find the source, say "I don't have a record of this decision."
- When logging from meetings, check transcripts for exact wording
- Flag contradictions without editorializing. Present both and let the user resolve.
- Decisions can be reversed. Mark old as SUPERSEDED, log the new one. Don't delete.
- Review dates are important. When a review date passes, the decision should be re-evaluated.
