---
name: skill-suggester
description: "Map any user request to the best matching skill or skill chain. Suggest uninstalled packs when a gap exists. Trigger when the user says 'what skills do I have', 'what can you do', 'help me find the right skill', or 'I don't know which skill'."
---

# Skill Suggester

Advisory skill for navigating the full capability set. Maps what you're trying to do to the best skill or chain - including skills from packs you haven't installed yet.

## Process

### Step 1: Load Context

Read these files:

- `CLAUDE.md` - The current Skills table (installed skills only)

Also read these INDEX files to know what's available but not yet installed:

- `skill-packs/product-management/INDEX.md` (if it exists)
- `skill-packs/engineering/INDEX.md` (if it exists)
- `skill-packs/automation/INDEX.md` (if it exists)
- `skill-packs/design/INDEX.md` (if it exists)
- `skill-packs/people-management/INDEX.md` (if it exists)
- `skill-packs/content-creation/INDEX.md` (if it exists)
- `skill-packs/strategy-planning/INDEX.md` (if it exists)
- `skill-packs/meta-system/INDEX.md` (if it exists)

### Step 2: Understand the Request

If the user hasn't described what they're trying to do, ask: "What are you trying to accomplish?"

Otherwise, parse the request directly. Identify: the task type, the output they want, and any constraints they've mentioned.

### Step 3: Match to Skills

**Installed skills:** Check the CLAUDE.md Skills table for exact and approximate matches.

**Uninstalled skills:** Check all INDEX files for skills that would fit even if not yet installed.

**Chains:** If the task spans multiple skills, identify the sequence.

### Step 4: Present the Recommendation

```markdown
## Skill Match: [Request Summary]

### Best match

**[Skill name]** - [one-sentence description of what it does]
[Installed / Needs install from: [pack name]]

Trigger phrase to use: "[exact trigger phrase]"

### Alternative

**[Skill name]** - [description]
[Installed / Needs install]

### If you need multiple steps

1. Start with [skill]: [why]
2. Then [skill]: [why]

### Gap (if applicable)

The closest available skill is [name], but it doesn't cover [specific gap]. The [pack name] pack would add [skill] which handles this.
```

This skill does not write to any files. Advisory only.

## After This Skill

| If...                                                               | Suggest...                                                              |
| ------------------------------------------------------------------- | ----------------------------------------------------------------------- |
| The user wants to install a suggested pack                          | Read the suggested pack's INDEX.md and append to CLAUDE.md Skills table |
| The user wants to automate a recurring version of the matched skill | Read `skill-packs/meta-system/skills/meta-workflow-builder.md`          |

## Rules

- Only recommend skills that exist in the Skills table or in an INDEX file you've read. Never invent skills.
- If nothing matches well, say so. A poor match is worse than no match.
- Always distinguish between installed and uninstalled skills in the recommendation.
- Never fabricate. If you can't find it, say so.
