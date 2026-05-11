# README updates for shipping accessibility-ux

Four sections of the README need changes. Each is a small, targeted edit — no restructuring.

---

## Change 1: Available skills table

**Find this block:**

```markdown
| Skill | What it does | Best for |
| --- | --- | --- |
| [messaging-ux](https://github.com/srohan8/forhumans/blob/main/skills/messaging-ux.md) | Writes and audits all in-product copy through a human-centric lens — tooltips, errors, empty states, loading states, onboarding, notifications, pricing, and more | Anyone building a product |
| [flow-ux](https://github.com/srohan8/forhumans/blob/main/skills/flow-ux.md) | Designs and audits user journeys — onboarding flows, error recovery, progressive disclosure, and respectful offboarding | Anyone shipping a product to non-experts |
```

**Replace with:**

```markdown
| Skill | What it does | Best for |
| --- | --- | --- |
| [messaging-ux](https://github.com/srohan8/forhumans/blob/main/skills/messaging-ux.md) | Writes and audits all in-product copy through a human-centric lens — tooltips, errors, empty states, loading states, onboarding, notifications, pricing, and more | Anyone building a product |
| [flow-ux](https://github.com/srohan8/forhumans/blob/main/skills/flow-ux.md) | Designs and audits user journeys — onboarding flows, error recovery, progressive disclosure, and respectful offboarding | Anyone shipping a product to non-experts |
| [accessibility-ux](https://github.com/srohan8/forhumans/blob/main/skills/accessibility-ux.md) | Audits and fixes accessibility across cognitive load, visual, motor, screen reader, plain language, forms, and navigation — translated into plain language and concrete code | Anyone building for real humans |
```

---

## Change 2: The Siblings section

**Find this block:**

```markdown
### Siblings: messaging-ux and flow-ux

[#siblings-messaging-ux-and-flow-ux](#siblings-messaging-ux-and-flow-ux)

These two are designed to work together. **messaging-ux** handles what every screen *says*. **flow-ux** handles what screens *exist and in what order*. Use them together for a full UX layer, or independently for focused work.
```

**Replace with:**

```markdown
### The trio: messaging-ux, flow-ux, accessibility-ux

[#the-trio-messaging-ux-flow-ux-accessibility-ux](#the-trio-messaging-ux-flow-ux-accessibility-ux)

These three are designed to work together. **messaging-ux** handles what every screen *says*. **flow-ux** handles what screens *exist and in what order*. **accessibility-ux** handles whether *everyone can actually use those screens*. Use them together for a full UX layer, or independently for focused work.

Each answers a different question:

- messaging-ux — *does everyone understand this?*
- flow-ux — *can everyone navigate this?*
- accessibility-ux — *can everyone use this?*

They never overlap — each handles a different layer of the same product.
```

---

## Change 3: Installation curl block

**Find this block:**

```markdown
Then add individual skills:

    curl -o skills/messaging-ux.md https://raw.githubusercontent.com/srohan8/forhumans/main/skills/messaging-ux.md
    curl -o skills/flow-ux.md https://raw.githubusercontent.com/srohan8/forhumans/main/skills/flow-ux.md
```

**Replace with:**

```markdown
Then add individual skills:

    curl -o skills/messaging-ux.md https://raw.githubusercontent.com/srohan8/forhumans/main/skills/messaging-ux.md
    curl -o skills/flow-ux.md https://raw.githubusercontent.com/srohan8/forhumans/main/skills/flow-ux.md
    curl -o skills/accessibility-ux.md https://raw.githubusercontent.com/srohan8/forhumans/main/skills/accessibility-ux.md
```

---

## Change 4: One-click copy list

**Find this block:**

```markdown
Click any skill below to open the raw file — copy and paste into your Claude project:

- [messaging-ux](https://raw.githubusercontent.com/srohan8/forhumans/main/skills/messaging-ux.md)
- [flow-ux](https://raw.githubusercontent.com/srohan8/forhumans/main/skills/flow-ux.md)
```

**Replace with:**

```markdown
Click any skill below to open the raw file — copy and paste into your Claude project:

- [messaging-ux](https://raw.githubusercontent.com/srohan8/forhumans/main/skills/messaging-ux.md)
- [flow-ux](https://raw.githubusercontent.com/srohan8/forhumans/main/skills/flow-ux.md)
- [accessibility-ux](https://raw.githubusercontent.com/srohan8/forhumans/main/skills/accessibility-ux.md)
```

---

## What stays the same

- Tagline ("Claude skills built around people, not systems.") — already covers accessibility
- Philosophy section — already names accessibility in the closing line: *"Whether it's copy, onboarding, data, or accessibility..."*
- Product profiles section — accessibility-ux uses the same shared profile format, no changes needed
- Contributing section — no changes needed
- License — no changes needed

---

## Optional: a one-line update to the Philosophy section

The README's closing philosophy line currently reads:

> Whether it's copy, onboarding, data, or accessibility — the output of any skill here should make things clearer, simpler, and more human for the person on the other end.

This already calls out accessibility, so no change is strictly needed. But if you want it to feel less aspirational and more "this is shipped," you could change "or accessibility" to read more naturally now that there's a skill for it. Suggested:

> Whether it's words, journeys, or access — the output of any skill here should make things clearer, simpler, and more human for the person on the other end.

This change is optional. The original line still works.
