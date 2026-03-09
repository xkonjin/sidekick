# Skill Packs

Role-specific skill bundles that extend Sidekick's core capabilities. Each pack is optimized for context efficiency using the **Skill Index pattern**.

## How Skill Packs Work

### The Context Bloat Problem

Loading 50+ skill files into CLAUDE.md would consume 30k+ tokens. Not viable.

### The Solution: Skill Index Pattern

CLAUDE.md contains only a tiny trigger table (~500 tokens for 50 skills). When user intent matches, Sidekick reads the specific skill file on-demand.

```
CLAUDE.md (always loaded)
  └── Skill Index (tiny table: skill name | trigger phrases | file path)
        └── When triggered -> Read skill-packs/[pack]/skills/[skill].md (on-demand)
```

**Result:** CLAUDE.md stays under 4k tokens even with all 6 packs installed. Skills load only on trigger. Maximum context cost per interaction: ~4k (CLAUDE.md) + ~2k (one triggered skill) = ~6k tokens.

## Available Packs

| Pack                                        | Skills                                                                   | Best For                                         |
| ------------------------------------------- | ------------------------------------------------------------------------ | ------------------------------------------------ |
| [Product Management](./product-management/) | 10 skills: PRDs, user stories, prioritization, OKRs, competitor analysis | PMs, product leads, founders                     |
| [Engineering](./engineering/)               | 6 skills: code review, ADRs, postmortems, tech debt tracking             | Engineers, tech leads, dev managers              |
| [Automation](./automation/)                 | 5 skills: email drafting, meeting prep, blocker audits, vendor tracking  | Ops, marketing, managers, executives             |
| [Design](./design/)                         | 4 skills: design review, accessibility audit, component specs            | Designers, design leads, PMs working with design |
| [People Management](./people-management/)   | 6 skills: 1:1 prep, hiring briefs, team health, feedback, capacity       | Managers, team leads, people ops                 |
| [Content Creation](./content-creation/)     | 5 skills: blog posts, social calendar, newsletters, content briefs       | Marketers, writers, content leads                |

## Auto-Installation

During onboarding, Sidekick detects your role and installs the most relevant packs automatically. You can also install packs manually anytime.

## Installing a Pack

Say "add the [pack name] skills" and Sidekick will install it automatically. Or manually:

1. Open `CLAUDE.md`
2. Find the Skills Index section
3. Append the contents of the pack's `INDEX.md` to the table
4. The individual skill files are already in place and will load on-demand

## Creating Custom Packs

You can create your own skill packs:

1. Create a directory in `skill-packs/` with your pack name
2. Create an `INDEX.md` with the trigger table format
3. Create a `skills/` subdirectory with individual skill files
4. Each skill file follows the same format as core skills (see `skills/self-correct/SKILL.md` for an example)

## Pack Format

Each pack contains:

- `README.md` - Pack description and install instructions
- `INDEX.md` - The trigger table to append to CLAUDE.md
- `skills/` - Individual skill files (loaded on-demand only)
