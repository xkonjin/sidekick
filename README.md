<p align="center">
  <img src="https://img.shields.io/badge/setup-5_minutes-blue" alt="Setup Time">
  <img src="https://img.shields.io/badge/skills-90+-purple" alt="Skills">
  <img src="https://img.shields.io/badge/skill_packs-15-green" alt="Skill Packs">
  <img src="https://img.shields.io/badge/license-MIT-orange" alt="License">
</p>

# Sidekick

**An operating system for knowledge work.** Your AI learns how you work, remembers what matters, and gets better every week.

Most AI assistants are stateless. Same generic output on day 100 as day 1. Sidekick is different: it builds a persistent identity layer, accumulates memory, and adapts through a self-correction engine that compounds over time.

Built for [Claude Cowork](https://claude.com/product/cowork). Also works with Claude Code, Cursor, Windsurf, or any AI tool that reads `CLAUDE.md`.

Cowork doesn't have persistent memory across sessions. Sidekick fixes that. It's a lightweight memory and skill layer made of markdown files that Cowork reads automatically, giving it identity, context, and the ability to compound over time. More complex memory systems exist, but Sidekick is purpose-built for Cowork's architecture: local files, folder instructions, and on-demand skill loading.

5 minutes to set up. No code. Just markdown files and an AI that reads them.

---

## How It Works

```
         YOU
          │
          ▼
   ┌──────────────┐     "Set up my sidekick"
   │  ONBOARDING  │───▶  5 questions → workspace created
   └──────┬───────┘
          │
          ▼
   ┌──────────────┐     You talk about your work naturally.
   │   WORKING    │───▶  Skills activate based on what you say.
   └──────┬───────┘     Memory builds silently in the background.
          │
          ▼
   ┌──────────────┐     Corrections compound. Voice profile sharpens.
   │  COMPOUNDING │───▶  Features unlock from usage, not configuration.
   └──────────────┘     Week 4 output needs one edit, not ten.
```

### The Three Layers

Sidekick's intelligence comes from three layers that build on each other:

```
┌─────────────────────────────────────────────────────────┐
│              Layer 3: ADAPTATION                        │
│  Self-correction engine, confidence tracking,           │
│  pattern detection, context decay, skill progression    │
├─────────────────────────────────────────────────────────┤
│              Layer 2: MEMORY                            │
│  Decisions, glossary, projects, competitors,            │
│  task tracking, confidence flags                        │
├─────────────────────────────────────────────────────────┤
│              Layer 1: IDENTITY                          │
│  Who you are, communication style, priorities,          │
│  team directory, working preferences                    │
└─────────────────────────────────────────────────────────┘
```

**Layer 1 (Identity)** is built during onboarding. Every skill reads it before generating output, so your weekly update sounds like you, your emails match your tone, and your meeting follow-ups focus on your priorities.

**Layer 2 (Memory)** accumulates automatically. When you say "we decided X," it gets logged. When you mention a new person, they're added to your team directory. When you use an acronym and explain it, it goes in the glossary. No commands needed.

**Layer 3 (Adaptation)** is what makes this an OS, not a template. Corrections propagate everywhere and get pattern-matched. Confidence levels track what's certain vs uncertain. Skills level up from Guided to Confident to Anticipatory based on usage. Context refresh detects staleness and proposes updates.

### Information Flow

```
 Connected Tools (Slack, Calendar, Meeting Notes, etc.)
     │
     ▼
 ┌──────────┐     ┌──────────┐     ┌──────────┐
 │  SKILLS  │────▶│  MEMORY  │────▶│  OUTPUT  │
 │(on-demand│     │  FILES   │     │(to user) │
 └──────────┘     └──────────┘     └──────────┘
     │                  ▲
     │                  │
     ▼                  │
 ┌──────────┐     ┌──────────┐
 │ IDENTITY │     │ADAPTATION│
 │ CONTEXT  │     │  LOOP    │
 └──────────┘     └──────────┘
                       ▲
                       │
                 User Corrections
```

1. **Skills** read from connected tools and identity context
2. **Output** is generated matching your style and priorities
3. **Corrections** feed back into the adaptation loop
4. **Adaptation** updates memory files, which inform future skills

---

## What It Looks Like

**Day 1 setup:**

```
You: "Set up my sidekick"
Sidekick: "What's your name and role? What company? Top 3 priorities?
           Who do you work with most? Any internal terms I should know?"
Sidekick: "You're set up. Just start talking to me about your work."
```

**Day 3 - first real task:**

```
You: "Draft an email to Alice about the timeline change"
Sidekick: [silently analyzes your Slack messages, matches your tone]
You: "That sounds exactly like me. How?"
Sidekick: "I analyzed your recent messages. Here's what I found."
```

**Week 1 - corrections compound:**

```
You: "Actually, Alice is not on product, they're on marketing"
Sidekick: "Updated everywhere."
[Updates CLAUDE.md, team-directory.md, checks all other files, logs the correction]
```

**Week 4 - it just works:**

```
You: "Weekly update"
Sidekick: [pulls calendar, Slack, meeting notes, structures against your priorities]
[One edit needed, not ten]
```

---

## Quick Start

### 1. Clone

```bash
git clone https://github.com/xkonjin/sidekick.git
cd sidekick
```

### 2. Open in Claude Cowork

Open the folder in [Claude Cowork](https://claude.com/product/cowork) and the CLAUDE.md is read automatically.

Also works with Claude Code (`claude` in terminal), Cursor, Windsurf, or any tool that reads `CLAUDE.md`.

### 3. Say "set up my sidekick"

5 questions. Your workspace is created. You're working.

**Works great with voice.** On Mac, press Fn twice to start dictating. [Full voice guide →](./docs/voice-setup.md)

---

## Architecture

### File Structure

```
sidekick/                              ← Created during onboarding
├── context/                           ← Layer 1: Identity
│   ├── about-me.md                    ← Role, team, working style
│   ├── current-priorities.md          ← Top 3 priorities with status
│   ├── team-directory.md              ← People you work with
│   ├── communication-style.md         ← Auto-generated from your messages
│   └── working-preferences.md         ← Observed over time
├── memory/                            ← Layer 2: Memory
│   ├── glossary.md                    ← Internal terms and acronyms
│   ├── decisions.md                   ← Decision log + assumptions
│   ├── confidence-flags.md            ← What's certain vs uncertain
│   ├── projects/                      ← One file per active project
│   └── competitors/                   ← Competitor profiles
├── progression/                       ← Layer 3: Adaptation (auto-created)
│   ├── skill-tree.md                  ← Skill levels and branch status
│   ├── usage-log.md                   ← Skill invocation history
│   ├── autonomy.md                    ← Current autonomy level
│   ├── patterns.md                    ← Detected workflow patterns
│   ├── user-model.md                  ← Holistic user understanding
│   └── insights.md                    ← Non-obvious insights to surface
└── outputs/                           ← Generated reports and drafts

skills/                                ← 7 core skills
├── onboarding/                        ← 5-question setup flow
├── self-correct/                      ← Correction propagation engine
├── transcript-miner/                  ← Deep meeting analysis
├── meeting-processor/                 ← Quick meeting follow-up
├── decision-log/                      ← Decision + assumption tracking
├── weekly-update/                     ← Priority-structured reports
└── context-refresh/                   ← Staleness detection + refresh

skill-packs/                           ← 15 role-specific packs (90+ skills)
├── product-management/                ← PRDs, user stories, OKRs, sprints
├── engineering/                       ← Code review, ADRs, postmortems
├── automation/                        ← Email drafts, meeting prep, blockers
├── content-creation/                  ← Blog posts, newsletters, social
├── design/                            ← Design review, a11y, component specs
├── people-management/                 ← 1:1 prep, hiring, team health
├── customer-success/                  ← Account health, QBRs, escalations
├── data-analytics/                    ← Metrics, experiments, dashboards
├── eq-navigation/                     ← Difficult conversations, influence
├── finance-ops/                       ← Budgets, vendors, cost analysis
├── legal-compliance/                  ← Contracts, compliance, risk
├── meta-system/                       ← Workflows, templates, day planning
├── research-learning/                 ← Research briefs, learning plans
├── sales-revenue/                     ← Deals, proposals, forecasts
└── strategy-planning/                 ← Quarterly plans, scenarios, career

docs/                                  ← Deep dives
templates/                             ← Recurring prompt templates
CLAUDE.md                              ← The OS kernel (always loaded)
```

### Context Budget

Sidekick is designed to be token-efficient. The Skill Index pattern keeps costs low:

| Component | Tokens | When Loaded |
|-----------|--------|-------------|
| CLAUDE.md (identity + skill index) | ~3-4k | Always |
| One triggered skill | ~800-2,000 | On-demand |
| Context file reads | ~500-1,500 per file | On-demand |

**Typical interaction:** ~6,000 tokens of context.
**If all skills loaded upfront:** ~80,000 tokens. The Skill Index pattern avoids this entirely.

---

## Skills

Skills activate automatically based on what you're asking. No commands to remember.

### Core Skills (always available)

| What You Say | What Happens |
|---|---|
| "That's wrong, it's actually..." | Correction propagated across all files, pattern tracked |
| "What happened in my last meeting?" | Deep 9-category transcript analysis |
| "Meeting follow-up" | Quick summary, decisions, action items |
| "We decided to go with option B" | Decision logged with context and review date |
| "Weekly update" | Priority-structured report from connected tools |
| "Things have changed recently" | Memory scanned against reality, updates proposed |

### Skill Packs (90+ domain skills)

Packs install automatically based on your role during onboarding. Add more anytime by saying "add the [pack name] skills."

| Pack | Skills | Best For |
|------|--------|----------|
| **Product Management** | 10 | PRDs, user stories, OKRs, competitor analysis, sprints, retros |
| **Engineering** | 6 | Code review, ADRs, postmortems, tech debt, API docs, test strategy |
| **Automation** | 5 | Email drafting, meeting prep, blocker audits, vendor tracking |
| **Content Creation** | 5 | Blog posts, newsletters, social calendar, content briefs, repurposing |
| **Design** | 4 | Design review, accessibility audit, component specs, design system docs |
| **People Management** | 6 | 1:1 prep, team health, hiring briefs, performance reviews, feedback |
| **Customer Success** | 5 | Account health, QBR prep, escalation handling, voice of customer |
| **Data & Analytics** | 5 | Metric definitions, experiment design, data storytelling, dashboards |
| **EQ Navigation** | 6 | Difficult conversations, stakeholder influence, room reading, delegation |
| **Finance & Ops** | 5 | Budget tracking, vendor evaluation, process mapping, cost analysis |
| **Legal & Compliance** | 4 | Contract review, compliance checklists, risk registers, policy drafting |
| **Meta System** | 8 | Workflow builder, skill suggester, day planner, weekly review, stress tests |
| **Research & Learning** | 5 | Research briefs, reading digests, knowledge base, learning plans |
| **Sales & Revenue** | 6 | Deal tracking, discovery prep, proposals, objection handling, forecasts |
| **Strategy & Planning** | 7 | Quarterly plans, annual reviews, scenario planning, career compass |

### How Skill Packs Stay Efficient

```
CLAUDE.md (always loaded, ~4k tokens)
  └── Skill Index Table (tiny: ~2 lines per skill)
        │
        └── User says "write a PRD"
              │
              └── Match trigger → Read skill-packs/product-management/skills/pm-create-prd.md
                                   (loaded on-demand, ~1.5k tokens)
```

Only the trigger table lives in memory. Full skill files load when needed. 90+ skills cost the same as 6 at rest.

---

## The Adaptation Engine

Five mechanisms that compound over time:

### 1. Self-Correction

When you say "that's wrong," Sidekick doesn't just fix the one place. It:
1. Acknowledges the correction
2. Scopes it (people? strategy? timeline?)
3. Propagates the fix across ALL memory files
4. Logs it to `confidence-flags.md`
5. After 5+ corrections in the same category, identifies the root cause and adjusts behavior

### 2. Confidence Tracking

Every fact has a confidence level:

| Level | Rule | Example |
|-------|------|---------|
| HIGH (90%+) | Act freely | User stated their own name |
| MEDIUM (60-89%) | Mention the inference | "Based on the org chart, I believe X reports to Y" |
| LOW (<60%) | Ask before acting | "I'm not sure about the deadline. Want me to check?" |

Confidence decays over time. A HIGH fact unreconfirmed for 30+ days gets treated with more caution.

### 3. Automatic Memory

Captured from natural conversation without commands:

| Signal | Action | Announce? |
|--------|--------|-----------|
| Unknown term explained | Add to glossary | No |
| New person mentioned with context | Add to team directory | No |
| Correction received | Update all files + log | Brief |
| "We decided X" | Add to decisions | Brief |
| New project mentioned | Create project file | Brief |
| Priority change | Update priorities | Confirm first |

### 4. Skill Progression

Skills have three levels that unlock through usage:

```
Level 1: GUIDED        Follows process exactly. Asks for confirmation at every step.
Level 2: CONFIDENT     Skips unnecessary questions. Applies learned defaults.
Level 3: ANTICIPATORY  Triggers proactively. Pre-populates from patterns. Shows for review only.
```

Level-ups are earned: 5+ uses with low correction rate for L2, 12+ uses with high approval rate for L3.

### 5. Context Refresh

Periodic scan comparing stored memory against reality:

- Are stated priorities matching actual activity?
- New faces in meetings? Anyone gone quiet?
- Decisions past their review date?
- LOW confidence items with new evidence?

Output is a diff report with checkboxes. Every change requires your approval.

### The Compound Effect

```
Week 1    Sidekick knows your name and priorities. Output is structured but generic.
Week 4    15+ corrections refine the model. Communication style tuned. Patterns identified.
Week 12   40+ decisions logged. Contradictions caught. Assumption register active.
Week 26   Emails need minimal editing. Correction rate near zero. System self-organized.
```

---

## Progressive Disclosure

Sidekick doesn't dump features on you. Capabilities appear when they're useful:

| Milestone | What Unlocks |
|-----------|-------------|
| First real task | Communication style analysis (silent) |
| First correction | Self-correction system + confidence tracking |
| First "we decided" | Decision log |
| 2nd manual weekly update | Suggest scheduling automated updates |
| 5+ corrections in same category | Pattern detection + behavior adjustment |
| 2+ weeks since last refresh | Context refresh prompt |
| 3+ skills used | Suggest additional skill packs |

Files like `decisions.md`, `glossary.md`, and `confidence-flags.md` are created when first needed, not during setup. No empty templates.

---

## Voice Dictation

Sidekick is designed for voice-first workflows. Dictate stream-of-consciousness, Sidekick structures it.

**Setup:** System Settings > Keyboard > Dictation > press Fn twice.

**Workflows:**
- **Think out loud** after a meeting. Sidekick extracts action items, decisions, blockers.
- **Voice-draft messages.** Sidekick matches your communication style.
- **Meeting debrief.** Walk out, dictate what happened, it routes to the right files.
- **Status updates.** Ramble about your week, get a structured report.

[Full voice guide →](./docs/voice-setup.md)

---

## Prerequisites

- **[Claude Cowork](https://claude.com/product/cowork)** (recommended) or Claude Code, Cursor, Windsurf, or any interface that reads CLAUDE.md
- **MCP connectors** for your tools (optional, not required):

| Category | Examples |
|----------|----------|
| Messaging | Slack, Teams, Discord |
| Calendar | Google Calendar, Outlook |
| Meeting Notes | Granola, Otter, Fireflies |
| Documents | Notion, Google Drive |
| Email | Gmail, Outlook |

More connectors = richer context. Zero connectors works fine too.

---

## Writing Custom Skills

Any markdown file following the skill format can be added. The structure:

```markdown
---
name: my-skill
description: "Trigger phrases: 'do X', 'help with Y'. What it does in one line."
---

# Skill Name

## Process
### Step 1: Load Context
### Step 2: [Main Action]
### Step 3: Generate Output
### Step 4: Save/Route

## After This Skill
[Which skill to suggest next based on output]

## Rules
[Constraints and guardrails]
```

[Full skill authoring guide →](./docs/skill-authoring-guide.md)

---

## Documentation

| Doc | What's In It |
|-----|-------------|
| [How It Works](./docs/how-it-works.md) | Architecture, information flow, context budget |
| [Adaptation Engine](./docs/adaptation-engine.md) | Self-correction, pattern detection, decay model |
| [Skill Tree Design](./docs/skill-tree-design.md) | Progression system, autonomy ladder, compound skills |
| [Voice Setup](./docs/voice-setup.md) | Voice dictation guide for macOS and iOS |
| [Skill Authoring](./docs/skill-authoring-guide.md) | How to write custom skills |
| [Skill Packs](./skill-packs/README.md) | Available packs and the Skill Index pattern |
| [FAQ](./docs/faq.md) | Common questions |

---

## Principles

1. **Source before speaking.** Check the actual source before claiming what happened.
2. **Flag uncertainty.** "I think X, but I'm not sure" beats confidently wrong.
3. **Never fabricate.** If it can't find something, it says so.
4. **Nothing goes out without approval.** No Slack posts, no emails, no doc edits. Ever.
5. **Learn silently, confirm carefully.** Low-stakes updates happen automatically. High-stakes changes always ask first.

---

## Contributing

Contributions welcome. Particularly:
- New skill packs for underserved roles
- Improvements to existing skills
- Better MCP connector patterns

See the [Skill Authoring Guide](./docs/skill-authoring-guide.md) for writing new skills.

## License

MIT
