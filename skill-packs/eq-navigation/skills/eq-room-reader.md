---
name: room-reader
description: "Post-meeting dynamics debrief: who was aligned, who was resistant, what wasn't said, and what to do next. Trigger when the user says 'how did that meeting go', 'read the room', 'what was the dynamic', or 'meeting debrief'."
---

# Room Reader

Analyses the human dynamics of a meeting after it ends. Works from a transcript if available, or from the user's recollection. Surfaces alignment, resistance, subtext, and next moves.

## Process

### Step 1: Load Context

- `sidekick/context/team-directory.md` - Role and relationship context for attendees
- `sidekick/memory/relationship-map.md` - Prior dynamic signals for recurring relationships (if it exists)
- Meeting transcript — ask the user to provide it if not already in context

### Step 2: Clarify What Happened

If a transcript is not provided, ask the user:

- Who was in the meeting and what was it about?
- What was decided or not decided?
- Who said what that stood out to you?
- Was anything left unsaid that you noticed?

Do not attempt to reconstruct dynamics from partial information. Ask rather than infer.

### Step 3: Build the Room Read

Follow the output format below.

### Step 4: Save Output

Write to `sidekick/outputs/room-read-[meeting]-[DATE].md`

If `sidekick/memory/relationship-map.md` already exists, append any new signals to it. Do not create it from scratch based on this one meeting alone.

## Output Format

```markdown
# Room Read: [Meeting Name]

**Date:** [DATE] | **Attendees:** [Names] | **Source:** Transcript / Recollection

## What Was Decided

- [Decision or outcome]
- [If nothing was decided, say so explicitly]

## Alignment Map

| Person | Stance                                  | Signal                                     | Confidence          |
| ------ | --------------------------------------- | ------------------------------------------ | ------------------- |
| [Name] | Aligned / Neutral / Resistant / Unclear | [What they said or did that suggests this] | High / Medium / Low |

## What Wasn't Said

[Observations about subtext, avoided topics, or body language (if recollection-based). Label all of this as interpretation, not fact.]

## Tensions to Watch

- [Dynamic or friction that surfaced or is building]

## What to Do Next

| Action      | Owner        | Why                 |
| ----------- | ------------ | ------------------- |
| [Follow-up] | [You / Name] | [What it addresses] |
```

## After This Skill

| Next skill       | When                                                          | How to load                                               |
| ---------------- | ------------------------------------------------------------- | --------------------------------------------------------- |
| transcript-miner | If the meeting transcript exists and warrants deeper analysis | Read `skills/transcript-miner/SKILL.md`                   |
| meeting-prep     | To prepare for the follow-up meeting with the same group      | Read `skill-packs/automation/skills/auto-meeting-prep.md` |

## Rules

- Surface assumptions. People situations have more unknowns than data problems.
- Never claim to know what someone was thinking or feeling. Use "may have been", "seemed to suggest", "this is an interpretation."
- Ask the user for context rather than inferring interpersonal dynamics from meeting notes alone.
- If working from recollection only, label the entire debrief as subjective and flag that it may not reflect others' experiences of the same meeting.
- Confidence levels on the alignment map are mandatory — do not omit them.
- Do not update relationship-map.md from a single data point without the user's awareness.
