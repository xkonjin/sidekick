# Skill Tree System Design

A progression system that makes Sidekick more capable and autonomous over time, driven entirely by usage patterns. No configuration, no XP bars, no gamification theater. The user works normally; the system evolves underneath.

---

## 1. Skill Tree Architecture

### Core Insight

The current system has two structural problems:

1. **Skills are flat.** `email-drafter` at week 1 is identical to `email-drafter` at week 26. The skill file never changes, so the behavior never deepens.
2. **Skills are isolated.** `transcript-miner` and `weekly-update` both touch the same data (meetings, decisions, priorities) but don't compound. There's no concept of "these two skills together unlock a third."

The skill tree solves both by adding **depth** (levels within a skill) and **connections** (prerequisites, synergies, and synthesis).

### Tree Structure

Five branches, each representing a domain of knowledge work:

```
                        ┌─────────────────┐
                        │   SIDEKICK      │
                        │   SKILL TREE    │
                        └────────┬────────┘
              ┌──────────┬──────┴──────┬──────────┐
              ▼          ▼            ▼           ▼
        ┌──────────┐ ┌──────────┐ ┌──────────┐ ┌──────────┐
        │ OBSERVE  │ │ ANALYZE  │ │ PRODUCE  │ │ ORGANIZE │
        │          │ │          │ │          │ │          │
        │ meeting  │ │ context  │ │ email    │ │ decision │
        │ capture, │ │ refresh, │ │ drafts,  │ │ log,     │
        │ people,  │ │ competi- │ │ updates, │ │ tasks,   │
        │ signals  │ │ tor, PRD │ │ content  │ │ priority │
        └────┬─────┘ └────┬─────┘ └────┬─────┘ └────┬─────┘
             │            │            │             │
             └────────────┴─────┬──────┴─────────────┘
                                ▼
                          ┌──────────┐
                          │ COMPOUND │
                          │          │
                          │ synergy  │
                          │ skills,  │
                          │ auto-    │
                          │ workflows│
                          └──────────┘
```

### Branch Definitions

| Branch       | What It Covers                        | Core Skills                                       | Pack Skills (examples)                                   |
| ------------ | ------------------------------------- | ------------------------------------------------- | -------------------------------------------------------- |
| **Observe**  | Capturing information from the world  | transcript-miner, meeting-processor, self-correct | competitor-analysis, stakeholder-map                     |
| **Analyze**  | Making sense of captured information  | context-refresh, decision-log                     | pre-mortem, prioritize-features, retro, OKRs             |
| **Produce**  | Generating output in the user's voice | weekly-update, email-drafter                      | blog-post, release-notes, status-report, PRD             |
| **Organize** | Structuring and tracking work         | decision-log, TASKS.md management                 | sprint-plan, tech-debt-tracker, blocker-audit            |
| **Compound** | Cross-branch synergy skills           | (auto-generated)                                  | meeting-to-update, decision-impact, priority-realignment |

### How Skills Map to Levels

Each skill has 3 levels. Levels are not version numbers of the SKILL.md file. They are behavioral modifiers that change HOW the skill operates.

```
Level 1: GUIDED      - Follows the SKILL.md process exactly. Asks for confirmation at every step.
Level 2: CONFIDENT   - Skips unnecessary confirmations. Fills in defaults from learned patterns.
Level 3: ANTICIPATORY - Proactively triggers when context suggests it. Produces output before being asked.
```

**Example: email-drafter progression**

| Level            | Behavior                                                                                                                                                                                |
| ---------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1 (Guided)       | Asks all 4 clarifying questions. Shows full draft. Waits for approval.                                                                                                                  |
| 2 (Confident)    | Skips obvious questions (knows sign-off style, formality per recipient). Applies voice model without asking. Still shows draft.                                                         |
| 3 (Anticipatory) | After a meeting with action items, proactively drafts follow-up emails. Pre-populates from context. Shows draft with "I drafted these follow-ups based on the meeting. Want to review?" |

### Markdown Representation

The skill tree state lives in a single file: `sidekick/progression/skill-tree.md`

```markdown
# Skill Tree

Last updated: 2026-03-15

## Overview

| Branch   | Active Skills | Avg Level | Strongest             |
| -------- | ------------- | --------- | --------------------- |
| Observe  | 3             | 1.7       | transcript-miner (L2) |
| Analyze  | 2             | 1.5       | context-refresh (L2)  |
| Produce  | 2             | 2.0       | weekly-update (L2)    |
| Organize | 1             | 1.0       | decision-log (L1)     |
| Compound | 0             | -         | -                     |

## Skills

### Observe

| Skill             | Level | Uses | Last Used  | Next Level At                      |
| ----------------- | ----- | ---- | ---------- | ---------------------------------- |
| transcript-miner  | 2     | 8    | 2026-03-14 | 12 uses + 0 corrections in last 5  |
| meeting-processor | 1     | 3    | 2026-03-12 | 5 uses                             |
| self-correct      | 2     | 11   | 2026-03-15 | 15 uses + pattern detection active |

### Analyze

| Skill           | Level | Uses | Last Used  | Next Level At |
| --------------- | ----- | ---- | ---------- | ------------- |
| context-refresh | 2     | 4    | 2026-03-10 | 8 uses        |
| decision-log    | 1     | 2    | 2026-03-08 | 5 uses        |

### Produce

| Skill         | Level | Uses | Last Used  | Next Level At                           |
| ------------- | ----- | ---- | ---------- | --------------------------------------- |
| weekly-update | 2     | 6    | 2026-03-14 | 10 uses + audience model built          |
| email-drafter | 2     | 9    | 2026-03-15 | 12 uses + recipient model for 3+ people |

### Organize

| Skill        | Level | Uses | Last Used  | Next Level At |
| ------------ | ----- | ---- | ---------- | ------------- |
| decision-log | 1     | 2    | 2026-03-08 | 5 uses        |

### Compound

(No compound skills unlocked yet. Requires 2+ skills at Level 2 in different branches.)

## Unlock Queue

| Skill             | Branch   | Unlocks When                                   | Progress        |
| ----------------- | -------- | ---------------------------------------------- | --------------- |
| meeting-to-update | Compound | transcript-miner L2 + weekly-update L2         | Ready to unlock |
| recipient-model   | Produce  | email-drafter used with 5+ distinct recipients | 3/5 recipients  |
| proactive-blocker | Organize | blocker-audit L2 + 3+ blockers tracked         | Not started     |
```

### Visual Progress (User-Facing)

When the user asks "show my skill tree" or "how is my sidekick progressing", render this:

```
OBSERVE          ANALYZE         PRODUCE         ORGANIZE
━━━━━━━━         ━━━━━━━         ━━━━━━━         ━━━━━━━━
[██████░] L2     [████░░] L2     [████████] L2   [██░░░░] L1
transcript       context-ref     weekly-upd      decision-log

[███░░░] L1      [██░░░░] L1     [██████░] L2
meeting-proc     decision-log    email-draft

[██████░] L2
self-correct

COMPOUND
━━━━━━━━
[READY] meeting-to-update (transcript-miner + weekly-update)
[2/3]   priority-realign  (context-refresh + decision-log + 10 decisions logged)
```

---

## 2. Progression Mechanics

### Usage Tracking

Every skill invocation gets logged to `sidekick/progression/usage-log.md`. This is append-only, never edited.

```markdown
# Usage Log

| Date       | Skill            | Duration | Outcome                | Corrections | Chain From        | Chain To     |
| ---------- | ---------------- | -------- | ---------------------- | ----------- | ----------------- | ------------ |
| 2026-03-15 | email-drafter    | 2 min    | sent (approved)        | 0           | meeting-processor | -            |
| 2026-03-15 | transcript-miner | 5 min    | 3 decisions, 4 actions | 0           | -                 | decision-log |
| 2026-03-14 | weekly-update    | 4 min    | sent (1 edit)          | 1           | -                 | -            |
| 2026-03-14 | self-correct     | 1 min    | people/roles           | -           | -                 | -            |
```

**What gets tracked:**

| Field         | How Captured                                                           |
| ------------- | ---------------------------------------------------------------------- |
| Date          | Timestamp when skill triggers                                          |
| Skill         | Which SKILL.md was loaded                                              |
| Duration      | Rough estimate (start of skill to final output/save)                   |
| Outcome       | What happened: approved as-is, edited then approved, rejected, chained |
| Corrections   | How many times user corrected the output within this invocation        |
| Chain From/To | Which skill triggered this one, which skill this led to                |

### Level-Up Conditions

Levels are earned, not configured. Each level has specific, measurable conditions.

**Level 1 -> Level 2 (Guided -> Confident):**

| Condition                            | Why                                             |
| ------------------------------------ | ----------------------------------------------- |
| 5+ successful uses                   | Proves the skill is part of the user's workflow |
| Correction rate < 20% in last 5 uses | Proves output quality is acceptable             |
| At least 1 chain completed           | Proves the skill integrates with the workflow   |

**Level 2 -> Level 3 (Confident -> Anticipatory):**

| Condition                                  | Why                                            |
| ------------------------------------------ | ---------------------------------------------- |
| 12+ successful uses                        | Sufficient pattern data                        |
| Correction rate < 10% in last 10 uses      | Output consistently matches expectations       |
| User has approved 3+ proactive suggestions | Proves user trusts autonomous behavior         |
| Branch average >= 1.5                      | Other skills in the branch are also developing |

**What changes at each level:**

```markdown
## Level Behavior Matrix

### Level 1: Guided

- Read full SKILL.md process
- Ask all clarifying questions
- Show output before any file writes
- Announce every memory update
- Chain suggestions are explicit questions

### Level 2: Confident

- Skip clarifying questions where answers are predictable from context
- Apply communication-style.md without mentioning it
- Batch low-stakes memory updates silently
- Chain to next skill automatically if the chain has been followed 3+ times
- Use learned defaults (audience for weekly update, formality per recipient)

### Level 3: Anticipatory

- Trigger proactively when context signals suggest the skill is needed
- Pre-populate output from accumulated patterns
- Only surface for review, not step-by-step confirmation
- Auto-chain common sequences
- Generate compound outputs (e.g., meeting analysis + drafted follow-ups in one pass)
```

### Skill Levels In Practice

The level modifiers are NOT stored in the SKILL.md files. They're applied at runtime by reading `skill-tree.md` before executing any skill. The logic in CLAUDE.md becomes:

```
When a skill triggers:
1. Read the SKILL.md
2. Read sidekick/progression/skill-tree.md for that skill's level
3. Apply level modifiers:
   - L1: Follow SKILL.md exactly
   - L2: Skip steps marked as "skippable at L2" (see modifier format below)
   - L3: Add proactive behaviors from the Anticipatory section
4. After completion, log to usage-log.md and check level-up conditions
```

### Level Modifier Format in SKILL.md

Skills gain a new optional section that defines level-specific behavior:

```markdown
## Level Modifiers

### At Level 2 (Confident)

- Skip: Step 2 clarifying questions when recipient is in team-directory.md
- Default: Use last-used audience setting for weekly updates
- Auto-chain: If this skill was triggered from [skill], automatically chain to [next skill]

### At Level 3 (Anticipatory)

- Proactive trigger: After any meeting with 3+ action items, suggest running this skill
- Pre-populate: Draft output before asking, show for review only
- Compound: Combine with [related skill] output when both would be triggered
```

### Combo Skills (Synergies)

When two skills in different branches are both at Level 2+, a compound skill becomes available. Compound skills are auto-generated definitions stored in `sidekick/progression/compounds/`.

**Compound skill definitions:**

| Compound Skill       | Required Skills                                             | What It Does                                                                                                 |
| -------------------- | ----------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------ |
| meeting-to-update    | transcript-miner L2 + weekly-update L2                      | Processes meeting, routes to memory, AND adds relevant items to the next weekly update draft automatically   |
| decision-impact      | decision-log L2 + context-refresh L2                        | When logging a decision, automatically checks impact on priorities, projects, and tracked assumptions        |
| follow-up-engine     | meeting-processor L2 + email-drafter L2                     | After processing a meeting, auto-drafts follow-up emails for each action item assigned to others             |
| priority-realignment | context-refresh L2 + decision-log L2 + 10 decisions logged  | Detects when accumulated decisions have drifted the user's actual work away from stated priorities           |
| stakeholder-brief    | transcript-miner L2 + email-drafter L2 + stakeholder-map L1 | After a key meeting, generates stakeholder-specific update emails with appropriate detail level per audience |
| pattern-advisor      | self-correct L3 + context-refresh L2                        | Identifies recurring correction patterns and proactively suggests systemic fixes                             |

**Compound skill file format** (`sidekick/progression/compounds/meeting-to-update.md`):

```markdown
# meeting-to-update

Compound skill. Auto-generated when transcript-miner reached L2 and weekly-update reached L2.

## What This Does

After processing a meeting transcript, automatically stages relevant items for the next weekly update:

- Decisions made -> "Decisions" section
- Action items completed -> "Completed" section
- New blockers -> "Blocked" section
- Priority-relevant activity -> "Progress" section under the relevant priority

## Process

1. Run transcript-miner as normal
2. After memory routing (Step 7), also write to `sidekick/outputs/weekly-staging.md`
3. On next weekly-update trigger, read weekly-staging.md to pre-populate the draft
4. Clear weekly-staging.md after the update is sent

## Unlock Date

2026-03-15

## Usage Count

0
```

---

## 3. Autonomy Ladder

### The Four Levels

Autonomy is separate from skill levels. It's a global setting that governs how much Sidekick does without asking. A skill can be Level 3 (Anticipatory) but the autonomy ladder can still be at Level 2 (Supervised), meaning the skill will proactively prepare output but always show it before acting.

```
Level 1: GUARDIAN     - Ask permission for everything. Default for new users.
Level 2: SUPERVISED   - Act on low-stakes items. Ask for medium and high-stakes. Default after week 2.
Level 3: TRUSTED      - Handle most things. Ask only for novel situations or high-stakes actions.
Level 4: AUTONOMOUS   - Full operation with exception-based alerts. User opts in explicitly.
```

### Autonomy State File

`sidekick/progression/autonomy.md`:

```markdown
# Autonomy Level

Current: Level 2 (Supervised)
Since: 2026-03-01
Promoted from: Level 1 on 2026-03-01 (auto, after 7 days + 10 interactions)

## Level History

| Date       | From | To  | Reason                                                       |
| ---------- | ---- | --- | ------------------------------------------------------------ |
| 2026-02-22 | -    | L1  | Initial setup                                                |
| 2026-03-01 | L1   | L2  | Auto-promoted: 7+ days, 10+ interactions, 0 trust violations |

## Category Overrides

| Category     | Override      | Reason                         | Since      |
| ------------ | ------------- | ------------------------------ | ---------- |
| People/Roles | Confirm-first | 6 corrections in this category | 2026-03-10 |
| Glossary     | Silent        | 0 corrections ever             | 2026-02-22 |

## Safety Record

| Metric                           | Value |
| -------------------------------- | ----- |
| Total interactions               | 47    |
| Trust violations                 | 0     |
| User overrides ("don't do that") | 2     |
| Successful autonomous actions    | 31    |
| Approval rate on shown drafts    | 89%   |
```

### Promotion/Demotion Conditions

| Transition | Conditions                                                                                    | Can Be Automatic?               |
| ---------- | --------------------------------------------------------------------------------------------- | ------------------------------- |
| L1 -> L2   | 7+ days active, 10+ interactions, 0 trust violations                                          | Yes                             |
| L2 -> L3   | 30+ days active, 50+ interactions, approval rate > 85%, user has never said "stop doing that" | Yes, with one-time notification |
| L3 -> L4   | User explicitly says "give me full autonomy" or "stop asking me about routine stuff"          | No, user must request           |
| Any -> L1  | User says "ask me before doing anything" or 3+ trust violations in 7 days                     | Immediate                       |
| Ln -> Ln-1 | User says "you're doing too much" or "check with me first"                                    | Immediate                       |

### What Each Level Permits

| Action                  | L1 Guardian | L2 Supervised                 | L3 Trusted | L4 Autonomous                 |
| ----------------------- | ----------- | ----------------------------- | ---------- | ----------------------------- |
| Add glossary term       | Ask         | Silent                        | Silent     | Silent                        |
| Add person to directory | Ask         | Silent                        | Silent     | Silent                        |
| Log correction          | Ask         | Brief                         | Silent     | Silent                        |
| Log decision            | Ask         | Brief                         | Silent     | Silent                        |
| Create project file     | Ask         | Brief                         | Silent     | Silent                        |
| Update priorities       | Confirm     | Confirm                       | Brief      | Brief                         |
| Draft email             | Show draft  | Show draft                    | Show draft | Show draft + "sent to drafts" |
| Trigger proactive skill | Never       | Suggest                       | Do + show  | Do + notify                   |
| Chain skills            | Ask         | Ask first time, auto after 3x | Auto       | Auto                          |
| Update CLAUDE.md        | Confirm     | Confirm                       | Brief      | Brief                         |
| Run scheduled tasks     | N/A         | Show output                   | Run + show | Run + file                    |

### Safety Rails

These apply at ALL autonomy levels, cannot be overridden:

1. **Never send external communications.** Emails, Slack messages, etc. always require explicit approval regardless of autonomy level.
2. **Never delete files.** Archiving is fine, deletion requires confirmation.
3. **Never modify someone else's work.** PRs, shared docs, etc.
4. **Always show the diff for CLAUDE.md changes.** This file controls Sidekick's behavior; changes are always high-stakes.
5. **Trust violations reset the category.** If the user says "don't do that" about a specific autonomous action, that category drops to confirm-first regardless of global autonomy level.
6. **3-strike demotion.** 3 trust violations in 7 days demotes the global level by 1.

### User Controls

The user adjusts autonomy through natural language:

| User Says                                               | Effect                                     |
| ------------------------------------------------------- | ------------------------------------------ |
| "Ask me before doing anything"                          | Set to L1                                  |
| "You don't need to ask about small stuff"               | Set to L2                                  |
| "I trust you, just flag important things"               | Set to L3                                  |
| "Full autopilot" / "stop asking me about routine stuff" | Set to L4                                  |
| "Check with me about [category]"                        | Category override to confirm-first         |
| "Stop doing [specific thing] automatically"             | Category override + trust violation logged |
| "You can handle [category] without asking"              | Category override to silent                |

---

## 4. Self-Organization Mechanics

### Pattern Detection Engine

Beyond the existing 5-correction pattern detection, the skill tree adds broader pattern recognition stored in `sidekick/progression/patterns.md`:

```markdown
# Detected Patterns

## Workflow Patterns

| Pattern                    | Evidence                                              | Suggested Action                             | Status                    |
| -------------------------- | ----------------------------------------------------- | -------------------------------------------- | ------------------------- |
| Monday meeting-heavy       | 8/8 Mondays had 4+ meetings                           | Pre-run meeting-processor on Monday mornings | Suggested, user accepted  |
| Friday update routine      | User asks for weekly-update every Friday 3-5pm        | Schedule proactive trigger                   | Active                    |
| Post-meeting email pattern | 6/10 meeting-processor runs followed by email-drafter | Create compound skill: follow-up-engine      | Pending user confirmation |

## Content Patterns

| Pattern                                 | Evidence                                   | Applied To                                         |
| --------------------------------------- | ------------------------------------------ | -------------------------------------------------- |
| Emails to Nathan are always <100 words  | 9/9 emails                                 | email-drafter recipient model                      |
| Weekly updates emphasize blockers first | User moved Blocked section first 4/6 times | weekly-update template order                       |
| Meeting notes skip competitive signals  | User deleted competitor section 3/4 times  | transcript-miner: de-prioritize competitor section |

## Anti-Patterns (Things NOT to Do)

| Pattern                             | Evidence                        | Rule                    |
| ----------------------------------- | ------------------------------- | ----------------------- |
| Don't suggest OKRs                  | User declined OKR skill 3 times | Remove from suggestions |
| Don't auto-chain to context-refresh | User skipped chain 5/5 times    | Disable auto-chain      |
```

### Skill Splitting

When a skill's usage log shows distinct use cases, suggest splitting:

**Detection signal:** The same skill gets invoked with qualitatively different inputs that produce qualitatively different outputs.

**Example:** `meeting-processor` gets used for:

- Quick 1:1 follow-ups (short, informal, action-item focused)
- All-hands summaries (long, formal, decision-focused)
- Client call notes (external-facing, diplomatic tone)

**Action:** Suggest specialization:

```
"I notice you use meeting-processor differently for 1:1s vs all-hands vs client calls.
Want me to create specialized versions? They'd share the base process but have
different defaults for tone, detail level, and output format."
```

If accepted, create `meeting-processor-1on1.md`, `meeting-processor-allhands.md`, `meeting-processor-client.md` as lightweight wrappers that set defaults before calling the base skill.

### Skill Merging

When two skills consistently chain together (>80% of uses), suggest merging:

**Detection signal:** Skill A chains to Skill B in 8+ out of 10 recent uses.

**Action:** Create a compound skill that runs both in sequence, present intermediate results but don't pause between them.

### Emergent Skill Detection

When the user repeatedly asks Sidekick to do something that no existing skill covers, detect the pattern and suggest creating a new skill.

**Detection signal:** 3+ conversations where the user describes a multi-step workflow that doesn't match any existing skill.

**Tracked in** `sidekick/progression/skill-requests.md`:

```markdown
# Skill Requests (Auto-Detected)

| Request Pattern                                    | Occurrences | Similar To                        | Suggested Skill     |
| -------------------------------------------------- | ----------- | --------------------------------- | ------------------- |
| "Summarize this Slack thread and draft a response" | 4           | meeting-processor + email-drafter | thread-responder    |
| "Compare these two proposals"                      | 3           | (none)                            | proposal-comparator |
| "Prep me for this call with [person]"              | 5           | meeting-prep + stakeholder-map    | call-prep           |

## Auto-Generated Skill Drafts

### thread-responder (draft)

Based on 4 observed uses. Would combine Slack thread summarization with response drafting.
Status: Awaiting user confirmation to create SKILL.md
```

---

## 5. Compound Learning

### The Learning Graph

Every interaction doesn't just improve one skill. It feeds into a shared knowledge base that all skills draw from.

```
┌─────────────────────────────────────────────────────────────────┐
│                    USER MODEL                                    │
│                                                                  │
│  ┌─────────────┐  ┌──────────────┐  ┌────────────────────────┐  │
│  │ Voice Model │  │ People Model │  │ Priority Model         │  │
│  │             │  │              │  │                        │  │
│  │ tone,       │  │ relationships│  │ stated vs actual,      │  │
│  │ vocabulary, │  │ formality    │  │ drift detection,       │  │
│  │ structure,  │  │ per person,  │  │ emerging themes        │  │
│  │ corrections │  │ influence    │  │                        │  │
│  └──────┬──────┘  └──────┬───────┘  └───────────┬────────────┘  │
│         │               │                       │               │
│         ▼               ▼                       ▼               │
│  ┌──────────────────────────────────────────────────────────┐   │
│  │              PATTERN MEMORY                              │   │
│  │                                                          │   │
│  │  workflow patterns, timing preferences, correction       │   │
│  │  history, decision patterns, communication preferences   │   │
│  └──────────────────────────────────────────────────────────┘   │
└─────────────────────────────────────────────────────────────────┘
         │              │                    │
         ▼              ▼                    ▼
    every skill    every skill          every skill
    reads voice    reads people         reads priorities
```

### Cross-Skill Learning

Specific mechanisms for how skills make each other smarter:

| Learning Source                      | What's Learned                             | Benefits Which Skills                                                             |
| ------------------------------------ | ------------------------------------------ | --------------------------------------------------------------------------------- |
| email-drafter corrections            | Vocabulary preferences, tone calibration   | weekly-update, status-report, any Produce skill                                   |
| transcript-miner decisions           | Decision-making patterns, who decides what | pre-mortem, stakeholder-map, priority-realignment                                 |
| self-correct patterns                | Where knowledge gaps exist                 | context-refresh (knows where to focus), all skills (confidence calibration)       |
| weekly-update edits                  | What the user considers important vs noise | transcript-miner (signal prioritization), meeting-processor (relevance filtering) |
| meeting-processor recipient patterns | Who needs to know what                     | email-drafter (audience model), stakeholder-map                                   |
| context-refresh changes              | Rate of change per domain                  | decay model calibration (how fast different categories go stale)                  |

### User Model Refinement

The user model is not a single file. It's distributed across existing files but tracked holistically in `sidekick/progression/user-model.md`:

```markdown
# User Model

## Voice Profile

Source: sidekick/context/communication-style.md
Last calibration: 2026-03-14 (from 3 email corrections)
Accuracy estimate: 87% (based on approval rate of Produce skills)

## Relationship Map

Source: sidekick/context/team-directory.md + observed interactions
Key insight: User communicates differently with Nathan (concise, outcome-focused) vs team (warmer, context-rich)
Formality gradient: Nathan > stakeholders > team > direct reports

## Work Rhythm

Derived from: calendar + usage-log.md timestamps

- Most active: 9-11am, 2-4pm
- Meeting-heavy: Monday, Wednesday
- Deep work: Tuesday, Thursday morning
- Update time: Friday 3-5pm
- Low activity: Friday morning

## Decision Style

Derived from: decisions.md + transcript-miner outputs

- Prefers data over intuition (8/10 decisions cite numbers)
- Decides quickly on operational matters (<1 day)
- Deliberates on strategic matters (3-5 days, usually after sleeping on it)
- Seeks Nathan's input on anything customer-facing

## Priority Behavior

Derived from: priorities vs actual activity (context-refresh comparisons)

- Stated priorities match actual work ~70% of the time
- Recurring drift toward [area] despite not listing it as a priority
- Tends to underestimate time spent on people management
```

### Insight Detection ("Aha Moments")

The system watches for moments where accumulated data crosses a threshold and produces a non-obvious insight. These are stored in `sidekick/progression/insights.md` and surfaced once at a natural moment.

**Insight triggers:**

| Trigger                | Minimum Data Required                     | Example Insight                                                                                                                         |
| ---------------------- | ----------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------- |
| Priority drift         | 3+ context refreshes showing same drift   | "You've spent 40% of your time on [X] the last 3 weeks, but it's not in your priorities. Should it be?"                                 |
| Decision contradiction | 2+ decisions that contradict each other   | "Decision D-12 (expand to UAE) conflicts with D-18 (focus on US market). Want to reconcile?"                                            |
| Relationship pattern   | 10+ interactions with same person tracked | "Your meetings with Nathan consistently produce 3x more action items than other meetings. Might be worth shorter, more frequent syncs." |
| Skill gap              | 3+ failed/corrected attempts in same area | "I keep getting [domain] wrong. This might be an area where I need more context. Can you tell me more about [specific gap]?"            |
| Workflow inefficiency  | Usage log shows repeated manual work      | "You've manually copied meeting notes to your weekly update 6 times. Want me to automate that link?"                                    |

**Surfacing rules:**

- Maximum 1 insight per session
- Never interrupt task-focused work with an insight
- Best time: end of a skill chain, or when user asks "anything else?"
- Mark insights as shown so they don't repeat
- Track whether the user found the insight useful (did they act on it?)

---

## 6. Implementation

### File Structure

```
sidekick/
  progression/                        # NEW directory
    skill-tree.md                     # Skill levels and branch status
    usage-log.md                      # Append-only skill invocation log
    autonomy.md                       # Current autonomy level + history
    patterns.md                       # Detected workflow/content/anti-patterns
    user-model.md                     # Holistic user understanding
    insights.md                       # Detected insights + surfacing log
    skill-requests.md                 # Emergent skill detection
    compounds/                        # Auto-generated compound skill definitions
      meeting-to-update.md
      follow-up-engine.md
  context/                            # EXISTING - unchanged
  memory/                             # EXISTING - unchanged
  outputs/                            # EXISTING - unchanged
```

**Token budget impact:** The progression directory adds ~2-3k tokens of always-loaded context (skill-tree.md summary) plus on-demand reads. This is manageable within the existing budget.

### Changes to CLAUDE.md

The CLAUDE.md template gains a new section after `## Capability Progression`:

```markdown
## Skill Tree

Sidekick's capabilities deepen with use. Read `sidekick/progression/skill-tree.md` for current levels.

When triggering a skill:

1. Read the SKILL.md file
2. Check skill level in `sidekick/progression/skill-tree.md`
3. Apply level modifiers (L1: follow exactly, L2: skip known steps, L3: proactive + pre-populated)
4. After completion, append to `sidekick/progression/usage-log.md`
5. Check level-up conditions

### Autonomy

Current level is tracked in `sidekick/progression/autonomy.md`. Read it at session start.

| Level | Name       | Rule                                      |
| ----- | ---------- | ----------------------------------------- |
| 1     | Guardian   | Ask permission for everything             |
| 2     | Supervised | Low-stakes: silent. Medium+: ask.         |
| 3     | Trusted    | Most things: act. Novel/high-stakes: ask. |
| 4     | Autonomous | Act on everything. Alert on exceptions.   |

Never exceed the current autonomy level. User can adjust with natural language ("ask me first", "I trust you", etc.)

### Compound Skills

When 2+ skills in different branches reach Level 2, check `sidekick/progression/compounds/` for available compound skills. Compound skills combine two workflows into one pass.

### Pattern Learning

After every 10th skill invocation, scan `sidekick/progression/usage-log.md` for:

- Skills that always chain together (>80%) -> suggest compound
- Skills the user never completes -> suggest removal or modification
- Repeated requests with no matching skill -> suggest new skill creation
- Output sections the user always deletes -> stop including them
```

### Token Budget Strategy

The progression system adds context. Here's how to keep it within budget:

| Component                         | Tokens        | When Loaded                                         |
| --------------------------------- | ------------- | --------------------------------------------------- |
| Skill tree summary (in CLAUDE.md) | ~300          | Always (part of CLAUDE.md)                          |
| skill-tree.md full state          | ~500-800      | On skill trigger (to check level)                   |
| usage-log.md                      | ~50 per entry | Only last 10 entries loaded (for pattern detection) |
| autonomy.md                       | ~200          | Session start                                       |
| patterns.md                       | ~300-500      | On skill trigger (to apply learned patterns)        |
| user-model.md                     | ~400          | On Produce skills (need voice/relationship data)    |
| insights.md                       | ~200          | End of skill chains (to check for surfacing)        |
| compound skill file               | ~200 each     | On compound skill trigger                           |

**Worst case per interaction:** ~2,000 additional tokens. Typical: ~800 (skill-tree.md + autonomy.md).

**Comparison:** Current system loads ~6,000 tokens per interaction. Progression adds ~800-2,000 for a total of ~7,000-8,000. Still well under the theoretical maximum of loading all skills (~80,000).

### Backward Compatibility

The progression system is fully backward compatible:

1. **No `sidekick/progression/` directory = flat mode.** All skills run at L1, autonomy is L1, no compound skills. Identical to current behavior.
2. **Existing SKILL.md files are unchanged.** Level modifiers are an optional section. Skills without modifiers always run at L1 behavior.
3. **Existing CLAUDE.md works as-is.** The skill tree section is additive. Old CLAUDE.md files without it just skip progression checks.
4. **Migration is automatic.** On first interaction after upgrade, create `sidekick/progression/` with default values. No user action required.

### Initialization

When `sidekick/progression/` doesn't exist but `sidekick/` does (existing user upgrading):

1. Create `sidekick/progression/skill-tree.md` with all existing skills at L1
2. Create `sidekick/progression/autonomy.md` at L2 (existing users have already built basic trust)
3. Create empty `sidekick/progression/usage-log.md`
4. Create empty `sidekick/progression/patterns.md`, `user-model.md`, `insights.md`
5. Brief notification: "I've added a progression system. I'll get better at your workflow over time. Say 'show my skill tree' anytime to see how things are developing."

For new users (running onboarding for the first time): create `sidekick/progression/` as part of Step 3 workspace build. All skills start at L1, autonomy at L1.

### The Progression Check (Runtime Logic)

Added to the skill trigger flow. This is the core runtime addition:

```
ON SKILL TRIGGER:
  1. Which skill? -> read SKILL.md
  2. What level? -> read skill-tree.md, find the skill's row
  3. What autonomy? -> read autonomy.md for current level + category overrides
  4. Apply level modifiers:
     - L1: Execute SKILL.md steps 1-N exactly as written
     - L2: Skip steps tagged "skippable at L2", apply defaults from patterns.md
     - L3: Pre-populate output from user-model.md, show for review only
  5. Execute skill
  6. Log result to usage-log.md:
     - Append: date, skill, outcome (approved/edited/rejected), corrections count
  7. Check level-up:
     - Count uses in usage-log.md
     - Check correction rate in last N uses
     - If conditions met: increment level in skill-tree.md, notify user briefly
  8. Check compound unlocks:
     - If this skill just hit L2: scan other L2+ skills in different branches
     - If a compound becomes available: add to unlock queue in skill-tree.md
  9. Every 10th invocation: run pattern scan on usage-log.md
     - Detect chains, anti-patterns, emergent skills
     - Update patterns.md
```

### Edge Cases

| Situation                                       | Handling                                                                                                                                 |
| ----------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------- |
| User asks to reset a skill level                | Set it back to L1 in skill-tree.md. Don't clear usage-log (historical data).                                                             |
| User never uses a skill after install           | After 30 days unused, move to "Dormant" in skill-tree.md. Don't suggest it proactively. Don't delete.                                    |
| Skill pack uninstalled                          | Mark all pack skills as "Uninstalled" in skill-tree.md. Preserve level data in case of reinstall.                                        |
| User has two Sidekick workspaces                | Each workspace has its own `sidekick/progression/`. No cross-workspace syncing.                                                          |
| Correction rate spikes on a high-level skill    | Demote the skill by 1 level. Notify: "My [skill] output has been off lately. I'm dialing back to get more input from you."               |
| Token budget exceeded                           | Drop user-model.md and patterns.md from context first (least critical). Then drop usage-log.md. Never drop skill-tree.md or autonomy.md. |
| User explicitly says "don't level up my skills" | Set `progression_paused: true` in skill-tree.md. All skills stay at current level.                                                       |

---

## Summary

| System            | Storage           | Token Cost                | User Visible?                         |
| ----------------- | ----------------- | ------------------------- | ------------------------------------- |
| Skill Tree        | skill-tree.md     | ~500-800 on trigger       | On request ("show my skill tree")     |
| Usage Tracking    | usage-log.md      | ~50/entry, last 10 loaded | No                                    |
| Autonomy Ladder   | autonomy.md       | ~200 at session start     | On request + natural language control |
| Pattern Detection | patterns.md       | ~300-500 on trigger       | Surfaced as suggestions               |
| User Model        | user-model.md     | ~400 on Produce skills    | No (feeds into output quality)        |
| Insights          | insights.md       | ~200 at chain end         | 1 per session max, at natural pause   |
| Compound Skills   | compounds/\*.md   | ~200 per compound         | On unlock notification                |
| Emergent Skills   | skill-requests.md | ~200 on pattern scan      | Surfaced as suggestions               |

**Total system overhead:** ~800-2,000 tokens per interaction (from current ~6,000 to ~7,000-8,000).

**Key design principle:** The user never thinks about progression. They just work. Sidekick gets better. The skill tree is available for inspection but never demands attention. Zero configuration, automatic promotion, natural language control for everything.
