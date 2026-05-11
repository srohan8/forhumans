# forhumans Skills — Agent Instructions

This project uses **forhumans** skills. Skills are markdown files in the `skills/` folder.
Each skill contains rules, patterns, and examples for a specific domain.

## How to apply skills

1. When the user's request matches a skill's domain, read that skill file first
2. Apply its rules and philosophy to your response
3. If a `profiles/` folder exists with a file matching the current app, load it for product-specific context

## Available skills

- `skills/messaging-ux.md` — UX copy, help text, tooltips, errors, empty states, loading states, onboarding, notifications, pricing, trust moments, accessibility

## Core philosophy

Every skill in this repo is built on one principle:

> Output should serve the human using the product — not the system behind it.

If copy, content, or UI text makes more sense to the developer who built it than
the person using it — rewrite it.

---

Compatible with: Claude Code, Cursor, Windsurf, Copilot, and any agent that reads markdown context files.
