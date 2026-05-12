# forhumans Skills

This project uses **forhumans** skills — a collection of Claude skills built around people, not systems.

## Active skills

- [messaging-ux](./skills/messaging-ux.md) — human-centric UX copy, tooltips, errors, empty states, onboarding, and more
- [flow-ux](./skills/flow-ux.md) — onboarding flows, error recovery, progressive disclosure, offboarding
- [accessibility-ux](./skills/accessibility-ux.md) — cognitive load, visual, motor, screen readers, keyboard nav, plain language

## How to use

Claude reads these skills automatically. Just ask naturally:

- "Review the copy on this screen"
- "Add help text to these fields"
- "Audit the codebase for missing explanations"
- "Rewrite this error message"
- "Write a loading message for this API call"
- "Design the onboarding flow for new users"
- "Audit this screen for accessibility issues"
- "What screens are missing from this flow?"

## Product profile

If a `profiles/` folder exists with a file matching your app name (e.g. `profiles/myapp.md`),
Claude loads it automatically — no need to re-explain your audience or tone.

See `profiles/example.md` for the format.

---

