# forhumans

> Agent skills built around people, not systems.

[![skills.sh](https://skills.sh/b/srohan8/forhumans)](https://skills.sh/srohan8/forhumans)

A collection of open-source agent skills built on one idea: **software should make sense to the humans using it, not just the people who built it.**

---

## What is a skill?

A skill is a markdown file that gives your AI agent deep, specialised expertise in a specific domain. Drop it into any project and your agent applies it automatically — no prompting, no repeating yourself.

Think of it as hiring a specialist. Not a general assistant — someone who knows exactly how to do one thing really well, every time.

Works with Claude Code, Cursor, Codex, GitHub Copilot, Windsurf, Gemini CLI, and any agent that reads markdown context files.

---

## Available skills

| Skill | What it does | Best for |
| --- | --- | --- |
| [messaging-ux](https://github.com/srohan8/forhumans/blob/main/skills/messaging-ux.md) | Writes and audits all in-product copy through a human-centric lens — tooltips, errors, empty states, loading states, onboarding, notifications, pricing, and more | Anyone building a product |
| [flow-ux](https://github.com/srohan8/forhumans/blob/main/skills/flow-ux.md) | Designs and audits user journeys — onboarding flows, error recovery, progressive disclosure, and respectful offboarding | Anyone shipping a product to non-experts |
| [accessibility-ux](https://github.com/srohan8/forhumans/blob/main/skills/accessibility-ux.md) | Audits and fixes accessibility across cognitive load, visual, motor, screen reader, plain language, forms, and navigation — translated into plain language and concrete code | Anyone building for real humans |

More skills coming. See [Contributing](#contributing) if you want to add one.

### The trio: messaging-ux, flow-ux, accessibility-ux

These three are designed to work together. **messaging-ux** handles what every screen *says*. **flow-ux** handles what screens *exist and in what order*. **accessibility-ux** handles whether *everyone can actually use those screens*. Use them together for a full UX layer, or independently for focused work.

Each answers a different question:

- messaging-ux — *does everyone understand this?*
- flow-ux — *can everyone navigate this?*
- accessibility-ux — *can everyone use this?*

They never overlap — each handles a different layer of the same product.

---

## Installation

### Skills CLI (recommended)

```bash
npx skills add srohan8/forhumans
```

Installs all forhumans skills automatically. Works with Claude Code, Cursor, Codex, Windsurf, Gemini CLI, and more. Restart your agent after install.

### Claude Code (manual)

```bash
curl -O https://raw.githubusercontent.com/srohan8/forhumans/main/CLAUDE.md
mkdir -p skills
curl -o skills/messaging-ux/SKILL.md https://raw.githubusercontent.com/srohan8/forhumans/main/skills/messaging-ux/SKILL.md
curl -o skills/flow-ux/SKILL.md https://raw.githubusercontent.com/srohan8/forhumans/main/skills/flow-ux/SKILL.md
curl -o skills/accessibility-ux/SKILL.md https://raw.githubusercontent.com/srohan8/forhumans/main/skills/accessibility-ux/SKILL.md
```

### Cursor / Codex / other agents (manual)

```bash
curl -O https://raw.githubusercontent.com/srohan8/forhumans/main/AGENTS.md
mkdir -p skills
curl -o skills/messaging-ux/SKILL.md https://raw.githubusercontent.com/srohan8/forhumans/main/skills/messaging-ux/SKILL.md
curl -o skills/flow-ux/SKILL.md https://raw.githubusercontent.com/srohan8/forhumans/main/skills/flow-ux/SKILL.md
curl -o skills/accessibility-ux/SKILL.md https://raw.githubusercontent.com/srohan8/forhumans/main/skills/accessibility-ux/SKILL.md
```

### Claude.ai projects

1. Open [claude.ai](https://claude.ai) → your project → **Project Settings**
2. Click **Add Content**
3. Copy and paste the contents of any skill file
4. Start a conversation — Claude applies the skill automatically

### One-click copy

Click any skill below to open the raw file — copy and paste into your Claude project:

- [messaging-ux](https://raw.githubusercontent.com/srohan8/forhumans/main/skills/messaging-ux.md)
- [flow-ux](https://raw.githubusercontent.com/srohan8/forhumans/main/skills/flow-ux.md)
- [accessibility-ux](https://raw.githubusercontent.com/srohan8/forhumans/main/skills/accessibility-ux.md)

---

## How it works in your project

Skills are most powerful inside a project that contains your code. Your agent will:

- Infer your app's audience and tone without you having to explain
- Audit your entire codebase, not just what you paste
- Build a profile of your product so it gets smarter over time

---

## Product profiles

Some skills support **product profiles** — small config files that store your app's specific settings (audience, tone, jargon swaps, example rewrites, accessibility level, tech stack) so Claude never asks the same questions twice.

Profiles live in a `profiles/` folder in your project. They're yours — private, never part of this shared repo. messaging-ux, flow-ux, and accessibility-ux share the same profile format, so you only set up one profile per product.

See `profiles/example.md` for the format.

---

## Contributing

### Adding a new skill

A good skill:

- Does one thing well — focused, not general
- Works across different products and codebases
- Has a clear philosophy, not just a list of rules
- Is built around the human using the product — not the system behind it

To contribute:

1. Fork this repo
2. Add your skill to `skills/yourskillname.md`
3. Open a pull request with a short description and a before/after example

### Improving an existing skill

See `CONTRIBUTING.md` for what each skill accepts — jargon swaps, new component or flow patterns, framework-specific accessibility patterns, domain-specific blocks, page-aware rules, and bug fixes.

---

## Philosophy

Every skill in this repo is built on one idea:

> Software should make sense to the humans using it — not just the people who built it.

Whether it's words, journeys, or access — the output of any skill here should make things clearer, simpler, and more human for the person on the other end.

---

## License

MIT — use freely, modify openly, share widely.
