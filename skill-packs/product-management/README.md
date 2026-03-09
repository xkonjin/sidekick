# Product Management Skill Pack

10 skills for the PM lifecycle: discovery, strategy, execution, and retrospectives.

## Skills

| Skill               | What it does                                                               |
| ------------------- | -------------------------------------------------------------------------- |
| create-prd          | Product requirements document: problem, scope, success metrics, edge cases |
| user-stories        | User stories with acceptance criteria and edge case coverage               |
| prioritize-features | Feature prioritization using RICE, ICE, or MoSCoW frameworks               |
| competitor-analysis | Structured competitive intelligence with evidence and implications         |
| brainstorm-okrs     | Objectives and key results with stress-testing and alignment checks        |
| sprint-plan         | Sprint planning: scope, capacity, commitments, risks                       |
| retro               | Retrospective: what went well, what didn't, action items                   |
| release-notes       | User-facing release notes matched to your voice                            |
| pre-mortem          | Pre-mortem: what could go wrong, likelihood, mitigation                    |
| stakeholder-map     | Stakeholder mapping: influence, interest, communication needs              |

## Install

Say "add the product management skills" during any conversation, or manually:

1. Open your `CLAUDE.md`
2. Find the `## Skills` table
3. Append the contents of `INDEX.md` to the table
4. Skill files in `skill-packs/product-management/skills/` load on-demand

## How it works

The trigger table in `INDEX.md` is all that lives in CLAUDE.md. When your intent matches a trigger phrase, Sidekick reads the relevant skill file on-demand. No context bloat.

These skills read `sidekick/context/current-priorities.md`, `sidekick/context/team-directory.md`, and `sidekick/context/communication-style.md` (if it exists) before producing output.
