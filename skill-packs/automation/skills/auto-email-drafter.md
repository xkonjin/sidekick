---
name: email-drafter
description: "Draft context-aware emails matched to the user's actual tone and communication style. Trigger when the user says 'draft email', 'write email to', or 'email to [person]'. Never sends. Always shows draft for approval first."
---

# Email Drafter

Writes emails in your voice, not a generic template. Reads your communication patterns before writing a single word.

## Process

### Step 1: Load Context

Read these files before drafting:

- `sidekick/context/communication-style.md` - Your tone, vocabulary patterns, banned words, message structure (if it exists; if not, ask the user to describe their typical email tone before drafting)
- `sidekick/context/team-directory.md` - Context on the recipient if they're on your team
- `sidekick/context/current-priorities.md` - What's live right now (informs urgency and framing)
- `sidekick/context/working-preferences.md` - Formatting preferences, sign-off style (if it exists)

### Step 2: Clarify Intent

If the user hasn't specified, ask:

- Who is this going to? (Name or role)
- What is the purpose? (Request, update, follow-up, introduction, feedback)
- What's the desired outcome? (What should the recipient do or know after reading?)
- Any specific constraints? (Length, formality, deadline to mention)

Skip questions if the user's message already answers them.

### Step 3: Draft the Email

Apply communication-style.md strictly:

- Match formality level to the recipient relationship
- Use vocabulary patterns from the profile, avoid flagged words
- Mirror message structure preferences (how they open, close, structure requests)
- Apply formatting preferences (bullets vs prose, length tendency)

```
Subject: [Clear, specific subject line]

[Opening - matches their warmth and formality setting]

[Body - structured to match their typical request/update/feedback pattern]

[Close - matches their sign-off style]
```

### Step 4: Show for Approval

Present the draft and ask:

- "Does this sound like you?"
- "Anything to adjust before you send?"

Never send. Never save to outbox. The user copies and sends it themselves.

## Rules

- If communication-style.md doesn't exist, ask the user to describe their tone before drafting
- Surface any assumptions made (e.g., assumed formal tone because recipient is external)
- If the email involves a commitment or decision, flag it: "This commits you to X - confirm that's intentional"
- One draft per request. Don't offer multiple versions unless asked.
