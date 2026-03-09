# Recurring Prompts Library

Ready-to-use prompts for common tasks. Copy and customize, or use as-is.

---

## Meeting Follow-Up

> Process my last meeting. Give me the summary, decisions, action items, and anything I need to follow up on.

Works with: Granola, Otter, Fireflies, or any connected meeting notes tool.

## Research Brief

> Brief me on [COMPANY/TOPIC]. I need: what they do, recent news, why it matters to us, and any contacts we have.

Works with: Web search, CRM (if connected), messaging history.

## Document Review

> Review this document against my communication style. Flag anything that doesn't sound like me, uses banned words, or doesn't match my preferences.

Requires: `sidekick/context/communication-style.md` to be populated.

## Team Update Prep

> Prep my update for [MEETING_NAME]. What have I accomplished since the last one? What's blocked? What should I raise?

Works with: Calendar, meeting notes, messaging, TASKS.md.

## Blocker Audit

> Check my tasks and priorities for anything that's been stuck for 3+ days. Who or what is blocking each one? What's the recommended escalation?

Works with: `sidekick/TASKS.md`, `sidekick/context/current-priorities.md`, messaging.

## Priority Drift Check

> Compare what I've actually been doing this week (meetings, messages, tasks) against my stated priorities. Am I focused or drifting?

Works with: Calendar, messaging, `sidekick/context/current-priorities.md`.

## Decision Recall

> What did we decide about [TOPIC]? When was it decided, who was involved, and what were the alternatives?

Works with: `sidekick/memory/decisions.md`, meeting notes if available.

## Competitor Check

> What do we know about [COMPETITOR]? Update their profile with anything new from the past month.

Works with: Web search, messaging, `sidekick/memory/competitors/`.

## End-of-Day Quick Check

> Quick check: anything I missed today? Unread messages that need responses, action items I haven't acknowledged, or meetings I need to prep for tomorrow.

Works with: Calendar, messaging, meeting notes.

## New Person Context

> I'm meeting with [NAME] for the first time. What do I know about them? Check CRM, Slack history, meeting notes, and any shared connections.

Works with: CRM, messaging, meeting notes, team directory.

---

## Customization

All prompts reference your Sidekick context files automatically. The more complete your `sidekick/context/` and `sidekick/memory/` files are, the better these prompts perform.

To add your own recurring prompts, add them to this file or create a new file in `sidekick/context/`.
