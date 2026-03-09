# Adaptation Engine

How Sidekick learns and improves over time. This is what separates it from a static prompt template.

## Self-Correction

When you correct Sidekick ("that's wrong, it's actually X"), the self-correct skill triggers a 5-step process:

1. **Acknowledge** - Confirm the correction without arguing
2. **Scope** - Determine what category the error falls into (people, strategy, process, etc.)
3. **Propagate** - Search ALL relevant memory files and fix every occurrence
4. **Log** - Record the correction in `sidekick/memory/confidence-flags.md`
5. **Detect patterns** - After 5+ corrections in the same category, identify the root cause

**Example correction flow:**

```
You: "Karen isn't on the research team anymore, she moved to product"

Sidekick:
1. Acknowledges: "Got it, Karen is now on product."
2. Scope: People/Roles category
3. Updates: CLAUDE.md People table, team-directory.md, any project files mentioning Karen
4. Logs: Correction entry with date, old value, new value
5. Checks: "I have 3 people/role corrections now. 2 more and I'll flag the pattern."
```

## Confidence Tracking

Every piece of information Sidekick stores has an implicit or explicit confidence level:

| Level      | Threshold | Rule                  | Example                                              |
| ---------- | --------- | --------------------- | ---------------------------------------------------- |
| **HIGH**   | 90%+      | Act on it freely      | User stated their own name and role                  |
| **MEDIUM** | 60-89%    | Mention the inference | "Based on the org chart, I believe X reports to Y"   |
| **LOW**    | <60%      | Ask before acting     | "I'm not sure about the deadline. Want me to check?" |

**Confidence degrades over time.** A HIGH confidence fact that hasn't been reconfirmed in 30+ days should be treated with more caution.

**Confidence upgrades require evidence.** To move from LOW to MEDIUM, there needs to be contextual evidence. To move to HIGH, there needs to be explicit confirmation or multiple independent sources.

### The Confidence Flags File

`sidekick/memory/confidence-flags.md` tracks:

- **Active flags** - Topics with their current confidence level and basis
- **Correction log** - Every correction with date, what was wrong, what's true, category
- **Correction patterns** - Recurring error types with root cause analysis

## Pattern Detection

After 5+ corrections in the same category, Sidekick doesn't just fix the individual errors. It asks: "Why do I keep getting this wrong?"

**Common patterns:**

- **Role inference errors**: Guessing titles from meeting context instead of confirmed sources
- **Timeline optimism**: Assuming deadlines will hold when evidence suggests delays
- **Absence as departure**: Assuming someone left the company because they weren't in recent meetings
- **Overprecise numbers**: Stating exact figures when the source gave ranges

When a pattern is detected, Sidekick adjusts its behavior:

- Downgrades the entire category to require confirmation
- Adds a note to the pattern section of confidence-flags.md
- References the pattern in future interactions to avoid repeating the error

## Context Refresh

The `context-refresh` skill runs a systematic comparison between stored memory and recent reality.

**What it checks:**

| Area       | Signal                                                                   |
| ---------- | ------------------------------------------------------------------------ |
| Priorities | Are stated priorities matching actual activity? Any new themes emerging? |
| People     | New faces in meetings? Anyone gone quiet? Role changes?                  |
| Glossary   | New terms appearing in conversations?                                    |
| Decisions  | Review dates that have passed? Assumptions needing revalidation?         |
| Projects   | Status changes? New projects? Completed/cancelled ones?                  |
| Confidence | LOW items with new evidence? HIGH items contradicted?                    |

**Output format:** A diff report with checkboxes. Every change requires user approval. Nothing auto-updates.

**Recommended cadence:** Weekly, ideally Friday afternoon or Monday morning.

## Decay Model

Information has a half-life. Sidekick tracks this implicitly:

| Information Type       | Reliable For | After That                |
| ---------------------- | ------------ | ------------------------- |
| Identity (name, email) | Indefinite   | -                         |
| Role/title             | ~6 months    | Verify on context refresh |
| Priorities             | ~2 weeks     | Flag if no activity       |
| Project status         | ~1 week      | Check on next mention     |
| Decisions              | ~3 months    | Review per schedule       |
| Competitor intel       | ~1 month     | Refresh with web search   |

This isn't enforced programmatically. It's a mental model that context-refresh uses when scanning for staleness.

## The Compound Effect

Week 1: Sidekick knows your name and priorities. Output is generic but structured. Skill packs matched to your role are active.

Week 4: 15+ corrections have refined the model. Communication style is tuned. Two correction patterns identified and adjusted for. Skills start chaining naturally - processing a meeting leads to logging decisions, which feeds your weekly update.

Week 12: Decision log has 40+ entries. Sidekick catches contradictions between new proposals and past decisions. Assumption register has flagged 3 invalidated assumptions before they caused problems. Calendar-aware suggestions feel timely, not robotic.

Week 26: Sidekick knows your voice so well that drafted emails need minimal editing. It predicts which meeting signals are relevant to your priorities. Correction rate has dropped to near-zero in previously problematic categories. The system has organized itself around your actual work patterns.

This is the compound effect: each correction, each decision logged, each context refresh makes every future interaction slightly better.
