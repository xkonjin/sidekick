---
name: research-insight-connector
description: "Surface non-obvious connections across topics the user is tracking, with concrete evidence and suggested actions. Trigger when the user says 'connect the dots', 'pattern across', 'synthesis', or 'what ties this together'."
---

# Insight Connector

Finds non-obvious connections between topics you're tracking. Only surfaces connections with concrete evidence — not vague associations.

## Process

### Step 1: Load Context

Read these files before starting — this skill runs entirely from accumulated data, not user input:

- `sidekick/memory/knowledge/` (if any exist) - the primary source for cross-topic connections
- `sidekick/memory/decisions.md` (if it exists) - decisions that may connect to new knowledge
- `sidekick/memory/projects/` (if any exist) - project context for relevance filtering
- `sidekick/outputs/` - recent digests, briefs, or narratives from the last 30 days (if any exist)

### Step 2: Map Topics

List all distinct topics found across the sources above. Group them:

- Active: topics that appear in current projects or priorities
- Background: topics in knowledge base not currently linked to active work
- Recent: topics added in the last 14 days

### Step 3: Find Connections

For each potential connection, apply a strict evidence test:

- Is there a concrete shared signal (same metric, same company, same mechanism)?
- Would the user be surprised by this connection?
- Can you point to specific evidence in the files you've read?

Discard any connection that fails the evidence test.

### Step 4: Draft the Insight Report

```markdown
# Insight Connector — [DATE]

## Connections Found

### Connection 1: [Short title]

**Topics:** [Topic A] + [Topic B]
**Evidence:** [Specific reference — file, quote, or data point that links them]
**Why it's non-obvious:** [What would someone miss if they looked at these separately?]
**Suggested action:** [What to do with this connection]

---

### Connection 2: [Short title]

**Topics:** [Topic A] + [Topic B]
**Evidence:** [Specific reference]
**Why it's non-obvious:** [Explanation]
**Suggested action:** [Action]

---

### Connection 3: [Short title]

**Topics:** [Topic A] + [Topic B]
**Evidence:** [Specific reference]
**Why it's non-obvious:** [Explanation]
**Suggested action:** [Action]

## Speculative (evidence weaker — treat with caution)

- [Possible connection with weaker evidence — flagged clearly as speculative]

## Topics With No Connections Found

- [Topic] — no cross-topic signal detected yet
```

### Step 5: Save

Save to `sidekick/outputs/insights-[DATE].md`.

## After This Skill

| Condition                                      | Suggestion                                                                             |
| ---------------------------------------------- | -------------------------------------------------------------------------------------- |
| A connection warrants a full research question | **research-brief** → `skill-packs/research-learning/skills/research-brief.md`          |
| A connection leads to a decision               | **decision-log** → `skills/decision-log/SKILL.md`                                      |
| Knowledge gaps identified during the scan      | **knowledge-base** → `skill-packs/research-learning/skills/research-knowledge-base.md` |

## Rules

- Only surface connections with concrete evidence — vague thematic associations don't count
- Limit to 3-5 insights per run; more than that and the signal is lost in noise
- Clearly label speculative connections as speculative — do not present them at the same confidence level as evidenced connections
- Never fabricate connections; if no real cross-topic signal exists, say "nothing notable found this run"
- If knowledge/ is empty or sparse, say so rather than manufacturing insights from insufficient data
