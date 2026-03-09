# Skill Authoring Guide

How to create custom skills for Sidekick.

## File Format

Every skill lives in its own directory under `skills/` or `skill-packs/[pack]/skills/`:

```
skills/
  my-skill/
    SKILL.md       <- The skill definition
```

### SKILL.md Structure

```markdown
---
name: my-skill
description: "When to trigger this skill. Include exact phrases users might say."
---

# Skill Name

[One sentence: what this skill does.]

## Process

### Step 1: Load Context

[Which sidekick/context/ and sidekick/memory/ files to read]

### Step 2: [Main Action]

[What to do, step by step]

### Step 3: Generate Output

[Output format template]

### Step 4: [Save/Route]

[Where to save output, what memory files to update]

## After This Skill

[Suggest the next relevant skill based on what was found]

| If...                   | Suggest...           |
| ----------------------- | -------------------- |
| [Condition from output] | [Next skill and why] |

## Rules

[Constraints, guardrails, things to never do]
```

## Key Principles

### 1. Always Read Context Files

Every skill should start by reading relevant context:

```markdown
### Step 1: Load Context

Read these files before proceeding:

- `sidekick/context/current-priorities.md` - Filter output through priorities
- `sidekick/context/communication-style.md` - Match output tone
- `sidekick/context/team-directory.md` - Understand who people are
```

Which files to read depends on the skill. At minimum, read `communication-style.md` if the skill generates any text output.

### 2. Never Hardcode Values

Bad:

```markdown
Search the #product and #engineering Slack channels.
```

Good:

```markdown
Search the channels listed in the user's CLAUDE.md or ask which channels to scan.
```

Skills must work for any user, not just the person who wrote them.

### 3. Graceful Degradation

Every skill should work even if some tools aren't connected:

```markdown
### Step 2: Gather Data

**If calendar is connected:** Pull this week's events.
**If not connected:** Ask the user for their meeting list.
```

A skill that fails when one tool is missing is poorly designed. Fall back to manual input.

### 4. Confirm Before Writing

Never modify memory files without showing the user what you're about to change:

```markdown
### Step 3: Confirm

Show the proposed changes. Ask: "Should I update these files?"
Only proceed after explicit confirmation.
```

### 5. Match Communication Style

If the skill generates user-facing text:

```markdown
Read `sidekick/context/communication-style.md` before generating output.
Match the user's tone, vocabulary, and message structure.
Never use words from their banned list.
```

### 6. Respect Confidence Levels

When a skill stores new information:

```markdown
Mark user-stated facts as HIGH confidence.
Mark inferences as MEDIUM confidence.
Mark guesses as LOW confidence with a note to verify.
```

## Description Field

The description in the frontmatter is critical. It controls when the skill triggers. Include:

- **Exact trigger phrases** users might say
- **Variations** of those phrases
- **When NOT to trigger** (if there's a similar skill)

Good:

```yaml
description: "Deep meeting transcript analysis. Trigger when: 'process meeting', 'mine transcript', 'deep dive on [meeting]'. For quick follow-ups, use meeting-processor instead."
```

Bad:

```yaml
description: "Analyzes meetings."
```

## Adding Skills to the Index

For skills to trigger automatically, they need an entry in the Skills Index section of CLAUDE.md:

```markdown
| my-skill | "trigger phrase 1", "trigger phrase 2" | skills/my-skill/SKILL.md |
```

Keep trigger phrases short and distinctive. Avoid overlap with existing skills.

## Testing Your Skill

1. Add the skill to the Skills Index in CLAUDE.md
2. Start a new conversation
3. Say one of the trigger phrases
4. Verify the skill loads and runs correctly
5. Check that context files are read properly
6. Verify output matches your communication style
7. Confirm memory file updates work as expected

## Common Patterns

### Read-Analyze-Present-Confirm-Write

Most skills follow this pattern:

1. Read context files and tool data
2. Analyze and classify information
3. Present findings to the user
4. Get explicit confirmation
5. Write to memory files

### Priority Impact Assessment

For skills that analyze incoming information:

```markdown
Assess each item against the user's current priorities:

- **Direct** - Directly affects a stated priority
- **Adjacent** - Affects something related to a priority
- **FYI** - Good to know but doesn't change anything
```

### Output Save Convention

```markdown
Save to `sidekick/outputs/[skill-name]-[YYYY-MM-DD].md`
```
