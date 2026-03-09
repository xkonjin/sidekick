---
name: self-correct
description: "Automatically triggers when the user corrects any factual claim. Detects phrases like 'that's wrong', 'actually', 'no, it's', 'update that', 'not anymore', or any contradiction of stored information. Also triggers when the user says something that conflicts with what's in memory files. NEVER requires the user to say 'self-correct' explicitly. Works with natural speech including voice dictation corrections like 'wait, I meant...' or 'sorry, that's not right'."
---

# Self-Correct

When the user corrects you, don't just acknowledge it. Fix it everywhere.

## Process

### Step 1: Acknowledge and Clarify

- Repeat back the correction to confirm understanding
- If the correction is ambiguous, ask one clarifying question before proceeding
- Never argue, justify, or explain why the original error was made

### Step 2: Identify Scope

Determine what type of correction this is:

| Category                | Examples                                            | Files to Check                                                                                                                    |
| ----------------------- | --------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| **People/Roles**        | Wrong title, wrong team, wrong relationship         | CLAUDE.md (People), sidekick/context/team-directory.md                                                                            |
| **Company/Strategy**    | Wrong product name, wrong timeline, wrong priority  | CLAUDE.md (Projects, Current Focus), sidekick/context/current-priorities.md, sidekick/memory/projects/                            |
| **Process/Preferences** | Wrong workflow, wrong preference, wrong banned word | CLAUDE.md (Preferences), sidekick/context/working-preferences.md (if exists), sidekick/context/communication-style.md (if exists) |
| **Terminology**         | Wrong acronym meaning, wrong internal term          | CLAUDE.md (Terms), sidekick/memory/glossary.md                                                                                    |
| **Decisions**           | Wrong decision attribution, wrong rationale         | sidekick/memory/decisions.md                                                                                                      |
| **Project**             | Wrong status, wrong owner, wrong deadline           | sidekick/memory/projects/\*.md                                                                                                    |

### Step 3: Search and Update

For the identified category, search ALL relevant files listed above:

1. Read each file
2. Search for the incorrect information
3. Update every occurrence with the correct information
4. Report what was changed and where

**Be thorough.** The same wrong fact can appear in multiple files. Check them all.

### Step 4: Log the Correction

If `sidekick/memory/confidence-flags.md` doesn't exist yet, create it from `skills/onboarding/references/confidence-flags-template.md` first.

Append to the Correction Log table:

```
| [TODAY'S DATE] | [What was wrong] | [What's actually true] | [Category] |
```

### Step 5: Pattern Detection

After logging, read the full Correction Log. If there are 5+ corrections in the same category:

1. Note the pattern in the Correction Patterns section
2. Identify the root cause (e.g., "Role inference errors: I keep guessing titles from context instead of asking")
3. Add a confidence flag: downgrade the entire category to require explicit confirmation before acting

**Example pattern entry:**

```
- **People/Roles errors (6)**: Inferring titles from meeting context instead of confirmed sources. New rule: treat all role information as MEDIUM confidence unless user-confirmed.
```

## After This Skill

| If...                               | Suggest...                                                                                                         |
| ----------------------------------- | ------------------------------------------------------------------------------------------------------------------ |
| 5+ corrections in same category     | "I keep getting [category] wrong. Want me to do a broader context check?" → Read `skills/context-refresh/SKILL.md` |
| Correction changes a priority       | "This affects your priorities." → Update `sidekick/context/current-priorities.md`                                  |
| Correction involves a person's role | Silently verify other entries about that person in team directory                                                  |
| Correction contradicts a decision   | "This conflicts with decision D-XXX." → Read `skills/decision-log/SKILL.md`                                        |

## Rules

- Never argue with a correction. Treat corrections as data.
- Always update the source files, not just your in-conversation understanding
- If a correction contradicts another stored fact, flag both and ask the user to resolve
- After updating, confirm what was changed: "Updated [file1], [file2]. The correction has been applied everywhere."
