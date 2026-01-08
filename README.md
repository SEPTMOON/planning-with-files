# Planning with Files

> **Work like Manus** — the AI agent company Meta acquired for **$2 billion**.

## Thank You

To everyone who starred, forked, and shared this skill — thank you. This project blew up in less than 24 hours, and the support from the community has been incredible.

If this skill helps you work smarter, that's all I wanted.

---

A Claude Code plugin containing an [Agent Skill](https://code.claude.com/docs/en/skills) that transforms your workflow to use persistent markdown files for planning, progress tracking, and knowledge storage — the exact pattern that made Manus worth billions.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Claude Code Plugin](https://img.shields.io/badge/Claude%20Code-Plugin-blue)](https://code.claude.com/docs/en/plugins)
[![Claude Code Skill](https://img.shields.io/badge/Claude%20Code-Skill-green)](https://code.claude.com/docs/en/skills)
[![Version](https://img.shields.io/badge/version-2.0.0-brightgreen)](https://github.com/OthmanAdi/planning-with-files/releases)

## Versions

| Version | Branch | Features | Install |
|---------|--------|----------|---------|
| **v2.0.0** (current) | `master` | Hooks, templates, scripts | `/plugin install planning-with-files@planning-with-files` |
| **v1.0.0** (legacy) | `legacy` | Core 3-file pattern | `git clone -b legacy https://github.com/OthmanAdi/planning-with-files.git` |

## What's New in v2.0.0

- **Hooks Integration** — Automatic plan re-reading and completion verification
- **Templates** — Structured templates for task_plan.md, findings.md, progress.md
- **Scripts** — Helper scripts for initialization and completion checks
- **Enhanced Documentation** — 2-Action Rule, 3-Strike Protocol, 5-Question Reboot Test

See [CHANGELOG.md](CHANGELOG.md) for details. Upgrading from v1.x? See [MIGRATION.md](MIGRATION.md).

## Why This Skill?

On December 29, 2025, [Meta acquired Manus for $2 billion](https://techcrunch.com/2025/12/29/meta-just-bought-manus-an-ai-startup-everyone-has-been-talking-about/). In just 8 months, Manus went from launch to $100M+ revenue. Their secret? **Context engineering**.

This skill implements Manus's core workflow pattern:

> "Markdown is my 'working memory' on disk. Since I process information iteratively and my active context has limits, Markdown files serve as scratch pads for notes, checkpoints for progress, building blocks for final deliverables."
> — Manus AI

## The Problem

Claude Code (and most AI agents) suffer from:

- **Volatile memory** — TodoWrite tool disappears on context reset
- **Goal drift** — After 50+ tool calls, original goals get forgotten
- **Hidden errors** — Failures aren't tracked, so the same mistakes repeat
- **Context stuffing** — Everything crammed into context instead of stored

## The Solution: 3-File Pattern

For every complex task, create THREE files:

```
task_plan.md      → Track phases and progress
findings.md       → Store research and findings
progress.md       → Session log and test results
```

### The Core Principle

```
Context Window = RAM (volatile, limited)
Filesystem = Disk (persistent, unlimited)

→ Anything important gets written to disk.
```

## Installation

### As a Claude Code Plugin (Recommended)

Install directly using the Claude Code CLI:

```
/plugin marketplace add OthmanAdi/planning-with-files
/plugin install planning-with-files@planning-with-files
```

### Manual Installation

Clone or copy this repository into your project's `.claude/plugins/` directory:

```bash
# Option 1: Clone into plugins directory
mkdir -p .claude/plugins
git clone https://github.com/OthmanAdi/planning-with-files.git .claude/plugins/planning-with-files

# Option 2: Add as git submodule
git submodule add https://github.com/OthmanAdi/planning-with-files.git .claude/plugins/planning-with-files

# Option 3: Use --plugin-dir flag
git clone https://github.com/OthmanAdi/planning-with-files.git
claude --plugin-dir ./planning-with-files
```

### Legacy Installation (Skills Only)

Copy the `skills/` directory contents into your `.claude/skills/` folder:

```bash
git clone https://github.com/OthmanAdi/planning-with-files.git
cp -r planning-with-files/skills/* ~/.claude/skills/
```

## Usage

Once installed, Claude will automatically:

1. **Create `task_plan.md`** before starting complex tasks
2. **Re-read plan** before major decisions (via hooks)
3. **Update progress** with checkboxes after each phase
4. **Store findings** in `findings.md` instead of stuffing context
5. **Log errors** for future reference
6. **Verify completion** before stopping (via hooks)

### Key Rules

1. **Create Plan First** — Never start without `task_plan.md`
2. **The 2-Action Rule** — Save findings after every 2 view/browser operations
3. **Log ALL Errors** — They help avoid repetition
4. **Never Repeat Failures** — Track attempts, mutate approach

## File Structure

```
planning-with-files/
├── .claude-plugin/
│   ├── plugin.json          # Plugin manifest
│   └── marketplace.json     # Marketplace listing
├── skills/
│   └── planning-with-files/
│       ├── SKILL.md         # Main skill definition
│       ├── reference.md     # Manus principles
│       ├── examples.md      # Usage examples
│       ├── templates/       # File templates
│       │   ├── task_plan.md
│       │   ├── findings.md
│       │   └── progress.md
│       └── scripts/         # Helper scripts
│           ├── init-session.sh
│           └── check-complete.sh
├── CHANGELOG.md             # Version history
├── MIGRATION.md             # Upgrade guide
├── LICENSE
└── README.md
```

## The Manus Principles

This skill implements these key context engineering principles:

| Principle | Implementation |
|-----------|----------------|
| Filesystem as memory | Store in files, not context |
| Attention manipulation | Re-read plan before decisions (hooks) |
| Error persistence | Log failures in plan file |
| Goal tracking | Checkboxes show progress |
| Completion verification | Stop hook checks all phases |

## When to Use

**Use this pattern for:**
- Multi-step tasks (3+ steps)
- Research tasks
- Building/creating projects
- Tasks spanning many tool calls
- Anything requiring organization

**Skip for:**
- Simple questions
- Single-file edits
- Quick lookups

## Acknowledgments

- **Manus AI** — For pioneering context engineering patterns
- **Anthropic** — For Claude Code, Agent Skills, and the Plugin system
- **Lance Martin** — For the detailed Manus architecture analysis
- Based on [Context Engineering for AI Agents](https://manus.im/blog/Context-Engineering-for-AI-Agents-Lessons-from-Building-Manus)

## Contributing

Contributions welcome! Please:
1. Fork the repository
2. Create a feature branch
3. Submit a pull request

## License

MIT License — feel free to use, modify, and distribute.

---

**Author:** [Ahmad Othman Ammar Adi](https://github.com/OthmanAdi)

## Star History

[![Star History Chart](https://api.star-history.com/svg?repos=OthmanAdi/planning-with-files&type=Date)](https://star-history.com/#OthmanAdi/planning-with-files&Date)
