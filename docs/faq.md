# FAQ

## Setup

**How long does onboarding take?**
About 5 minutes. 5 questions, then you're working.

**Do I need all the MCP connectors?**
No. Sidekick works with whatever you have. More connections means richer context, but it degrades gracefully. You can start with zero connectors and add them later.

**What if I don't use Slack?**
The communication analysis uses whatever messaging tool is connected (Teams, Discord, email). If nothing is connected, it analyzes your conversation style and builds from there.

**Can I use this with Claude Code?**
Yes. Open the repo in Claude Code and the CLAUDE.md will be read automatically. Say "set up my sidekick" to begin.

**Does it work with voice dictation?**
Yes. Sidekick is designed to handle natural speech including filler words, mid-sentence corrections, and stream-of-consciousness input. See [Voice Setup](./voice-setup.md) for details.

## Daily Use

**How do I update my priorities?**
Just say "my priorities changed" and describe the new ones. Or edit `sidekick/context/current-priorities.md` directly.

**How do I add a new team member?**
Just mention them with context ("Sarah from engineering said...") and Sidekick adds them automatically. Or edit `sidekick/context/team-directory.md` directly.

**How do I correct a mistake?**
Just say "that's wrong, it's actually X." Sidekick propagates the fix across all memory files and logs the correction. No special command needed.

**How often does context refresh happen?**
Sidekick suggests a refresh after 2+ weeks of no scan. You can also say "refresh context" anytime.

**Can Sidekick send emails or post to Slack on my behalf?**
Never without explicit approval. All generated messages are drafts. You decide where and when they get sent.

**Do I need to remember any commands?**
No. Skills activate based on what you're asking. "What happened in my meeting?" triggers meeting analysis. "That's wrong" triggers self-correction. Just talk naturally.

## Skills

**What's the difference between transcript-miner and meeting-processor?**
Transcript-miner is deep analysis: 9-category signal classification, priority impact assessment, routing to memory. Meeting-processor is a quick follow-up: summary, decisions, action items.

**How do I install a skill pack?**
Skill packs are installed automatically during onboarding based on your role. You can also say "add the product management skills" or browse `skill-packs/` and pick what's relevant. The trigger table gets added to your CLAUDE.md automatically.

**Can I write my own skills?**
Yes. See `docs/skill-authoring-guide.md`. Any markdown file following the skill format can be added.

**Do skill packs slow things down?**
No. Only the tiny trigger table lives in CLAUDE.md (~2 lines per skill). Full skill files load on-demand.

**How many skill packs are there?**
Six: Product Management (10 skills), Engineering (6), Automation (5), Design (4), People Management (6), and Content Creation (5). Total: 36 domain skills + 6 core skills = 42 skills.

**Do skills chain together?**
Yes. When a skill finishes, it suggests the next relevant skill based on what it found. For example, after processing a meeting, it might suggest logging decisions or updating your weekly report. You always choose whether to follow the chain.

## How It Works

**Where does my data live?**
Everything is local markdown files in your workspace. No external databases, no cloud storage, no API calls (unless you're using MCP connectors to your own tools).

**How does automatic memory work?**
Sidekick captures information from natural conversation: new terms, people, decisions, preferences. Low-stakes items (glossary terms, people) are added silently. High-stakes items (priority changes) always ask first.

**What happens when information gets stale?**
Sidekick suggests a context refresh after 2+ weeks. Priorities with no activity get flagged. Decisions past their review date get flagged. Nothing is auto-deleted.

**Why didn't Sidekick create all the files during setup?**
Progressive disclosure. Files like `decisions.md`, `glossary.md`, and `confidence-flags.md` are created when first needed, not before. This keeps the workspace clean and avoids empty templates.

**Can multiple people share a Sidekick setup?**
Each person should have their own. The identity layer is personal. Shared team context (glossary, projects) could be symlinked, but personal files should be individual.

## Voice

**What's the best way to use voice with Sidekick?**
Press Fn twice on Mac to start dictating. Talk naturally. Sidekick handles filler words, mid-sentence corrections, and unstructured thoughts. See [Voice Setup](./voice-setup.md).

**Does voice dictation work on mobile?**
Yes. Enable dictation in iOS/iPadOS settings and use the microphone icon in the Claude app.

## Troubleshooting

**"Sidekick doesn't know about X"**
Mention it in conversation and Sidekick will capture it. Or edit the relevant memory file directly.

**"Output doesn't sound like me"**
Ask Sidekick to re-analyze your communication style with more messages. Or edit `sidekick/context/communication-style.md` directly.

**"A skill didn't activate"**
Try rephrasing naturally. Skills detect intent, not exact phrases. If it still doesn't work, you can say "use the [skill-name] skill" as a fallback.

**"Scheduled tasks aren't running"**
Say "list my scheduled tasks" to check. If they exist but aren't producing output, verify connected tools are still authenticated.
