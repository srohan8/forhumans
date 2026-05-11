# Contributing to forhumans

Thanks for wanting to improve these skills. Contributions are welcome from anyone
building products — especially if you've spotted jargon we missed, a pattern we
haven't covered, an accessibility check we should add, or a better way to say
something.

This document covers all skills in the collection. Find your skill below, or jump
to the shared sections that apply to all of them.

---

## Which skill are you contributing to?

- **[messaging-ux](#contributing-to-messaging-ux)** — words on every screen
- **[flow-ux](#contributing-to-flow-ux)** — the journey and screen order
- **[accessibility-ux](#contributing-to-accessibility-ux)** — who can actually use the product

Or skip ahead to [shared sections](#shared-sections) that apply to all three.

---

## Contributing to messaging-ux

### 1. Jargon swaps

Found a tech term that needs a plain-language alternative? Add it to the jargon
swap table in `SKILL.md`.

Format:

```
| [tech term] | [plain alternative] |
```

Good candidates:

- Terms specific to an industry (fintech, healthtech, devtools, e-commerce)
- New terms that emerged after the skill was written
- Terms that have better alternatives than what's currently listed

### 2. Component patterns

A UI component or moment we haven't covered yet. Each pattern needs:

- A name and short description
- The doubt test applied (when does this need copy? when is it self-explanatory?)
- At least one example per fun level (🎭 / 😊 / 🧱)
- Bad example (❌) and good example (✅)

### 3. Domain-specific jargon sections

If you work in a specific industry (legal, medical, finance, e-commerce, edtech),
you can contribute a domain jargon block — a focused table of terms common in that
space with plain-language alternatives.

Format:

```markdown
### [Industry] Jargon

| Avoid | Use instead |
|-------|-------------|
| ...   | ...         |
```

### 4. Page-aware rules

A new page type we haven't covered (settings, search, dashboard, etc.). Each needs:

- How to detect the page type (route patterns, component names, content patterns)
- The copy rules that apply specifically to this page type
- Examples following the format of existing page-aware sections

---

## Contributing to flow-ux

### 1. New flow patterns

A flow or journey we haven't covered. Each pattern needs:

- A name and the user moment it addresses (onboarding, error, upgrade, etc.)
- The principle behind it — what the flow is optimising for
- A flow skeleton: the steps in order, what each step does, what's deferred
- Bad pattern (❌) and good pattern (✅) — full flow shape, not just one screen
- The emotional state of the user at each step

### 2. Drop-off risk additions

A pattern that makes users abandon flows that we haven't flagged yet. Each needs:

- The specific behaviour or screen that causes drop-off
- Why it happens — what the user is thinking
- The fix — a concrete change that addresses the cause, not the symptom

### 3. Error recovery patterns

A new error scenario or recovery pattern. Each needs:

- The error type and likelihood (common / occasional / rare)
- The anxiety level (low / medium / high)
- Auto-recovery behaviour, user-visible message, primary action, fallback, escape hatch
- What still works when this fails (graceful degradation)

### 4. Offboarding additions

A new cancellation or deletion pattern. Each needs:

- The user state at this moment — why they're leaving
- The appropriate save offer (if any) for this reason
- The confirmation copy showing what happens to access and data
- The post-exit behaviour — win-back cadence, data deletion timing

### 5. Page-aware rules

A new flow type we should detect and apply rules to. Each needs:

- Detection signals (routes, components, content patterns)
- The relevant chapter the detection maps to

---

## Contributing to accessibility-ux

### 1. New framework or library patterns

We cover HTML, React, and Vue. If you have patterns for Svelte, Solid, Angular, or
a component library (Mantine, Ant Design, etc.), contribute them. Each needs:

- The framework or library name and version range it applies to
- The specific accessibility concern being addressed
- Bad pattern (❌) and good pattern (✅) — in the actual syntax of that stack
- Why this stack needs special handling (e.g. Vue's `v-model` on custom inputs)

### 2. New audit checks

An accessibility check we don't currently flag. Each needs:

- The severity level (🔴 Critical, 🟠 Serious, 🟡 Minor) and the rationale
- How to detect it — what to look for in code or rendered output
- What it blocks — which users are affected and how
- The fix — concrete code, not just a description

### 3. Accessibility level refinements

A rule that needs different treatment at 🟢 Baseline vs 🟡 Thorough vs 🔵 Comprehensive.
Each needs:

- The rule and which chapter it belongs in
- The Baseline approach (pragmatic, ship-fast)
- The Thorough approach (WCAG 2.1 AA)
- The Comprehensive approach (AAA + inclusive design)
- Why the levels diverge for this rule

### 4. Domain-specific accessibility patterns

If you work in a domain with specific accessibility requirements (healthcare,
education, government, financial services), contribute a focused section. Each
needs:

- The domain and the regulations or standards that apply (ADA, EAA, Section 508)
- Patterns that come up repeatedly in this domain
- Examples that show the right way to handle each

### 5. Page-aware rules

A page type we should detect and apply accessibility rules to. Each needs:

- Detection signals (routes, components, content patterns)
- Which chapters apply to this page type
- Why this combination matters for this page

---

## Shared sections

These apply to all three skills.

### Example profiles

A well-written profile for a fictional app (like `profiles/example.md`) helps others
understand the format and calibrate their own. Keep it fictional — don't submit
profiles for real products you don't own.

Profiles are shared across all three skills. A good profile contains:

- Audience, app type, vibe (used by messaging-ux and flow-ux)
- Accessibility level and tech stack (used by accessibility-ux)
- Jargon swaps specific to the product
- Example rewrites approved for the product
- Any flow notes, drop-off observations, or accessibility decisions already made

### Bug fixes and clarifications

If a rule is ambiguous, contradicts another rule, or produces bad output in
practice — open an issue or submit a fix with an explanation. Bug fixes are
welcome in any skill.

### Cross-skill alignment

If you find a moment where the three skills give conflicting advice, that's a
bug worth fixing. Open an issue with:

- The user moment or screen where the conflict shows up
- What each skill currently says
- A suggested reconciliation

---

## How to submit

1. Fork the repo
2. Make your changes in a branch — keep contributions to one skill per PR where
   possible (cross-skill changes are fine, just call them out)
3. Open a pull request with a short description of what you changed and why
4. Include a before/after example if you're changing rules — code for
   accessibility-ux, copy for messaging-ux, flow shape for flow-ux

---

## What we won't merge

- Rules that add jargon back in (the direction is always toward plain language)
- Patterns that are too product-specific to be reusable
- Contributions that compromise the human-centric philosophy
- Real product profiles or any real user data
- Accessibility patterns that prioritise compliance optics over actual usability
- Flow patterns that prioritise the system's needs over the user's progress

---

## Philosophy reminder

Every rule in every skill flows from one idea:

> Software should make sense to the humans using it — not just the people who
> built it.

Each skill applies it to a different layer:

- **messaging-ux** — does everyone understand this?
- **flow-ux** — can everyone navigate this?
- **accessibility-ux** — can everyone use this?

If your contribution serves the human on the other side, it belongs here.
