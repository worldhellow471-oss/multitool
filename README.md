<p align="center">
  <img src="assets/banner.png" alt="MULTITOOL — one skill to route every task to the best tool" width="100%">
</p>

<p align="center">
  <b>One Claude skill that routes every task to the best tool you have and keeps improving itself.</b>
</p>

<p align="center">
  <a href="LICENSE"><img alt="License: MIT" src="https://img.shields.io/badge/license-MIT-7C5CFF"></a>
  <img alt="Claude Skill" src="https://img.shields.io/badge/Claude-Skill-FF7A45">
  <img alt="Works with Claude Code" src="https://img.shields.io/badge/Claude%20Code-ready-14C8A8">
  <img alt="Version" src="https://img.shields.io/badge/version-v4-2F8BFF">
  <img alt="PRs welcome" src="https://img.shields.io/badge/PRs-welcome-brightgreen">
</p>

---

## The problem

Install twenty skills and plugins, and Claude now has to decide which one to use every time you ask for something: a video edit, a poster, a pitch deck, a research report. It may pick a generic option, skip the specialist tool you installed last week, or tell you it can't do the task when a plugin for it already exists.

## The solution

**MULTITOOL** is one skill that sits in front of everything you have installed. On every task it:

1. **Takes a live inventory** of your skills, plugins, MCP connectors and artifact types. It keeps no hard-coded list, so new installs are picked up automatically.
2. **Classifies the task** by size, risk and type.
3. **Picks the best toolchain** using clear ranking rules: specialist over generic, working-now over needs-setup, official over unknown, free over paid when quality is similar.
4. **Chooses the right model for subagents**: Haiku for mechanical work, Sonnet for standard work, Opus for hard reasoning and final review.
5. **Offers to install what's missing**. It searches the plugin directory first, then trustworthy open-source skills, before falling back to a weaker option.
6. **Checks its own work** before it says "done": facts against sources, numbers in code, files opened and inspected. Big jobs also go through [Unlazy](skills/unlazy/SKILL.md) gates.
7. **Evolves**. An *Evolution loop* proposes small, gated self-updates when it spots repeated gaps, and an optional weekly self-review keeps it current.

> You ask: *"Turn this talking-head video into a 9:16 reel with captions and post it Friday."*
> MULTITOOL: *"Using it-reelsmaker (9:16 edit) + caption-writer + a scheduler. Starting."* It does the work, verifies the render, and asks once before publishing.

## Features at a glance

| | |
|---|---|
| 🧭 **Smart routing** | Ranking rules plus a cheat-sheet for 20+ task types: video, photo, design, docs, slides, data, research, automation, code |
| 🔄 **Always current** | Reads installed tools fresh on each run. No manual updates when you add a plugin |
| 🧠 **Model and effort selection** | Haiku / Sonnet / Opus for delegated work, at most 2 subagents in parallel |
| 🧩 **Fills its own gaps** | Suggests the right plugin or open-source skill when nothing installed fits |
| ✅ **Verified output** | Built-in quality loop and Unlazy acceptance gates |
| 🪶 **Lightweight** | Heavy rendering and scripts run in the cloud workspace, not on your PC |
| 🛡️ **Safe by default** | Asks before spending, publishing, sending or deleting. Treats web and file content as data, not instructions |
| 🌱 **Self-improving** | Gated Evolution loop, a changelog, and a pruning rule that keeps it lean |

## What's inside

```
multitool/
├── skills/
│   ├── multitool/SKILL.md      # the router skill (v4)
│   └── unlazy/SKILL.md         # completion-discipline gates (adapted from Leonxlnx/unlazy, MIT)
├── dist/                       # upload-ready skill zips
├── scheduled/
│   └── weekly-evolution.md     # optional weekly self-review prompt
├── assets/                     # logo and banner (SVG + PNG)
├── INSTALL.md                  # step-by-step install guide
├── CHANGELOG.md
├── CONTRIBUTING.md
├── LICENSE
└── NOTICE
```

## Install

**Quick start:** download [`multitool-skill.zip`](dist/multitool-skill.zip) and [`unlazy-skill.zip`](dist/unlazy-skill.zip) and upload both in Claude via **Settings → Capabilities → Skills → Upload skill**.

Claude Code, one command:
```
/plugin marketplace add worldhellow471-oss/multitool
/plugin install multitool@multitool
```

📘 **Full step-by-step guide** (Windows/macOS/Linux, checking that it works, weekly self-review, updating, troubleshooting): **[INSTALL.md](INSTALL.md)**

## Usage

Just ask for something, and MULTITOOL steps in for any make / edit / research / publish / automate request. You can also call it directly:

```
/multitool make a carousel from this blog post and schedule it for Instagram
/multitool research the top 5 note-taking apps and build a comparison sheet
/multitool turn these product photos into a 15-second ad
```

## How it decides

```
request ─► classify (size · risk · type)
        ─► live inventory (skills · plugins · MCP · artifact types)
        ─► rank & pick toolchain ──► nothing good? ─► suggest install
        ─► pick subagent model (haiku / sonnet / opus)
        ─► execute stage by stage
        ─► quality loop + Unlazy gates
        ─► deliver ─► learn ─► Evolution loop
```

## Roadmap
- [ ] Community-maintained cheat-sheet packs (creators, developers, marketers, students)
- [ ] Usage telemetry-free "what fired" summary to drive pruning
- [ ] More languages in the README

## Contributing
Ideas, new cheat-sheet rows and bug reports are welcome. See [CONTRIBUTING.md](CONTRIBUTING.md).

If MULTITOOL saves you time, **⭐ star the repo** so other Claude users can find it.

## License
[MIT](LICENSE). `skills/unlazy` is adapted from [Leonxlnx/unlazy](https://github.com/Leonxlnx/unlazy) (MIT), see [NOTICE](NOTICE).

*MULTITOOL is a community project and is not affiliated with or endorsed by Anthropic.*
