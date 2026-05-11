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
- Examples beat explanations: `e.g. hello@yourcompany.com`
- Show it always — don't hide behind hover for important fields
- Example → `Your business name as it appears on invoices`

### Help Text Length Rules

**Inline help text: 60 characters max. Always visible. No exceptions.**

Anything that needs more explanation must have a "read more" path — one interaction
away. The UI pattern (expandable, drawer, modal) is the developer's call. The rule
is: short inline, full explanation accessible.

**Short and long versions are written separately — never truncate.**

By default, only write the short version (≤60 chars). Write the long version too when:
- The user asks for "read more" text or full explanations
- The product profile specifies it
- The concept is genuinely complex and 60 chars can't cover it safely (e.g. a setting with serious consequences)

The short version is not the first sentence of the long version chopped off.
Each is written specifically for its format.

Example — metric: Conversion rate
```
SHORT (inline, ≤60 chars):
How many visitors actually took action

LONG (read more):
Out of everyone who visited your page, this is the percentage
who did the thing you wanted — signed up, purchased, clicked.
A typical rate is 2–5%. Yours is calculated over the last 30 days.
```

Example — setting: Retry limit
```
SHORT (inline, ≤60 chars):
How many times we'll try before giving up

LONG (read more):
When a request fails, we'll automatically retry it this many
times before marking it as failed. Higher numbers mean more
chances to succeed, but longer wait times. The default (3) works
for most cases.
```

When writing both versions:
- Short: one plain sentence, outcome-focused, no jargon
- Long: 2–4 sentences, adds the why, the context, and a benchmark or default if relevant
- Long version should sound natural read aloud — no abbreviations, no parenthetical asides, spell out numbers

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

## Page-Aware Mode

**When working inside a codebase, detect what page or screen the user is working on
and apply the right patterns automatically.** Don't wait to be told — read the file,
recognise the page type, and switch to the relevant rules.

### How to detect the page type

Read the file being worked on. Look at:
- Route name or URL path (`/settings`, `/dashboard`, `/search`, `/onboarding`)
- Component name (`SettingsPage`, `SearchResults`, `EmptyDashboard`, `PermissionDenied`)
- Content patterns — forms with toggles = settings, charts = dashboard, "no results" = search

### Page-specific rules

Once you know the page type, apply these rules **on top of** the general Component Playbook:

#### Settings & Configuration Pages
The graveyard of jargon. Every toggle, dropdown, and input here was named by a developer.
- Every setting needs a label + one-sentence explanation of what it actually changes
- Group settings by what the user is trying to do, not by system category
  - ❌ "API Settings", "Notification Settings", "Account Settings"
  - ✅ "Connections", "What you get notified about", "Your account"
- Toggles need to say what happens when ON, not just what the thing is
  - ❌ "Email notifications" [toggle]
  - ✅ "Email notifications" [toggle] — "Get an email when someone views your proposal"
- Dangerous settings (delete account, revoke access) should be visually separated and have confirmation dialogs
- If a setting has no effect until the user does something else, say so: "Takes effect next time you publish"

#### Search & Zero-Result States
"No results found" is the laziest message in software. Users feel stuck.
- Always suggest what to do next — broaden search, check spelling, try different terms
- If possible, show related or popular items instead of emptiness
- Preserve the search query in the UI so they can edit, not retype
- Different zero-result messages for different causes:
  - Nothing matches: "No matches for '[query]'. Try fewer or different words."
  - Filters too narrow: "No results with these filters. Remove some to see more."
  - Empty category: "Nothing here yet. [CTA to add something]"
- Search placeholder should hint at what's searchable: `Search invoices, clients, or amounts...`

#### Permission & Access Denied Screens
"You don't have access" tells the user nothing. These moments feel like a slammed door.
- Always explain WHY they don't have access in plain language
- Always tell them HOW to get access — who to ask, what to do
- Never just show a lock icon with no words
- Match the tone to the situation:
  - Wrong plan: "This is available on the Pro plan. You're on Free. → See what Pro includes"
  - Wrong role: "Only admins can change this. Ask [admin name] to update it, or request admin access."
  - Expired: "Your access expired on [date]. Renew to pick up where you left off."
  - Not logged in: "Sign in to see this page."
- Never make the user feel like they did something wrong — they just arrived at the wrong door

#### Dashboard, Analytics & Data Pages
Numbers without context are meaningless. Most dashboards are built for the person
who wrote the query, not the person reading the result.

**The core rule: every number needs a sentence that tells the user what it means for them.**

Metric labels:
- Name the outcome, not the metric: "How many people visited" not "Sessions"
- ❌ "MRR" ✅ "Monthly revenue" ✅ "What you earned this month"
- ❌ "DAU/MAU" ✅ "How often people come back"
- ❌ "Churn rate" ✅ "How many customers you lost"
- ❌ "Bounce rate" ✅ "People who left without doing anything"
- ❌ "LTV" ✅ "What a customer is worth over time"
- ❌ "P95 latency" ✅ "Slowest load time (for 95% of users)"

Context over absolutes:
- Always show relative context: "Up 23% from last week" > just "1,234"
- Comparisons make numbers meaningful: "You're ahead of last month's pace"
- If a number is good or bad, say so — don't make the user guess: "⬆ 12% — that's your best week yet"
- Timeframes should be visible and plain: "Last 30 days" not "30d" or "T-30"

Zero-state metrics:
- Don't just show 0 or a dash — explain what will appear here
- ❌ "Revenue: $0.00" ✅ "No revenue yet. This updates when you get your first payment."
- ❌ "—" ✅ "Not enough data yet — check back after your first week"

Charts and graphs:
- Title = what the chart answers: "How your traffic changed this month" not "Traffic — 30d"
- Y-axis labels in human units: "visits" not "sessions", "dollars" not "USD (cents)"
- Highlight the insight, not just the data: annotate spikes, dips, milestones
- If a chart is empty, don't show an empty chart — show an encouraging empty state with the CTA that will generate data

Tables:
- Column headers should be plain words: "Customer" not "account_id", "Signed up" not "created_at"
- Format numbers for readability: "1,234" not "1234", "$12.50" not "12.5"
- Dates in human format: "May 11, 2026" or "3 days ago" — never "2026-05-11T00:00:00Z"
- Empty table: same rule as empty states — explain what will appear and how to get started

Tooltips on metrics:
- Every metric card or number that isn't immediately obvious needs a tooltip
- Format: what it measures + why it matters
- ✅ "Views — How many people looked at your page. Higher = more interest."
- ✅ "Conversion rate — Out of everyone who visited, how many took action. Industry average is around 2–3%."

Summary / insight lines:
- If the dashboard can surface one takeaway, do it in plain language at the top
- ✅ "Your best day this week was Tuesday. Most visitors came from LinkedIn."
- ✅ "Revenue is flat — you haven't sent any invoices this week."
- This is the most human-centric thing a dashboard can do: tell me what I should know without making me read every chart

#### Forms & Multi-Step Flows
- Show total steps only if it's 3+ steps. For 2 steps, just show "Next" and "Done"
- Each step title should name the goal, not the system's need: "Tell us about your business" not "Company Information"
- Save progress automatically — and tell the user you did: "Draft saved"
- Required fields: mark the optional ones, not the required ones (most fields are required — flagging the few that aren't is cleaner)
- At the end of a form, confirm what will happen: "We'll send an invoice to jane@acme.com for $1,200"

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
