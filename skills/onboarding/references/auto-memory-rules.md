# Automatic Memory Rules

How Sidekick captures and updates information without being told. These rules get embedded in the user's CLAUDE.md as compact behavioral instructions.

## Core Principle

Low-stakes updates happen silently. High-stakes updates get brief confirmation. Nothing requires the user to invoke a command.

## Auto-Capture Triggers

| Signal                                       | Action                                                | Announce?                                            | Example                                                        |
| -------------------------------------------- | ----------------------------------------------------- | ---------------------------------------------------- | -------------------------------------------------------------- |
| User uses unfamiliar acronym and explains it | Add to `sidekick/memory/glossary.md`                  | No                                                   | "The OKR (that's our quarterly planning thing) needs updating" |
| User mentions new person with context        | Add to `sidekick/context/team-directory.md`           | No                                                   | "Sarah from engineering said the API is ready"                 |
| User corrects a fact                         | Update all memory files + log to confidence-flags.md  | Brief: "Updated everywhere."                         | "Actually, Karen is on the product team, not marketing"        |
| User says "we decided X"                     | Add to `sidekick/memory/decisions.md`                 | Brief: "Logged."                                     | "We decided to push the launch to May"                         |
| User mentions new project                    | Create `sidekick/memory/projects/[name].md`           | Brief: "Tracking [project] now."                     | "The Athena project is ramping up"                             |
| Message contains a deadline                  | Note in relevant project or priority file             | No                                                   | "We need the deck by Friday"                                   |
| User changes a priority                      | Update `sidekick/context/current-priorities.md`       | Confirm: "Updating priority 2 from X to Y. Correct?" | "SEO isn't the focus anymore, it's partnerships"               |
| User mentions a competitor                   | Create/update `sidekick/memory/competitors/[name].md` | No                                                   | "Did you see what Etherfy launched?"                           |
| User expresses preference                    | Update `sidekick/context/working-preferences.md`      | Brief: "Noted."                                      | "Don't use bullet points in my emails"                         |

## File Creation Rules

Not all files exist from the start. Create them on first use:

| File                     | Created When                                           | Template                                                       |
| ------------------------ | ------------------------------------------------------ | -------------------------------------------------------------- |
| `communication-style.md` | First time user asks Sidekick to draft/write something | `skills/onboarding/references/communication-style-template.md` |
| `working-preferences.md` | First time user expresses a preference                 | `skills/onboarding/references/working-preferences-template.md` |
| `glossary.md`            | First unknown acronym encountered                      | `skills/onboarding/references/glossary-template.md`            |
| `decisions.md`           | First "we decided" signal                              | `skills/onboarding/references/decisions-template.md`           |
| `confidence-flags.md`    | First correction received                              | `skills/onboarding/references/confidence-flags-template.md`    |

## Confidence Escalation

| Confidence Level | Behavior          | Example                                              |
| ---------------- | ----------------- | ---------------------------------------------------- |
| Certain          | Act on it         | User explicitly stated the fact                      |
| Likely           | Mention naturally | "I think Karen handles that, but I could be wrong"   |
| Uncertain        | Ask before acting | "I'm not sure about the timeline. Want me to check?" |

No clinical labels (HIGH/MEDIUM/LOW) in conversation. Use natural language.

## When to Confirm vs Act Silently

**Act silently (low stakes, easily reversible):**

- Adding a glossary term
- Adding a new person to the team directory
- Noting a deadline
- Creating a competitor file

**Brief acknowledgment (medium stakes):**

- Logging a correction
- Recording a decision
- Noting a preference
- Tracking a new project

**Confirm before acting (high stakes, hard to reverse):**

- Changing priorities
- Updating someone's role
- Marking a decision as superseded
- Removing or archiving anything
