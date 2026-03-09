# How Sidekick Works

Sidekick's intelligence comes from three compounding layers. Each layer builds on the one below it.

## The Three Layers

```
┌─────────────────────────────────────────┐
│         Layer 3: ADAPTATION             │
│  Self-correction, confidence tracking,  │
│  pattern detection, context refresh     │
├─────────────────────────────────────────┤
│         Layer 2: MEMORY                 │
│  Decisions, glossary, projects,         │
│  task tracking, competitor profiles     │
├─────────────────────────────────────────┤
│         Layer 1: IDENTITY              │
│  Who you are, communication style,      │
│  priorities, team, preferences          │
└─────────────────────────────────────────┘
```

### Layer 1: Identity

**What it captures:** Who you are, how you communicate, what you care about.

**Files:**
| File | Purpose |
|------|---------|
| `sidekick/context/about-me.md` | Role, team, working style, energy patterns |
| `sidekick/context/communication-style.md` | Tone, vocabulary, structure (auto-generated from messages) |
| `sidekick/context/working-preferences.md` | Output format, guardrails, banned words |
| `sidekick/context/current-priorities.md` | Top 3 priorities with status and blockers |
| `sidekick/context/team-directory.md` | People you work with, roles, relationships |

**Why it matters:** Every skill reads these files before generating output. Your weekly update sounds like you. Your meeting follow-ups focus on your priorities. Your email drafts match your actual tone.

### Layer 2: Memory

**What it captures:** What happened, what was decided, what's uncertain.

**Files:**
| File | Purpose |
|------|---------|
| `sidekick/memory/glossary.md` | Internal terms and acronyms |
| `sidekick/memory/decisions.md` | Decision log + assumption register |
| `sidekick/memory/confidence-flags.md` | What's certain vs uncertain |
| `sidekick/memory/projects/*.md` | One file per active project |
| `sidekick/memory/competitors/*.md` | Competitor profiles |
| `sidekick/TASKS.md` | Active task tracker |

**Why it matters:** Sidekick doesn't start from zero each conversation. It knows what was decided last week, what terms mean in your context, and what projects are active.

### Layer 3: Adaptation

**What it captures:** How to get better over time.

**Mechanisms:**
| Mechanism | How it Works |
|-----------|-------------|
| **Self-correction** | When you correct Sidekick, it propagates the fix across all memory files and logs the correction |
| **Confidence tracking** | Every fact has a confidence level (HIGH/MEDIUM/LOW). Uncertain things get flagged, not guessed. |
| **Pattern detection** | After 5+ corrections in the same category, Sidekick identifies the root cause and adjusts its behavior |
| **Context refresh** | Weekly scan compares stored memory against recent activity and proposes updates |
| **Communication learning** | Initial style profile from message analysis, refined over time as corrections come in |
| **Skill chaining** | Skills suggest the next relevant skill after completing, creating natural workflows |
| **Progressive capabilities** | Features unlock based on usage milestones, not configuration |
| **Role-based setup** | Onboarding auto-installs relevant skill packs based on the user's role |

**Why it matters:** Most AI assistants are static. They work the same on day 100 as day 1. Sidekick compounds: it gets better at matching your voice, understanding your priorities, and avoiding mistakes it's made before.

## Information Flow

```
Connected Tools (Slack, Calendar, Meeting Notes, CRM, etc.)
    │
    ▼
┌──────────────┐     ┌──────────────┐     ┌──────────────┐
│   Skills     │────▶│   Memory     │────▶│   Output     │
│ (on-demand)  │     │   Files      │     │ (to user)    │
└──────────────┘     └──────────────┘     └──────────────┘
    │                      ▲
    │                      │
    ▼                      │
┌──────────────┐     ┌──────────────┐
│  Identity    │     │  Adaptation  │
│  Context     │     │  Loop        │
└──────────────┘     └──────────────┘
                           ▲
                           │
                     User Corrections
```

1. **Skills** read from connected tools and identity context
2. **Output** is generated matching the user's style and priorities
3. **User corrections** feed back into the adaptation loop
4. **Adaptation** updates memory files, which inform future skills

## Context Budget

Sidekick is designed to be token-efficient:

| Component                          | Always Loaded | On-Demand                  |
| ---------------------------------- | ------------- | -------------------------- |
| CLAUDE.md (identity + skill index) | ~3-4k tokens  | -                          |
| One triggered skill                | -             | ~800-2,000 tokens          |
| Context file reads                 | -             | ~500-1,500 tokens per file |

**Typical interaction cost:** ~6,000 tokens of context. Compare to loading all skills upfront: ~80,000 tokens.
