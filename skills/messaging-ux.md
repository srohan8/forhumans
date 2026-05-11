---
name: messaging-ux
description: >
  Writes, rewrites, and reviews all in-product text through a human-centric lens.
  Covers: UI copy, button labels, error messages, empty states, success messages,
  loading states, onboarding flows, tooltips, help text, form hints, placeholders,
  confirmation dialogs, destructive actions, notifications, emails, pricing copy,
  trust moments, accessibility language, and feature descriptions. Use this skill
  whenever the user asks to write or improve any text that appears inside a product
  — especially when simplifying jargon for non-technical users. Trigger on: "make
  this simpler", "write copy for", "what should this say", "how do I word this",
  "add a tooltip", "add help text", "this sounds too technical", "audit my copy",
  "review my UI", or any pasted UI text asking for feedback or improvement. Also
  trigger when given access to a codebase and asked to improve messaging, UX, or
  user communication. Always use this skill when messaging, copy, or UX writing
  is the subject — even for quick rewrites.
---

# Messaging UX Skill

## Core Philosophy: Human-Centric, Not Tech-Centric

**Every word in a product exists for the human using it — not the system behind it.**

Tech-centric writing describes what the system does.
Human-centric writing describes what the human gets.

| Tech-centric | Human-centric |
|--------------|---------------|
| Describes mechanics | Describes outcomes |
| Uses the builder's vocabulary | Uses the user's vocabulary |
| Assumes context | Provides context |
| Labels features | Explains value |
| Silent where "obvious" | Explains even the obvious |

This is the lens for every rewrite, every help text, every tooltip, every error message.
If a piece of copy makes more sense to the developer who built it than the person using it — rewrite it.

---

## Step 1: Detect Context — Don't Ask What You Can Infer

**If running inside a project or codebase**, read the code first and infer:

- **App name** — from package.json, README, or folder name
- **Product profile** — check `profiles/` for a matching `.md` file and load it
- **Audience** — infer from README, landing page copy, onboarding flows, or existing UI text
- **Domain** — infer from the app's purpose
- **Vibe** — infer from existing copy tone or marketing text

**Only ask if you genuinely can't infer.** Ask only what's missing — never all 3 if 2 are clear.

### If no project context (standalone conversation)

Ask all 3 together, once:

> **1. Who are your users?**
> - 🟢 Non-technical — solo founders, small business owners, general public
> - 🟡 Intermediate — ops teams, marketers, startup teams with some SaaS experience
> - 🔵 Technical — developers, engineers, data teams

> **2. What kind of app is it?**
> - ⚙️ Tech / productivity — automation, dev tools, APIs, SaaS workflows
> - 💼 Business / professional — invoicing, CRM, legal, finance, HR
> - 🌱 Daily life / consumer — health, habits, personal finance, home
> - 🎨 Lifestyle / creative — fitness, food, travel, design, social

> **3. What's the vibe?**
> - Friendly & warm
> - Clear & neutral
> - Direct & minimal

> **4. How much personality / fun is allowed?**
> - 🎭 **Go for it** — wit, humor, playful loading messages, cheeky empty states are welcome
> - 😊 **Warm but professional** — friendly and human, but not trying to be funny
> - 🧱 **Straight-faced** — plain and clear, no jokes, no personality — users trust serious tone here (e.g. finance, legal, medical)
>
> Examples so you can calibrate:
>
> | Moment | 🎭 Go for it | 😊 Warm but professional | 🧱 Straight-faced |
> |--------|-------------|--------------------------|-------------------|
> | Loading | "Asking the AIs nicely..." | "Checking your results..." | "Loading results" |
> | Empty state | "Crickets. Let's fix that." | "Nothing here yet — let's get started." | "No data available." |
> | Success | "Nailed it. 🎉" | "You're all set!" | "Saved successfully." |
> | Error | "Oops, that didn't work." | "Something went wrong — try again." | "An error occurred. Please retry." |
> | Destructive confirm | "Wait — you sure? This is permanent." | "This can't be undone." | "This action is irreversible." |

Never ask the same question twice in a session.

### Product Profiles

If a `profiles/` folder exists next to this SKILL.md, check for a file matching
the current app name (e.g. `profiles/myapp.md`). If found, load it — it contains
the audience, domain, vibe, jargon swaps, and example rewrites for that product.

If no profile exists yet, infer what you can, ask only what's missing, then offer:
*"Want me to save this as a profile so you don't have to answer these again?"*
and create `profiles/[appname].md`.

A profile contains: audience + domain + vibe settings, product-specific jargon swaps,
approved example rewrites, and emotional tone per moment.

Profiles are per-project and never bundled into the shared skill file.

---

## Audience & Domain Calibration

| Audience | Language rules |
|----------|---------------|
| 🟢 Non-technical | No jargon. No acronyms. Outcome-focused. Short sentences. Explain consequences, not mechanics. |
| 🟡 Intermediate | Light SaaS vocabulary OK. Still plain sentences. Avoid deep technical terms. |
| 🔵 Technical | Technical terms fine. Precision over simplicity. Minimal hand-holding. |

**When unsure, default to 🟢 non-technical.**

| Domain | What to adjust |
|--------|----------------|
| ⚙️ Tech / productivity | Avoid dev jargon but tech metaphors (sync, connect, automate) are fine |
| 💼 Business / professional | Precise over casual. Users care about accuracy and money. Don't be breezy. |
| 🌱 Daily life / consumer | Warm, simple, human. Avoid anything corporate or clinical. |
| 🎨 Lifestyle / creative | Expressive and punchy. Short copy. Emotion is welcome. |

---

## The Golden Rules

1. **Lead with the outcome, not the action.**
   - ❌ "Authenticate via OAuth"
   - ✅ "Sign in with Google"

2. **One idea per sentence.** If you need a comma, consider splitting.

3. **No passive voice.** Active verbs only.
   - ❌ "Your data is being synced"
   - ✅ "We're syncing your data"

4. **Name the thing the user cares about, not the system thing.**
   - ❌ "Webhook endpoint registered"
   - ✅ "Your app will now get notified automatically"

5. **Errors must say what to do next — not just what went wrong.**
   - ❌ "Invalid API key"
   - ✅ "That key didn't work. Check it in Settings → Integrations."

6. **Match the emotional moment.**
   Success = warm. Error = calm + helpful. Empty state = encouraging. Destruction = serious.

7. **If it sounds weird read aloud — rewrite it.**

---

## Component Playbook

### Button Labels
- Use verb + noun: "Save changes", "Connect Stripe", "Send invoice"
- Never: "Submit", "OK", "Confirm" — too vague
- Destructive actions: name the consequence specifically ("Delete account" not "Remove")
- Disabled buttons: explain why, don't just grey them out. Add tooltip: "Fill in your company name first"

### Tooltips
- One sentence max. Answer: *"What does this do / why does it matter?"*
- Don't repeat the label. Add context the label can't give.
- No period needed for short fragments.
- Example → Label: `Retry limit` / Tooltip: `How many times we'll try before marking it failed`

### Help Text (below a field)
- Answers: *"What should I put here, and in what format?"*
- Keep under 12 words ideally. Examples beat explanations: `e.g. hello@yourcompany.com`
- Show it always — don't hide behind hover for important fields
- Example → `Your business name as it appears on invoices`

### Placeholders (inside a field)
- Hint, don't instruct — they disappear when typing starts
- Use realistic-looking examples: `e.g. Acme Corp` not `Enter company name`
- Never use a placeholder as the only label — always pair with a visible label

### Error Messages
Structure: **What happened → Why (brief) → What to do**
- ❌ "Error 422: Unprocessable entity"
- ✅ "We couldn't save this. The email looks incomplete — check for a missing @."
- Stay calm. Blame the situation, not the user. Never say "invalid" without explaining why.

### Empty States

Three parts: what's missing → why it matters → one clear CTA. Then apply the fun level:

| Fun level | Example |
|-----------|---------|
| 🎭 Go for it | "Crickets in here. Send your first invoice and break the silence. → Create invoice" |
| 😊 Warm | "No invoices yet. Send your first one and get paid faster. → Create invoice" |
| 🧱 Straight | "No invoices. Create your first invoice to get started. → Create invoice" |

- Make it encouraging — this is often the first thing a new user sees
- The CTA should feel like the obvious next step, not a last resort
- Never make the user feel like they broke something by landing here

### Success / Confirmation Messages

Confirm the outcome, not just the action. Apply the fun level:

| Fun level | Example |
|-----------|---------|
| 🎭 Go for it | "Nailed it. Your changes are live. 🎉" |
| 😊 Warm | "You're all set — your changes are live." |
| 🧱 Straight | "Changes saved successfully." |

- Add a useful next step when relevant: "Invoice sent. We'll let you know when they open it."
- 🎭 Fun celebrations work best for milestone moments (first invoice, first integration, hitting a goal) — not every save button click

### Loading & Skeleton States

Never just "Loading..." — always say what's happening. Then apply the fun level:

| Fun level | Short wait | Long wait | Background task |
|-----------|-----------|-----------|-----------------|
| 🎭 Go for it | "Asking the AIs nicely..." | "Good things take time. This is one of them." | "Working on it in the background — go grab a coffee." |
| 😊 Warm | "Checking your results..." | "This usually takes 20–30 seconds — hang tight." | "We're on it — you can keep using the app." |
| 🧱 Straight | "Loading results" | "Processing. This may take up to 30 seconds." | "Running in background." |

- For long waits: always set time expectations ("This usually takes 20–30 seconds")
- For background tasks: explicitly say they can keep using the app
- Skeleton screens: match the shape of real content so users know what's coming
- Rotate fun messages if the wait is long — one loading joke lands; the same one three times doesn't

### Onboarding / First-Run Experience
- Frame every step around the user's goal, not your system's needs
- Replace "We need your X" → "Add your X so you can Y"
- Progress framing: "Almost there" not "Step 3 of 5"
- First empty state a user sees should feel like an invitation, not a void
- Celebrate first actions: "You just sent your first invoice. That's money incoming."

### Confirmation Dialogs (Destructive Actions)
High-anxiety moments. Copy must acknowledge the weight of the decision.
- Title: state what's about to happen, not a question ("Delete this project")
- Body: one sentence on what they'll lose, specifically ("Your 3 posts and all settings will be removed permanently.")
- CTA: repeat the action word, never just "Yes" ("Delete project" + "Keep it")
- Never make the destructive action the primary/default button
- ❌ Title: "Are you sure?" Body: "This cannot be undone." CTA: "OK / Cancel"
- ✅ Title: "Delete project?" Body: "Your 3 posts and settings will be permanently removed." CTA: "Delete project" / "Keep it"

### Modal / Dialog Copy
- Title = what's happening or being decided (noun phrase or direct question)
- Body = just enough context to make the decision, nothing more
- CTA = specific verb ("Delete project", "Keep my data") — never just "Yes / No"

### Notifications & System Emails
- Subject lines: outcome first, not feature name
  - ❌ "Invoice #1042 status update"  ✅ "Your invoice was opened — follow up now?"
- Push notifications: one line, one action. If there's no action, don't send it.
- Alert banners: say what the user should do, not just what happened
  - ❌ "Your trial ends in 3 days."  ✅ "3 days left — add a card to keep everything running."
- Transactional emails: plain language, no marketing fluff. One purpose per email.

### Pricing & Upgrade Prompts
- Never: "Upgrade to Pro" with no context
- Always tie the upgrade to what the user is trying to do right now
  - ❌ "This is a Pro feature. Upgrade to access."
  - ✅ "Unlimited exports are on the Pro plan. You've used 3 of your 5 this month. → See what's included"
- Free trial end: don't threaten — remind them what they'd lose
  - ❌ "Your trial expires tomorrow."
  - ✅ "Tomorrow your reports, integrations, and history go on pause. Keep them? → Add a card"
- Pricing page copy: name the outcome of each tier, not just the feature list

### Trust Moments (Password, Payment, Permissions)
These are where users hesitate most. Every word counts.
- Password fields: tell them your rules upfront, not after they fail
  - ✅ Help text: "At least 8 characters. We'll never ask for this over email."
- Payment forms: acknowledge the anxiety
  - ✅ "Your card details are encrypted and never stored on our servers."
- Permission requests (camera, location, notifications): explain the benefit before asking
  - ❌ "[Allow notifications]"
  - ✅ "Get notified when someone opens your proposal — so you can follow up at the right moment. → Turn on notifications"
- Any form collecting sensitive data: one line of reassurance near the submit button

### Accessibility & Inclusive Language
- Never rely on direction alone: "click the button on the left" → "click Save changes"
- Icon-only buttons must have aria-labels that describe the action, not the icon
  - ❌ aria-label="pencil icon"  ✅ aria-label="Edit project name"
- Avoid: "simply", "just", "obviously", "easy" — condescending to users who are struggling
- Avoid: "guys", "blacklist/whitelist" — use "everyone", "blocklist/allowlist"
- Color alone should never convey meaning — always pair with text or icon
- Error messages must be readable without seeing the red color

---

## Enforcement Rule: Audit for Doubt, Not for Coverage

**The goal is not to add help text everywhere. The goal is zero hesitation.**

A well-named label that creates no doubt in the user's mind needs nothing else.
Help text exists to resolve confusion — not to prove the product is documented.

> If the label alone creates zero doubt — no help text needed.
> If there's any chance of hesitation or misunderstanding — add it.

### The doubt test

For every title, label, or section — ask:
*"Could a user in this audience pause and wonder what this means or does?"*

- **No doubt** → leave it alone. Don't add help text for the sake of it.
- **Any doubt** → add help text. One sentence. What it is + why it matters.

### When help text is unavoidable

Some products genuinely need more explanation — and that's fine:
- **Genuinely new concepts** — things that didn't exist a year ago (AI visibility, generative search, etc.)
- **Serious consequences** — finance, legal, medical settings where a wrong input causes real harm
- **Non-obvious inputs** — API keys, webhook URLs, regex patterns, cron expressions
- **Non-technical users doing technical tasks** — the gap between what the label says and what they need to do is too wide to bridge with a label alone

In these cases, help text isn't a crutch — it's the right design decision.

### When self-explanatory is achievable

- The action is familiar: send, save, delete, connect, export
- The label already tells the full story: "Send invoice to client"
- The context makes it obvious: a "Due date" field inside an invoice form needs no explanation
- The user has seen this pattern in every other app they use

### How to audit a codebase

For each hardcoded UI string, apply the doubt test against the target audience.
Non-technical audience = lower threshold for adding help text.
Technical audience = higher threshold, more can be left self-explanatory.

Produce a **Copy Audit Report** with two sections:

```
NEEDS HELP TEXT: [N items]

1. "[Title]" — [location in code]
   WHY: [one sentence on what's ambiguous]
   SUGGESTED: [one-sentence help text]


SELF-EXPLANATORY — NO ACTION NEEDED: [N items]

1. "[Title]" — clear because [reason]
2. "[Title]" — familiar pattern, no doubt created
```

Always write the suggested copy immediately — don't just flag the gap.
Always explain why something is self-explanatory too — so the team builds the instinct.

---

## Jargon Swap Reference

For non-technical audiences, swap these automatically:

| Avoid | Use instead |
|-------|-------------|
| Authenticate | Sign in / Verify it's you |
| API key | Your secret access code |
| Webhook | Automatic notification |
| Sync / syncing | Updating / keeping up to date |
| Deploy | Publish / go live |
| Environment | Version (test version, live version) |
| Endpoint | Connection point |
| Token | Temporary access code |
| Cache | Saved version |
| Payload | The data being sent |
| Rate limit | Speed limit on requests |
| Deprecate | No longer supported |
| Repository | Project folder |
| OAuth | Sign in with Google / etc. |
| SSO | One password for everything |
| Cron job | Scheduled task |
| Parse | Read and process |
| Boolean | On/off setting |
| Null / undefined | Empty / not set yet |
| Regex | Search pattern |
| Scope | What it has access to |
| Permissions | What you're allowed to do |
| Instance | Your version / your copy |
| Sandbox | Test mode |
| Production | Live / real |
| Latency | Delay / loading time |
| Timeout | Took too long and stopped |
| Abort | Cancel / stop |
| Deprecated | No longer supported — switch to X |

---

## Output Format

**Rewriting existing copy:**
```
ORIGINAL:  [their text]
REWRITTEN: [your version]
WHY:       [one sentence on the key change]
```

**Writing from scratch** (tooltip, help text, notification, etc.):
Return the copy directly with a brief note on format choices if non-obvious.

**Reviewing a full screen or flow:**
Organize by component type — titles → help text → buttons → errors → empty states.

**Auditing a codebase:**
Lead with the Missing Help Text Report, then full rewrites grouped by file or screen.

---

## Quick Reminders

- Read it aloud. If it sounds weird — rewrite it.
- Cut 30% and re-read. Almost always better.
- When the right call is subjective, offer 2 options.
- Never use "simply", "just", "easy" — they make struggling users feel worse.
- The best UX copy is invisible. Users shouldn't notice it — they should just know what to do.
