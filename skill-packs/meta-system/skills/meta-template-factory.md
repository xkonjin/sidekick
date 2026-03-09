---
name: meta-template-factory
description: "Extract any output into a reusable template saved to your sidekick. Trigger when the user says 'make a template', 'save this as a template', 'I do this every time', or 'standardize this'."
---

# Template Factory

Turns an output you liked into a reusable template. Captures the structure, placeholders, and voice so the same format can be reproduced on demand.

## Process

### Step 1: Load Context

Read these files:

- `sidekick/context/communication-style.md` - Preserve the user's voice in the template (if it exists)

### Step 2: Identify the Template Source

If not specified, ask:

- Which output should become a template? (paste it or describe it)
- What should be variable each time? (e.g., names, dates, topics)
- What should stay fixed? (structure, section headers, tone)

Skip questions if the user has already provided the output to templatize.

### Step 3: Extract the Template

**Replace variable content** with clear placeholders in brackets: `[DATE]`, `[TOPIC]`, `[PERSON NAME]`.

**Keep fixed structure** intact: headers, table shapes, ordering, tone.

**Add a header comment** noting which skill produced the original output, so future users know where it came from.

```markdown
<!-- Template: [template-name] -->
<!-- Source skill: [skill that generated the original output] -->
<!-- Created: [date] -->

[Full template with [PLACEHOLDER] substitutions for variable fields]
```

### Step 4: Save the Template

Save to `sidekick/templates/[name].md`.

If `sidekick/templates/` doesn't exist, create the directory by saving the first file there.

Present the saved template path and confirm with the user.

## After This Skill

| If... | Suggest... |
|-------|-----------|
| The user wants to run the source skill again | Return to the skill that generated the original output |
| The template needs a workflow to auto-populate it | Read `skill-packs/meta-system/skills/meta-workflow-builder.md` |

## Rules

- Preserve the user's voice. Don't rewrite sections - only replace variable content with placeholders.
- Note the source skill in the header comment. Templates detached from their source skill become hard to maintain.
- If the output has no recurring structure worth templating, say so. Not everything needs a template.
- Never fabricate. If you can't find it, say so.
