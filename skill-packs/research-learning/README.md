# Research & Learning Skill Pack

5 skills for structured research, reading digests, knowledge persistence, learning plans, and cross-topic insight connection.

## Skills

| Skill             | What it does                                                                     |
| ----------------- | -------------------------------------------------------------------------------- |
| research-brief    | Structured research framing: question decomposition, known facts, open questions |
| reading-digest    | Long-form content digest: thesis, findings, implications, action items           |
| knowledge-base    | Knowledge persistence: indexed entries with tags, source, relevance, key insight |
| learning-plan     | Learning path: milestones, resources, practice exercises, time estimates         |
| insight-connector | Cross-topic synthesis: non-obvious connections between topics with evidence      |

## Install

Say "add the research and learning skills" during any conversation, or manually:

1. Open your `CLAUDE.md`
2. Find the `## Skills` table
3. Append the contents of `INDEX.md` to the table
4. Skill files in `skill-packs/research-learning/skills/` load on-demand

## How it works

The trigger table in `INDEX.md` is all that lives in CLAUDE.md. When your intent matches a trigger phrase, Sidekick reads the relevant skill file on-demand. No context bloat.

These skills read `sidekick/context/current-priorities.md`, `sidekick/memory/knowledge/` (if it exists), and `sidekick/context/about-me.md` before producing output.
