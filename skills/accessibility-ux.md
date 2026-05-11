---
name: accessibility-ux
description: >-
  Designs, reviews, and audits product accessibility through a human-centric
  lens. Covers — cognitive load, visual accessibility (contrast, colour-blind
  safety, focus, motion), motor accessibility (touch targets, keyboard
  navigation, time limits), screen reader support (semantic HTML, ARIA,
  alt text, live regions), plain language, form and input accessibility, and
  navigation and wayfinding. Use this skill whenever the user asks to make
  something accessible, audit accessibility, fix a11y issues, or build
  inclusively from the start. Trigger on — "make this accessible", "audit
  accessibility", "a11y review", "is this accessible", "WCAG compliance",
  "screen reader support", "keyboard navigation", "colour contrast", "focus
  states", "alt text", "aria-label", "skip nav", "tab order", "reduced motion",
  or any pasted code or screen asking whether it works for everyone. Also
  trigger when given access to a codebase and asked to improve accessibility,
  inclusivity, or usability for people with disabilities. Completes the
  forhumans trio with messaging-ux (does everyone understand this) and flow-ux
  (can everyone navigate this) — accessibility-ux handles can everyone use this.
  Always use this skill when accessibility is the subject.
---

# Accessibility UX Skill

## Core Philosophy: Human-Centric, Not Compliance-Centric

**Accessibility isn't a checklist to pass — it's a commitment to including everyone in what you build.**

If someone can't use your product because of how it's built — that's a bug, not an edge case. Not a "we'll get to it." Not a "that's a small percentage." A bug.

Compliance-centric accessibility asks *"did we pass the audit?"* Human-centric accessibility asks *"can the person on the other side actually use this?"* The first one optimises for a legal threshold. The second one optimises for a human.

| Compliance-centric | Human-centric |
|--------------------|---------------|
| "Did we pass WCAG?" | "Can everyone use this?" |
| Adds aria-labels to silence linters | Writes labels because screen reader users matter |
| Fixes what audits flag | Fixes what blocks real people |
| Treated as a separate phase before launch | Treated as part of every build |
| Optimised for the legal threshold | Optimised for the human on the other side |
| Measures coverage of rules | Measures whether someone got through |

This is the lens for every audit, every fix, every component built. If a screen works for the developer who built it but breaks for someone using a keyboard, screen reader, or magnifier — it's not done.

**accessibility-ux completes the forhumans trio.**

- **messaging-ux** decides *what every screen says.*
- **flow-ux** decides *what screens exist and in what order.*
- **accessibility-ux** decides *whether everyone can actually use those screens.*

The three never overlap — they handle different layers of the same problem. When auditing a product, all three apply: messaging-ux finds the unclear words, flow-ux finds the broken journeys, accessibility-ux finds who's locked out.

---

## Step 1: Detect Context — Don't Ask What You Can Infer

**If running inside a project or codebase**, read the code first and infer:

- **App name** — from package.json, README, or folder name
- **Product profile** — check `profiles/` for a matching `.md` file and load it (shared with messaging-ux and flow-ux)
- **Tech stack** — HTML, React, Vue, Svelte, Angular, Solid (from file extensions, imports, package.json). Every code suggestion must match the stack.
- **Component library** — shadcn/ui, Radix, Material UI, Chakra, Headless UI, Ant Design, or custom (from imports and class patterns). Some libraries are accessible by default — adjust advice accordingly.
- **Styling approach** — Tailwind, CSS modules, styled-components, vanilla CSS (affects the form of every fix you suggest)
- **Existing accessibility surface** — search for `aria-`, `role=`, `<main>`, `<nav>`, `<button>` vs `<div onClick>`, focus-visible styles, eslint-plugin-jsx-a11y, axe-core, `prefers-reduced-motion`. Establish baseline before recommending changes.
- **Audience** — infer from README, landing page, onboarding. A medical product, a kids' app, and a developer tool need different accessibility targets.

**Only ask if you genuinely can't infer.** Ask only what's missing — never all questions if some are clear.

### If no project context (standalone conversation)

Ask once:

> **What level of accessibility does your product need?**
>
> - 🟢 **Baseline** — the 20% of changes that fix 80% of accessibility issues. Pragmatic, ship-fast approach for solo founders. Covers the issues that lock people out entirely.
> - 🟡 **Thorough** — WCAG 2.1 AA compliance. Covers all major accessibility requirements. The standard most regulated industries and public services expect.
> - 🔵 **Comprehensive** — WCAG 2.1 AAA where achievable, plus inclusive design considerations beyond compliance. For products serving disability communities, public-sector work, or anywhere access is part of the mission.

**Default to 🟢 Baseline.** Most solo founders need the highest-impact fixes first, not the full spec. State which level is being applied and offer to upgrade if the project needs it.

You may also need to confirm tech stack if it can't be inferred — ask only what's missing.

Never ask the same question twice in a session.

### Product Profiles

Profiles are shared with messaging-ux and flow-ux. If a `profiles/` folder exists next to this SKILL.md, check for a file matching the current app name (e.g. `profiles/myapp.md`). If found, load it — it contains audience, app type, vibe, tech stack, and any accessibility notes already captured.

If no profile exists, infer what you can, ask only what's missing, and offer: *"Want me to save this as a profile so you don't have to answer these again?"* and create or update `profiles/[appname].md`.

When accessibility-ux adds to a profile, it adds: accessibility level (🟢/🟡/🔵), tech stack and component library, known accessibility decisions made (e.g. "we use Radix for all primitives — already keyboard-accessible"), and any product-specific patterns or overrides.

Profiles are per-project and never bundled into the shared skill file.

---

## Accessibility Level Calibration

| Level | What it means in practice |
|-------|----------------------------|
| 🟢 **Baseline** | Keyboard reachable, every input has a visible label, alt text on meaningful images, contrast at least 4.5:1 for body text, focus visible, colour never used alone, touch targets at least 44px, no autoplay audio, no keyboard traps. Skip the rest until v2. |
| 🟡 **Thorough** | Everything in Baseline, plus: correct heading hierarchy, ARIA live regions for dynamic content, skip navigation, reduced-motion support, error messages tied to fields, autocomplete attributes, fieldset/legend for grouped inputs, contrast at least 3:1 for large text and UI components, full screen reader testing. |
| 🔵 **Comprehensive** | Everything in Thorough, plus: AAA contrast (7:1 body, 4.5:1 large), reading level at grade 8 or below, no time limits or generous extensions offered, audio descriptions for video, sign language alternatives where relevant, context-sensitive help, identification of unusual words and abbreviations. |

**When unsure, default to 🟢 Baseline.** Tell the user which level is being applied. Offer to upgrade when the product context warrants it — public sector, health, education, or audiences that include older users or disability communities all warrant Thorough at minimum.

---

## The Golden Rules of Accessibility

1. **If you can't reach it with a keyboard, half your users can't reach it.** Tab to every interactive element. Activate it with Enter or Space. If anything is unreachable, it's broken — not a polish issue.

2. **Every input has a visible label.** Placeholders are not labels. Floating labels that vanish on focus are not labels. Icons next to a field are not labels.

3. **Colour is never the only signal.** Red text needs an icon. A green badge needs a word. "Required fields are in red" is a defect, not a style.

4. **Focus must be visible.** Removing the focus ring without replacing it isn't a design choice — it's a critical bug. Keyboard users navigate by following the focus.

5. **Semantic HTML before ARIA.** A `<button>` beats `<div role="button" tabindex="0" onClick>` every time. ARIA fills gaps HTML can't fill — it isn't a substitute for using the right element.

6. **Errors say what to do, not just what went wrong** — and they're attached to the field that broke, not floating at the top of the page.

7. **Touch targets are at least 44×44px on mobile.** Spacing between targets matters too. Tremors, fat fingers, small screens, motion — all real.

8. **Test it the way users use it.** Tab through the page. Turn on the screen reader. Zoom to 200%. Disable colour. If it breaks, it's broken — regardless of what the linter says.

---

## Chapter 1: Cognitive Load

**The job of every screen is to reduce thinking, not show capability.** Cognitive accessibility is the most universal pillar — everyone is sometimes tired, distracted, stressed, or working in a second language. Designing for cognitive load benefits everyone.

### One Decision Per Screen, One Action Per Moment

If a screen presents five primary buttons, it has no primary button. Decide which action matters most. Make that one prominent. Make the others secondary, or move them off this screen entirely.

- **One primary action per screen.** Visually dominant. Unmistakable.
- **Secondary actions exist but don't compete.** Outlined, ghost, or text styles.
- **Tertiary actions live in menus.** Not on the main canvas.

### Chunking Information

A settings page with 47 toggles is not accessible — even if every toggle is labelled correctly. Cognitive load comes from quantity as much as from complexity.

The pattern:

- Group related settings into sections of 5–7 items maximum
- Hide less-common settings behind progressive disclosure (collapsed sections, "advanced" panels)
- Lead each section with a one-sentence purpose so the user knows whether to read it
- Never present a wall of 30+ form fields on one screen — split into steps if the form is long, group with `fieldset`/`legend` if it must stay on one screen

```html
<!-- HTML: collapsed advanced settings -->
<details>
  <summary>Advanced settings</summary>
  <!-- secondary options live here -->
</details>
```

```jsx
// React with shadcn/Radix: secondary options hidden by default
<Accordion type="single" collapsible>
  <AccordionItem value="advanced">
    <AccordionTrigger>Advanced settings</AccordionTrigger>
    <AccordionContent>{/* secondary options */}</AccordionContent>
  </AccordionItem>
</Accordion>
```

```vue
<!-- Vue: same idea -->
<details>
  <summary>Advanced settings</summary>
  <SecondaryOptions />
</details>
```

### Reading Level

Aim for a grade 8 reading level for body content. Test with Hemingway Editor, readable.io, or the Flesch-Kincaid score in most writing tools.

- Sentences under 20 words
- Common words over rare ones
- Active voice over passive
- One idea per sentence — if there's a comma, consider splitting

Long sentences are barriers for non-native speakers, people with cognitive disabilities, anyone reading on a phone, and anyone tired. They aren't sophistication — they're friction.

(messaging-ux handles the exact wording — accessibility-ux ensures reading level is part of the bar.)

### Consistency Over Cleverness

If "Save" is bottom-right on one page and bottom-left on another, the user has to think every time. Same interaction, same place, every time. This is invisible work that compounds across a session.

- Same component does the same thing everywhere
- Same shortcut works on every screen
- Same destructive action looks the same and behaves the same
- Don't invent novel interaction patterns when standard ones work

### Don't Make Users Remember

Memory load is invisible work. If a user entered something on step 1, show it on step 4. If they made a choice earlier, don't make them repeat it. If they're filling out a form, save their progress.

- Multi-step flows: show what was entered in earlier steps
- Auto-save drafts and tell the user ("Draft saved")
- Pre-fill known fields (autocomplete attributes, see Chapter 6)
- Never make the user repeat information you already have

### Avoid Unnecessary Time Limits

Sessions that silently expire while a user is reading a form are hostile. If a time limit is necessary:

- Warn at least 20 seconds before it expires
- Offer "Give me more time" — and honour it
- Never use time limits on reading content, forms, or anything that requires thought
- For 🔵 Comprehensive: eliminate time limits entirely except where legally required (e.g. real-time auctions)

### Cognitive Load Output Format

When auditing or designing for cognitive load:

```
SCREEN: [Screen name]
LEVEL: [🟢 / 🟡 / 🔵]

DECISIONS ON THIS SCREEN: [count]
PRIMARY ACTION: [What it should be]
COMPETING ACTIONS: [What else is fighting for attention — should be downgraded]

INFORMATION DENSITY:
  Sections: [count]
  Items per section: [average / max]
  Progressive disclosure used for: [list]

READING LEVEL:
  Current: [grade X]
  Target: [grade 8 or lower]
  Notes: [longest sentences, jargon to swap — refer to messaging-ux]

MEMORY LOAD:
  Things the user must remember from earlier screens: [list]
  Fix: [how to surface or eliminate each]
```

---

## Chapter 2: Visual Accessibility

**Visual accessibility goes far beyond "make the text bigger."** It covers contrast, colour-blindness, focus, motion, scaling, and whether the same screen works in both light and dark mode.

### Colour Contrast

Minimum ratios:

| Content | 🟢 Baseline / 🟡 AA | 🔵 AAA |
|---------|--------------------|--------|
| Body text (under 18pt or 14pt bold) | 4.5:1 | 7:1 |
| Large text (18pt+ or 14pt bold+) | 3:1 | 4.5:1 |
| UI components, icons, focus rings | 3:1 | 3:1 |

Test with: WebAIM Contrast Checker, axe DevTools (free Chrome extension), Chrome DevTools → Lighthouse → Accessibility, or `npm install -g pa11y`.

**Common failures to look for:**

- Light grey placeholder text on white (`#9CA3AF` on `#FFFFFF` = 2.8:1 — fails)
- White text on a brand colour that's "almost dark enough" — check before shipping
- Disabled-state colours being used for active text
- Hover states tested in light mode, never checked in dark mode
- Icons that fail contrast even if surrounding text passes

```css
/* Don't ship without checking these */
:root {
  --text-body: #1a1a1a;       /* 16:1 on white ✓ */
  --text-muted: #6b7280;       /* 5.7:1 on white ✓ — good */
  --text-placeholder: #9ca3af; /* 2.8:1 on white ✗ — fix */
}
```

### Colour-Blind Safe Design

About 1 in 12 men and 1 in 200 women have some form of colour vision deficiency. Never use colour as the only signal.

```html
<!-- ❌ Bad: only the red border signals error -->
<input class="border-red-500" />

<!-- ✅ Good: colour + icon + text + ARIA -->
<input
  class="border-red-500"
  aria-invalid="true"
  aria-describedby="email-err"
/>
<p id="email-err" class="text-red-600">
  <Icon name="alert" aria-hidden="true" /> Email is required
</p>
```

For charts and data viz:

- Lines and bars distinguished by colour also need patterns, shapes, or direct labels
- Status badges have a word, not just a dot
- Map regions need text on hover, not just hue
- Test with a colour-blindness simulator (Stark, Colorblindly browser extension, or macOS Display Accommodations)

### Text Sizing

- Body text minimum **16px**. Smaller is uncomfortable for everyone and unreadable for some.
- Use relative units (`rem`, `em`) — hard-coded `px` everywhere breaks user text scaling
- Layout must survive **200% zoom** without horizontal scrolling
- Line length: 50–75 characters for body copy. Wider lines lose readers between lines.

```css
/* Don't */
body { font-size: 14px; }
h1 { font-size: 32px; }

/* Do — scales with user preferences */
html { font-size: 100%; } /* respects browser default */
body { font-size: 1rem; }  /* = 16px by default, scales with user setting */
h1 { font-size: 2rem; }
```

### Focus Indicators

Removing the focus ring without replacing it is a critical accessibility bug.

```css
/* ❌ Critical bug — keyboard users are now lost */
*:focus { outline: none; }

/* ✅ Visible, consistent, high contrast */
:focus-visible {
  outline: 2px solid var(--focus-color);
  outline-offset: 2px;
  border-radius: 2px;
}

/* Tip: focus-visible only shows when navigating by keyboard,
   so mouse clicks don't get the ring. Best of both worlds. */
```

Focus rings should contrast at least 3:1 against the surrounding background. Test in both light and dark mode — a ring that's visible on white can disappear on black.

### Animation and Motion

People with vestibular disorders can experience nausea, dizziness, and migraine from motion. Respect their system preference:

```css
/* Respect the user's system setting — applies app-wide */
@media (prefers-reduced-motion: reduce) {
  *,
  *::before,
  *::after {
    animation-duration: 0.01ms !important;
    animation-iteration-count: 1 !important;
    transition-duration: 0.01ms !important;
    scroll-behavior: auto !important;
  }
}
```

```jsx
// React: detect the preference and conditionally render
const prefersReducedMotion = window.matchMedia(
  '(prefers-reduced-motion: reduce)'
).matches;

<Component animate={!prefersReducedMotion} />
```

Beyond the toggle:

- Never put essential information only in animation — auto-scrolling carousels lose users who can't keep up
- Avoid auto-playing video with motion above the fold
- Parallax scrolling needs a reduced-motion fallback
- Spinning loaders are usually fine, but flashing or rapid movement is not — never flash more than 3 times per second

### Light and Dark Mode

Both modes need separate accessibility checks. A 4.5:1 ratio in light mode often becomes 3.1:1 in dark.

- Test contrast in *both* modes — not just the one you designed first
- Pure white on pure black is harsh and triggers halation for people with astigmatism. Use off-white (`#F5F5F5`) on near-black (`#0F0F0F`)
- Images and icons designed for light mode may invert poorly. Provide dark-mode versions if needed
- Don't auto-switch based on time of day — respect the user's system setting

### Visual Accessibility Output Format

```
SCREEN: [Screen name]
LEVEL: [🟢 / 🟡 / 🔵]

CONTRAST AUDIT:
  Body text on background: [X:Y ratio] — [pass / fail]
  Muted text on background: [X:Y ratio] — [pass / fail]
  Buttons / UI elements: [X:Y ratio] — [pass / fail]
  Tested in: [light / dark / both]

COLOUR-ONLY SIGNALS FOUND:
  [Component] uses colour alone — add: [icon / text / pattern]

FOCUS:
  Visible: [yes / no / partial]
  Contrast against background: [ratio]
  Consistent across components: [yes / no]

MOTION:
  prefers-reduced-motion supported: [yes / no]
  Auto-playing animations: [list]

SCALING:
  200% zoom intact: [yes / no — horizontal scroll appears at X%]
  Uses relative units: [yes / no]
```

---

## Chapter 3: Motor Accessibility

**Not everyone uses a mouse, and not everyone has steady hands.** Motor accessibility covers keyboard navigation, touch targets, and giving users time and alternatives.

### Touch Target Sizing

- **Minimum 44×44px** tap area on mobile (Apple HIG) — about 48×48dp on Android (Material)
- Spacing between targets matters as much as size — at least 8px gap between tappable items
- For interactive elements smaller than 44px visually, extend the hit area with padding or `::before` overlays

```css
/* Visually small icon button, but tap area is full size */
.icon-button {
  width: 24px;
  height: 24px;
  padding: 10px; /* total hit area now 44×44 */
  position: relative;
}
```

```jsx
// React: extending hit area without affecting layout
<button
  className="relative w-6 h-6 before:absolute before:inset-[-10px] before:content-['']"
  aria-label="Close dialog"
>
  <CloseIcon />
</button>
```

### Keyboard Navigation

Everything interactive must be reachable and operable by keyboard:

| Element | Expected keyboard behaviour |
|---------|------------------------------|
| Buttons, links | Tab to focus, Enter or Space to activate |
| Form fields | Tab to focus, type to enter, Tab to leave |
| Checkboxes, toggles | Tab to focus, Space to toggle |
| Radio groups | Tab into group, arrow keys between options |
| Dropdowns / selects | Tab to focus, Space to open, arrow keys, Enter to select |
| Modals / dialogs | Focus trapped inside while open, Escape closes |
| Custom widgets | Match the closest standard pattern — never invent |

```jsx
// ❌ Looks like a button, isn't reachable by keyboard
<div onClick={handleClick} className="button">Save</div>

// ✅ Real button — keyboard, screen reader, all of it free
<button onClick={handleClick} className="button">Save</button>

// ✅ If you must use a div (you almost never must),
// you have to manually provide everything a button gives you
<div
  role="button"
  tabIndex={0}
  onClick={handleClick}
  onKeyDown={(e) => {
    if (e.key === 'Enter' || e.key === ' ') {
      e.preventDefault();
      handleClick();
    }
  }}
  className="button"
>
  Save
</div>
```

The lesson: **use the right HTML element, save yourself the work.**

### Tab Order

Tab order must follow the visual reading order. The DOM order is the tab order — don't fight it with `tabindex` values above 0.

- `tabindex="0"` — element joins the natural tab order (use sparingly, only for non-interactive elements that need focus)
- `tabindex="-1"` — element is focusable programmatically but not via Tab (used for managing focus in modals, error scrolling)
- `tabindex="1"` or higher — **never use.** Breaks the natural order and creates unpredictable navigation

If the visual order doesn't match the DOM order, fix the DOM (or the visual). Reordering via CSS Grid or Flexbox `order` is an accessibility trap — it changes what users see but not what the keyboard follows.

### Skip Navigation

The first focusable element on every page should be a "Skip to main content" link. Without it, keyboard users have to Tab through the entire nav on every page.

```html
<body>
  <a href="#main" class="skip-link">Skip to main content</a>
  <nav>...</nav>
  <main id="main">...</main>
</body>
```

```css
/* Visible only when focused */
.skip-link {
  position: absolute;
  left: -9999px;
  top: 0;
}
.skip-link:focus {
  left: 0;
  background: var(--surface);
  padding: 12px 16px;
  z-index: 999;
}
```

### Drag and Drop

Drag-and-drop is inaccessible by default. Always provide a keyboard/click alternative.

- A Kanban board: drag cards between columns, *and* a "Move to..." menu with a list of columns
- File upload: drag in files, *and* a "Browse" button that opens the file picker
- Reorderable list: drag handles, *and* up/down arrow buttons or a "Move" action

Libraries that get this right by default: dnd-kit (with keyboard sensors enabled), React Aria's `useDrag`/`useDrop`. Libraries that don't: react-beautiful-dnd needs explicit setup, plain HTML5 drag-and-drop has no keyboard support.

### Time Limits

If something times out, the user must be:

- Warned at least 20 seconds before it expires
- Offered "Extend time" or "Give me more"
- Allowed to disable the time limit entirely (🔵 Comprehensive)

Never time out destructive confirmations, payment flows, or forms with significant content. The user is reading or typing — interrupting them risks data loss.

### Motor Accessibility Output Format

```
SCREEN: [Screen name]
LEVEL: [🟢 / 🟡 / 🔵]

TOUCH TARGETS:
  Smallest target found: [X×Y px]
  Targets below 44px: [list]
  Spacing between adjacent targets: [pass / fail]

KEYBOARD NAVIGATION:
  All interactive elements reachable by Tab: [yes / no]
  Custom widgets using divs as buttons: [list]
  Keyboard traps found: [list]
  Modal focus management: [trapped / not trapped / no modals]

TAB ORDER:
  Matches visual order: [yes / no]
  Uses tabindex > 0: [no — good / yes — fix]
  Skip link present: [yes / no]

DRAG AND DROP:
  Drag interactions found: [list]
  Keyboard alternative for each: [yes / no / partial]

TIME LIMITS:
  Time-bounded screens: [list]
  Warnings before expiry: [yes / no / partial]
  Extension offered: [yes / no]
```

---

## Chapter 4: Screen Reader Support

**Screen reader users navigate by structure.** Headings, landmarks, lists, tables, and labels are the map. Semantic HTML gives them the map for free. ARIA is for the rare cases when HTML can't.

### Semantic HTML First

The shortest path to screen reader support is using the right HTML element.

| Use | Not |
|-----|-----|
| `<button>` | `<div onClick>` |
| `<a href>` | `<span onClick>` |
| `<nav>` | `<div class="nav">` |
| `<main>` | `<div id="main">` |
| `<h1>` to `<h6>` | `<div class="title">` |
| `<ul>` / `<ol>` / `<li>` | `<div>` lists |
| `<label>` | placeholder text |
| `<table>` for tabular data | `<div>` grids |

Every native element comes with keyboard support, focus behaviour, screen reader announcements, and form integration for free. ARIA is the duct tape — and duct tape only works if you put it on correctly. Native HTML works by default.

### Heading Hierarchy

Screen reader users jump from heading to heading to navigate a page — like skimming a table of contents. Broken hierarchy makes that impossible.

- One `<h1>` per page (the page title)
- Never skip levels (`<h1>` → `<h3>` skips `<h2>` — broken)
- Headings describe sections, not styles. Don't pick `<h3>` because you want smaller text — pick it because it's a sub-section of an `<h2>`
- If you need smaller text, use CSS. Heading levels are structural.

```html
<!-- ❌ Skips from h1 to h3, breaks the outline -->
<h1>Settings</h1>
<h3>Notifications</h3>

<!-- ✅ Logical outline -->
<h1>Settings</h1>
<h2>Notifications</h2>
<h3>Email preferences</h3>
```

### Landmarks and Regions

Landmark elements let screen reader users jump to the major regions of a page. Use them.

```html
<header>...</header>          <!-- top of page -->
<nav>...</nav>                 <!-- primary navigation -->
<main>...</main>               <!-- main content — only one per page -->
<aside>...</aside>             <!-- complementary content -->
<footer>...</footer>           <!-- bottom of page -->
```

If you have multiple navs (primary, footer, in-content), label them:

```html
<nav aria-label="Primary">...</nav>
<nav aria-label="Footer">...</nav>
```

### ARIA Labels

ARIA labels describe what something does, in plain language, for a screen reader. Used when the visible text isn't enough — or when there isn't any.

- **Describe the action, not the icon.** `aria-label="Edit project name"`, not `aria-label="pencil icon"`
- **One label per element.** Don't combine `aria-label` and `aria-labelledby` on the same element.
- **Don't duplicate the visible text.** If a button says "Save," it doesn't need `aria-label="Save button"`.
- **Use `aria-label` for icon-only controls.** Use `aria-labelledby` when another element on the page already describes this one.

```jsx
// ❌ Describes the icon, not the action
<button aria-label="trash icon"><TrashIcon /></button>

// ✅ Describes the action
<button aria-label="Delete project"><TrashIcon /></button>

// ✅ When text is visible, no aria-label needed
<button><TrashIcon /> Delete project</button>

// ✅ Decorative icon — hide it from the screen reader
<button>
  <TrashIcon aria-hidden="true" />
  Delete project
</button>
```

### ARIA Live Regions

For content that updates without a page reload — toasts, loading states, error banners, validation, search results — screen readers need to be told about the change.

```html
<!-- Polite — announces when the screen reader is idle.
     Use for most notifications. -->
<div aria-live="polite" aria-atomic="true">
  Draft saved
</div>

<!-- Assertive — interrupts the user. Use only for urgent issues
     like a payment failure or destructive action confirmation. -->
<div aria-live="assertive" role="alert">
  Payment failed — your card wasn't charged
</div>
```

```jsx
// React: a toast region that announces every new toast
function ToastRegion({ messages }) {
  return (
    <div aria-live="polite" aria-atomic="true">
      {messages.map((m) => <p key={m.id}>{m.text}</p>)}
    </div>
  );
}
```

For loading states:

```html
<!-- Tell the screen reader the content is loading -->
<div aria-busy="true" aria-live="polite">
  <Skeleton />
</div>

<!-- And when it's done -->
<div aria-busy="false">
  <Content />
</div>
```

### Image Alt Text

- **Informational images** — describe what matters: `alt="Sales graph showing 23% growth in Q3"`
- **Decorative images** — use empty alt: `alt=""` (the screen reader skips it). Never omit the attribute entirely.
- **Functional images** (a logo that's also a link) — describe the function: `alt="Home"`, not `alt="company logo"`
- **Complex images** (charts, diagrams) — short alt + a longer description nearby in the page

```html
<!-- Informational -->
<img src="chart.png" alt="Revenue grew from $12k to $48k between Jan and June 2026." />

<!-- Decorative -->
<img src="divider-pattern.svg" alt="" />

<!-- Functional -->
<a href="/"><img src="logo.svg" alt="Home" /></a>

<!-- Don't do this — screen readers announce the filename -->
<img src="hero-photo-final-v2.jpg" />
```

### Tables

Tables are for tabular data. Not for layout — never for layout.

```html
<table>
  <caption>Monthly revenue, last 6 months</caption>
  <thead>
    <tr>
      <th scope="col">Month</th>
      <th scope="col">Revenue</th>
      <th scope="col">Change</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th scope="row">January</th>
      <td>$12,400</td>
      <td>+8%</td>
    </tr>
  </tbody>
</table>
```

Key parts: `<caption>` describes the table, `<th scope>` tells the screen reader whether a header is for a column or a row. Without `scope`, the screen reader has to guess.

### Reading Order

The DOM order *is* the reading order. CSS positioning (`order`, `flex-direction: reverse`, absolute positioning) can move things visually without changing what the screen reader sees — that's a trap.

If you reorder visually, also reorder the DOM. If the DOM order matches the visual order, you don't need to think about it.

### Screen Reader Output Format

```
SCREEN: [Screen name]
LEVEL: [🟢 / 🟡 / 🔵]

SEMANTIC HTML:
  Buttons using <button>: [yes / no / partial — list violations]
  Links using <a>: [yes / no / partial]
  Headings present: [yes / no]
  Landmarks present: [main / nav / header / footer — list which]

HEADING HIERARCHY:
  h1 count: [should be 1]
  Skipped levels found: [list — e.g. h1 → h3 in pricing section]
  Headings used for styling, not structure: [list]

ARIA:
  Icon-only buttons without aria-label: [list]
  Decorative icons not hidden from SR: [list]
  Live regions for dynamic content: [present / missing]

IMAGES:
  Images without alt: [list]
  Decorative images with descriptive alt: [list — should be alt=""]
  Functional images with poor alt: [list]

TABLES:
  Tables for layout (anti-pattern): [list]
  Data tables without caption / scope: [list]

READING ORDER:
  DOM matches visual: [yes / no — list mismatches]
```

---

## Chapter 5: Plain Language

**Plain language is accessibility.** It serves cognitive disabilities, non-native speakers, anyone tired or distracted, and the user reading on a 5-inch phone in the rain. Writing for the lowest common reading level isn't dumbing down — it's clearing the road.

### Target Grade 8 or Lower

For consumer products and public-facing content, grade 8 reading level is the target. Tools that measure: Hemingway Editor, readable.io, hemingwayapp.com, or built-in scores in Microsoft Word and Grammarly.

For technical products with a developer audience, grade 10–12 is fine. For 🔵 Comprehensive in regulated industries (health, government), aim for grade 6.

### Sentence Length

Keep sentences under 20 words. If a sentence has a comma, it can usually be split. If it has two commas, it should be.

- ❌ "Our service, which is designed for small businesses that need a simple way to manage invoices, lets you send up to 5 invoices per month on the free plan, with unlimited invoices available on Pro."
- ✅ "Send up to 5 invoices a month on the free plan. Need more? Pro gives you unlimited."

### Avoid Idioms, Metaphors, and Cultural References

These don't translate. They confuse non-native speakers, people with autism, and anyone unfamiliar with the source culture.

- ❌ "Hit it out of the park" → ✅ "Great work"
- ❌ "Piece of cake" → ✅ "Easy"
- ❌ "Drop the ball" → ✅ "Make a mistake"
- ❌ "Touch base" → ✅ "Talk to"
- ❌ "Above and beyond" → ✅ "More than expected"

Sports metaphors, military metaphors, food metaphors — all of them fail somewhere. Use plain words.

### Spell Out Acronyms on First Use

- ❌ "Configure your SSO settings"
- ✅ "Configure your Single Sign-On (SSO) settings" — first use only; subsequent uses can be just "SSO"

For technical audiences with stable jargon (API, URL, HTML), don't spell out the obvious. For non-technical audiences, spell out almost everything.

### Active Voice Over Passive

Active voice is shorter, clearer, and easier to translate.

- ❌ "Your data is being processed by our servers." (passive)
- ✅ "We're processing your data." (active)

- ❌ "An error was encountered when the file was uploaded." (passive)
- ✅ "We couldn't upload your file." (active)

### Instructions That Work Without Seeing the Screen

A screen reader user can't see "the blue button on the right." Refer to interactive elements by their label, not their visual position or appearance.

- ❌ "Click the blue button to continue"
- ✅ "Click **Save changes** to continue"

- ❌ "Tap the icon in the top-right corner"
- ✅ "Tap **Settings**" (and ensure the settings icon has `aria-label="Settings"`)

- ❌ "Look for the red banner"
- ✅ "Look for the message at the top of the page"

### The Words to Avoid

These words make struggling users feel worse:

- "simply", "just", "easy", "obviously", "of course" — if it were simple, the user wouldn't be reading the help text
- "merely", "trivially" — same problem
- "user" in user-facing copy — say "you" instead (this is conversational, not documentation)

### Plain Language Output Format

```
CONTENT: [What's being audited]
LEVEL: [🟢 / 🟡 / 🔵]
TARGET READING LEVEL: [Grade X — based on level]
CURRENT READING LEVEL: [Measured grade]

LONG SENTENCES (>20 words):
  [Sentence] — suggested split: [reword]

IDIOMS / METAPHORS FOUND:
  [Phrase] — replace with: [plain]

UNDEFINED ACRONYMS:
  [Acronym] — spell out on first use

PASSIVE VOICE:
  [Sentence] — active version: [reword]

VISUAL-DEPENDENT INSTRUCTIONS:
  [Instruction referring to colour / position] — accessible version: [reword]

CONDESCENDING WORDS:
  "[word]" found in [location] — remove or rephrase

(For the exact rewrites, refer to messaging-ux.)
```

---

## Chapter 6: Forms & Input Accessibility

**Forms are where accessibility most often breaks** — and where the consequences of breaking it are highest. A user who can't fill out a form can't sign up, can't pay, can't get help.

### Every Field Has a Visible Label

Placeholders are not labels. Floating labels that disappear on focus are not labels. Tooltips that appear on hover are not labels.

```html
<!-- ❌ Placeholder as label — vanishes when typing, fails for screen readers -->
<input type="email" placeholder="Email" />

<!-- ❌ Label visually hidden but technically there — only works if hiding is done correctly -->
<input type="email" aria-label="Email" />

<!-- ✅ Visible label, associated with the input -->
<label for="email">Email</label>
<input id="email" type="email" />

<!-- ✅ Same idea, wrapped -->
<label>
  Email
  <input type="email" />
</label>
```

For floating-label patterns: make sure the label stays visible (above the input) once the field has content. Don't replace the label with the value — the label is *what the field is*, the value is *what the user typed*.

### Error Messages Attached to the Field

A user with a screen reader can't see a red border or a red error summary at the top of the page. Errors must be programmatically tied to the field that broke.

```html
<label for="email">Email</label>
<input
  id="email"
  type="email"
  aria-invalid="true"
  aria-describedby="email-error"
/>
<p id="email-error" role="alert">
  Email is required
</p>
```

When the screen reader focuses the input, it announces: *"Email, edit, invalid entry. Email is required."* That's the goal — the user knows what went wrong without having to navigate elsewhere.

```jsx
// React with react-hook-form or similar
<label htmlFor="email">Email</label>
<input
  id="email"
  type="email"
  aria-invalid={!!errors.email}
  aria-describedby={errors.email ? 'email-error' : undefined}
  {...register('email', { required: 'Email is required' })}
/>
{errors.email && (
  <p id="email-error" role="alert">{errors.email.message}</p>
)}
```

### Autocomplete Attributes

The `autocomplete` attribute lets browsers and password managers fill in known data. This is a huge win for users with motor disabilities, cognitive disabilities, or anyone using a screen reader.

```html
<input type="email" autocomplete="email" />
<input type="text" autocomplete="given-name" />
<input type="text" autocomplete="family-name" />
<input type="tel" autocomplete="tel" />
<input type="text" autocomplete="street-address" />
<input type="text" autocomplete="postal-code" />
<input type="password" autocomplete="current-password" />
<input type="password" autocomplete="new-password" />
<input type="text" autocomplete="cc-number" />
```

Full list: HTML spec section on autofill. Use the right value — not just `autocomplete="on"`.

### Fieldset and Legend for Grouped Inputs

Radio groups, checkbox groups, and related inputs need a group label.

```html
<fieldset>
  <legend>Notification preferences</legend>

  <label>
    <input type="checkbox" name="notif" value="email" />
    Email
  </label>

  <label>
    <input type="checkbox" name="notif" value="sms" />
    SMS
  </label>

  <label>
    <input type="checkbox" name="notif" value="push" />
    Push
  </label>
</fieldset>
```

The screen reader announces the legend before each checkbox, giving context. Without `fieldset`/`legend`, the user just hears "checkbox, email" with no indication of what the group is for.

### Required vs Optional

Most fields in most forms are required. Flagging the few optional ones is cleaner than marking everything with red asterisks.

```html
<!-- ✅ Flag the optional ones, not the required ones -->
<label for="phone">Phone <span class="optional">(optional)</span></label>
<input id="phone" type="tel" />
```

For required fields, the asterisk pattern is fine — but make sure it isn't the only signal:

```html
<label for="email">Email <span aria-hidden="true">*</span></label>
<input id="email" type="email" required aria-required="true" />
```

The `required` attribute plus `aria-required="true"` makes the screen reader announce it. The visible asterisk is for sighted users.

### Inline Validation

Tell users about errors *before* they submit, not just after. But:

- Don't validate on every keystroke — wait until the field blurs or the user clearly finished
- Don't validate empty fields on first focus — wait until they've typed something or moved on
- Keep error messages near the field, not floating at the top

The right pattern: validate on blur for format issues (email, phone), validate on submit for required fields, validate immediately for fields with constraints (password strength, character count remaining).

### Forms Output Format

```
FORM: [Form name / location]
LEVEL: [🟢 / 🟡 / 🔵]

LABELS:
  Fields without visible labels: [list]
  Placeholder-as-label patterns found: [list]
  All labels programmatically associated: [yes / no — list violations]

ERRORS:
  Errors attached to fields via aria-describedby: [yes / no]
  Errors announced (role="alert" or live region): [yes / no]
  aria-invalid set on broken fields: [yes / no]

AUTOCOMPLETE:
  Fields with autocomplete attribute: [count / total]
  Missing autocomplete on: [list of fields where it would help]

GROUPING:
  Radio / checkbox groups without fieldset+legend: [list]

REQUIRED / OPTIONAL:
  Pattern used: [flag optional / flag required]
  required attribute present: [yes / no]

VALIDATION TIMING:
  When errors appear: [on every keystroke / on blur / on submit]
  Fix: [list specific changes]
```

---

## Chapter 7: Navigation & Wayfinding

**Users need to know where they are, how they got there, and how to get somewhere else.** Wayfinding is what turns a collection of screens into something navigable.

### Page Titles

Every page needs a unique, descriptive `<title>`. This shows up in the browser tab, in the screen reader's first announcement on each page, in bookmarks, in search results.

```html
<!-- ❌ Same title on every page -->
<title>My App</title>

<!-- ✅ Page-specific, then app name -->
<title>Invoice #1042 — Acme Corp — My App</title>
<title>Settings — My App</title>
<title>Dashboard — My App</title>
```

For single-page apps (React, Vue, etc.), update the title on route change:

```jsx
// React with React Helmet, or manually
useEffect(() => {
  document.title = `${pageName} — My App`;
}, [pageName]);
```

### Breadcrumbs

Breadcrumbs answer two questions: where am I, and how did I get here.

```html
<nav aria-label="Breadcrumb">
  <ol>
    <li><a href="/">Home</a></li>
    <li><a href="/invoices">Invoices</a></li>
    <li aria-current="page">Invoice #1042</li>
  </ol>
</nav>
```

Use breadcrumbs when:

- The site has clear hierarchy (more than 2 levels deep)
- Users may arrive on a deep page from search and need orientation
- The flow is non-linear and users may have come from multiple paths

Don't use breadcrumbs for flat sites or single-section apps — they add noise without value.

### Consistent Navigation

Primary navigation should be in the same place on every page, with the same items, in the same order. Users learn the location once.

- Same nav, same place, every page
- Current page indicated visually *and* via `aria-current="page"`
- Logo links to home — universal convention, don't fight it

```html
<nav aria-label="Primary">
  <ul>
    <li><a href="/dashboard">Dashboard</a></li>
    <li><a href="/invoices" aria-current="page">Invoices</a></li>
    <li><a href="/clients">Clients</a></li>
  </ul>
</nav>
```

### Current Page Indicator

Users should always know where they are. Not just visually — programmatically too.

- `aria-current="page"` on the current nav item
- Visual indicator that's not colour alone (underline, bold, indicator bar)
- Page title matches the nav item label

### Back Button Behaviour

The browser back button should always work predictably. This sounds obvious — but single-page apps break it constantly.

- Every meaningful state change updates the URL
- Back button returns to the previous meaningful state
- Modals that need to be dismissible by back button should push history
- Don't trap users in flows where back button breaks the app

For single-page apps, use proper routing (React Router, Next.js, Vue Router) — never manage state internally without updating the URL.

### Error Pages (404, 500)

Error pages are full pages too — they need to be accessible and helpful.

A good 404 has:

- A clear heading: "Page not found"
- A plain explanation: "The page you were looking for doesn't exist or has moved."
- Useful next steps: link to home, search box, link to recent or popular pages
- Standard navigation still present — don't strip it on error pages
- Proper semantic HTML and landmarks — `<main>` still wraps the content

A good 500 has:

- A clear heading: "Something went wrong"
- Honest acknowledgment: "We're looking into it."
- A way out: link to home, "try again" if relevant
- No technical detail visible to the user — stack traces go to the logs

(Refer to messaging-ux for the exact wording on error pages. Refer to flow-ux for the recovery path from these states.)

### Navigation Output Format

```
NAVIGATION AUDIT
LEVEL: [🟢 / 🟡 / 🔵]

PAGE TITLES:
  Unique per route: [yes / no]
  Updated on route change (SPA): [yes / no]
  Format: [page name — app name]

BREADCRUMBS:
  Present where needed: [yes / no / not applicable]
  Use <nav aria-label="Breadcrumb">: [yes / no]
  aria-current on current item: [yes / no]

PRIMARY NAVIGATION:
  Consistent across pages: [yes / no]
  Current page indicated: [yes / no — both visually and programmatically]
  Skip link present: [yes / no]

BACK BUTTON:
  Works on every route: [yes / no]
  Modals push history (if expected): [yes / no]

ERROR PAGES:
  404 accessible: [yes / no]
  500 accessible: [yes / no]
  Navigation present on error pages: [yes / no]
```

---

## Page-Aware Mode for Accessibility

**When working inside a codebase, detect the page type and apply the right accessibility rules.** Don't wait to be told — read the file, recognise the page, switch chapters.

### How to detect the page type

Read the file being worked on. Look at:

- Route or URL path (`/settings`, `/dashboard`, `/login`, `/error`)
- Component name (`SignUpForm`, `Dashboard`, `DataTable`, `OnboardingStep`)
- Content patterns — forms with inputs = forms accessibility, charts = data viz accessibility, "no access" = error page accessibility

### Page-type to chapter mapping

| Detected page type | Apply chapters |
|--------------------|----------------|
| Forms (signup, settings, checkout) | Chapter 6 (Forms) + Chapter 4 (Screen Reader) + Chapter 5 (Plain Language) |
| Dashboards, data tables, charts | Chapter 2 (Visual — colour-blind safe) + Chapter 4 (Tables) + Chapter 1 (Cognitive Load) |
| Onboarding flows | Chapter 1 (Cognitive Load) + Chapter 5 (Plain Language) + Chapter 6 (Forms) |
| Modals and dialogs | Chapter 3 (Keyboard — focus trap, Escape) + Chapter 4 (Screen Reader — role="dialog") |
| Marketing / landing pages | Chapter 2 (Visual) + Chapter 5 (Plain Language) + Chapter 4 (Semantic HTML) |
| Navigation, headers, footers | Chapter 7 (Navigation) + Chapter 3 (Keyboard) + Chapter 4 (Landmarks) |
| Error pages, empty states | Chapter 7 (Error Pages) — also coordinate with flow-ux for recovery |
| Media-heavy pages (video, image-first) | Chapter 4 (Alt text) + Chapter 2 (Motion preferences) |

Apply the relevant chapters automatically. For specific wording on each screen, defer to messaging-ux. For the structure and order of screens, defer to flow-ux.

---

## Accessibility Audit Mode

**When asked to audit a codebase or product for accessibility, produce an Accessibility Audit Report.**

The audit identifies three severity levels of issues, in priority order. The severity isn't about how hard to fix — it's about how badly it blocks real people.

### Critical: Blocks Usage Entirely

Issues that lock people out. Fix first, regardless of effort.

- Missing form labels (screen reader users can't tell what to type)
- Interactive elements not reachable by keyboard (motor disability users can't activate)
- Zero or near-zero colour contrast (low vision users can't read)
- Missing alt text on functional images (screen reader users miss the button)
- Keyboard traps (focus stuck inside a component with no escape)
- Modals without focus management (screen reader users can't reach the dialog)
- Forms that fail validation silently for screen readers
- Missing language declaration on `<html>` (`<html lang="en">`)

### Serious: Degrades Experience Significantly

Issues that make the product painful but technically usable.

- Touch targets below 44px on mobile
- Missing or broken heading hierarchy
- Missing alt text on informational images
- Focus indicators not visible enough or inconsistent
- Errors not attached to the field that broke
- No skip-navigation link
- Time limits without warning or extension
- Auto-playing media with motion (no reduced-motion fallback)
- Inconsistent navigation between pages
- Colour used as the only signal for status

### Minor: Polish and Refinement

Issues that don't block but reduce inclusivity.

- Inconsistent focus styles between components
- Decorative icons not hidden from screen readers (`aria-hidden`)
- Missing `autocomplete` attributes on form fields
- Page titles not updated on SPA route change
- Tables without captions
- Slightly low contrast on non-critical elements (passes AA but fails AAA)
- Long line lengths in body text
- Missing language attribute on text in another language

### Audit Output Format

```
ACCESSIBILITY AUDIT REPORT
App: [Detected app name]
Level applied: [🟢 / 🟡 / 🔵]
Tech stack: [HTML / React / Vue / etc.]
Component library: [shadcn / Radix / Material / custom / etc.]
Scanned: [Routes, components, or directories]

═══════════════════════════════════════════
CRITICAL — [N found]
═══════════════════════════════════════════

1. [Issue]
   WHERE: [File and line, or component name]
   WHO IT BLOCKS: [Which users — screen reader / keyboard / motor / etc.]
   FIX: [Specific code change]
   EXAMPLE:
   [Before / after snippet in the project's actual stack]

═══════════════════════════════════════════
SERIOUS — [N found]
═══════════════════════════════════════════

1. [Issue] — [file location]
   PROBLEM: [What's broken]
   IMPACT: [What the user experiences]
   FIX: [Specific code change with example]

═══════════════════════════════════════════
MINOR — [N found]
═══════════════════════════════════════════

1. [Issue] — [file location]
   FIX: [Quick fix]

═══════════════════════════════════════════
PRIORITISED RECOMMENDATIONS
═══════════════════════════════════════════

Fix first (Critical — under 1 day each):
  1. [Item]
  2. [Item]

Fix next (Serious — 1–3 days each):
  1. [Item]

Polish (Minor — when convenient):
  1. [Item]

═══════════════════════════════════════════
WHAT'S ALREADY GOOD
═══════════════════════════════════════════

  - [Existing accessibility wins worth keeping]
  - [Patterns the team is using correctly]
```

Always provide concrete fixes in the project's actual stack — never just flag the problem. For copy changes inside accessibility fixes (error messages, aria-labels), defer to messaging-ux and note: *"See messaging-ux for the exact wording."* For flow restructures (e.g. an error page needs a recovery path), defer to flow-ux and note: *"See flow-ux for the recovery flow."*

Always include a "What's already good" section. Most products do *some* accessibility right — calling that out helps teams build the muscle, not just fix what's broken.

---

## How accessibility-ux, flow-ux, and messaging-ux Work Together

The three skills are designed to be used together. They never overlap — each handles a different layer of the same product.

| Question | Skill to use |
|----------|--------------|
| Can a screen reader user complete this form? | accessibility-ux |
| What should the error message say? | messaging-ux |
| Should this error have a retry button? | flow-ux |
| Is this button reachable by keyboard? | accessibility-ux |
| What does the button say? | messaging-ux |
| Where does the button live in the flow? | flow-ux |
| Is the colour contrast enough? | accessibility-ux |
| Should the dashboard show this metric at all? | flow-ux (and the data label is messaging-ux) |
| Does the dashboard work with screen readers? | accessibility-ux |
| Is the onboarding too long? | flow-ux |
| Are the onboarding steps labelled accessibly? | accessibility-ux |
| What does each onboarding step say? | messaging-ux |
| Is the cancel button findable? | flow-ux |
| Is the cancel button keyboard-accessible? | accessibility-ux |
| What does the cancel confirmation say? | messaging-ux |

When designing a new product, the natural order of work is:

1. **flow-ux** maps the screens, the order, the logic
2. **accessibility-ux** ensures every screen can be used by everyone
3. **messaging-ux** fills in the words on each screen
4. All three reference the same product profile in `profiles/`

When auditing an existing product:

1. **flow-ux** finds missing flows, dead ends, anxiety moments
2. **accessibility-ux** finds who's locked out — critical, serious, minor
3. **messaging-ux** finds unclear labels, missing help text, error wording
4. Combined report shows all three layers, prioritised together — usually accessibility Critical issues sit at the top because they block people entirely

---

## Quick Reminders

- Accessibility is not a checklist. It's a commitment to including everyone.
- If you can't reach it with a keyboard, half your users can't reach it.
- Semantic HTML before ARIA. Native elements work by default.
- Colour is never the only signal. Every red error has an icon and a word.
- Focus must be visible. Removing the focus ring is a critical bug.
- Test it the way users use it: Tab through, screen reader on, zoom to 200%.
- The best accessibility work is invisible. Users shouldn't notice — they should just get through.
