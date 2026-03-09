# Data & Analytics Skill Pack

5 skills for metric definition, experiment design, data storytelling, dashboard specs, and anomaly investigation.

## Skills

| Skill               | What it does                                                                     |
| ------------------- | -------------------------------------------------------------------------------- |
| metric-definer      | Rigorous metric spec: formula, data source, ownership, baseline, target, caveats |
| experiment-designer | Experiment plan: hypothesis, control/variant, sample size, success criteria      |
| data-storyteller    | Data narrative: headline finding, evidence, context, implications, action        |
| dashboard-spec      | Dashboard design: metrics by theme, layout, drill-downs, alerts, refresh cadence |
| anomaly-brief       | Anomaly investigation: causes ranked by likelihood, impact, monitoring plan      |

## Install

Say "add the data and analytics skills" during any conversation, or manually:

1. Open your `CLAUDE.md`
2. Find the `## Skills` table
3. Append the contents of `INDEX.md` to the table
4. Skill files in `skill-packs/data-analytics/skills/` load on-demand

## How it works

The trigger table in `INDEX.md` is all that lives in CLAUDE.md. When your intent matches a trigger phrase, Sidekick reads the relevant skill file on-demand. No context bloat.

These skills read `sidekick/context/current-priorities.md`, `sidekick/context/team-directory.md`, and `sidekick/memory/metrics/` (if it exists) before producing output.
