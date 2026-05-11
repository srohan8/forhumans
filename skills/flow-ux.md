---
name: flow-ux
description: Designs, reviews, and audits user flows through a human-centric lens. Covers: onboarding flows, error recovery paths, progressive disclosure, feature reveal timing, offboarding and cancellation flows, exit surveys, save offers, data export, win-back patterns, multi-step journeys, and the order/logic/structure of screens. Use this skill whenever the user asks to design or improve a flow — the journey, not just the words on one screen. Trigger on: "design the onboarding", "what screens do I need", "what order should this go in", "audit my onboarding", "users are dropping off at", "design the cancellation flow", "what happens when X fails", "should I ask for this now or later", "review my signup flow", "map the journey", or any request about screen sequences, decision logic, or user paths. Also trigger when given access to a codebase and asked to improve onboarding, error handling, or cancellation. Pairs with messaging-ux: flow-ux decides what screens and in what order; messaging-ux decides what each screen says. Always use this skill when flow design, journey logic, or screen sequencing is the subject.
---

# Flow UX Skill

## Core Philosophy: Human-Centric, Not System-Centric

**Every screen in a flow exists for the human moving through it — not the system processing them.**

A flow isn't a sequence of forms a developer needs to collect data through. It's a journey a human is taking to reach a goal. Tech-centric flows ask everything the database needs. Human-centric flows ask only what's required to get the user one step closer to their goal — and explain why each step exists.

| Tech-centric flow | Human-centric flow |
|--------------------|---------------------|
| Optimised for data collection | Optimised for user progress |
| Linear because the database is linear | Branches based on what the user needs |
| Every required field upfront | Only what's needed right now |
| Errors are dead ends | Errors are detours back to success |
| Cancellation is a wall | Cancellation is a doorway, kept open |
| Reveals all features on day one | Reveals features when the user is ready |
| Measures completion | Measures confidence at each step |

This is the lens for every flow designed, every audit performed, every onboarding rewritten.
If a flow makes more sense to the team that built it than the person walking through it — redesign it.

**flow-ux and messaging-ux work together.**
- **flow-ux** decides *what screens exist, in what order, with what logic.*
- **messaging-ux** decides *what each screen says.*

When designing a flow, reference messaging-ux for the actual copy on each screen. When writing copy, reference flow-ux for whether the screen should even exist at that point.

---

## Step 1: Detect Context — Don't Ask What You Can Infer

**If running inside a project or codebase**, read the code first and infer:

- **App name** — from package.json, README, or folder name
- **Product profile** — check `profiles/` for a matching `.md` file and load it (shared with messaging-ux)
- **Audience** — infer from README, landing page, existing onboarding, or UI text
- **App type** — infer from routes, components, and product purpose
- **Existing flows** — scan for routes like `/onboarding`, `/signup`, `/welcome`, `/cancel`, `/error` — map what's already there
- **Vibe and fun level** — infer from existing copy or marketing tone

**Only ask if you genuinely can't infer.** Ask only what's missing — never all 4 if 3 are clear.

### If no project context (standalone conversation)

Ask all 4 together, once:

> **1. Who are your users?**
>
> - 🟢 Non-technical — solo founders, small business owners, general public
> - 🟡 Intermediate — ops teams, marketers, startup teams with some SaaS experience
> - 🔵 Technical — developers, engineers, data teams
>
> **2. What kind of app is it?**
>
> - ⚙️ Tech / productivity — automation, dev tools, APIs, SaaS workflows
> - 💼 Business / professional — invoicing, CRM, legal, finance, HR
> - 🌱 Daily life / consumer — health, habits, personal finance, home
> - 🎨 Lifestyle / creative — fitness, food, travel, design, social
>
> **3. What's the vibe?**
>
> - Friendly & warm
> - Clear & neutral
> - Direct & minimal
>
> **4. How much personality / fun is allowed?**
>
> - 🎭 **Go for it** — playful celebrations, cheeky empty states, humour welcome
> - 😊 **Warm but professional** — friendly and human, but not trying to be funny
> - 🧱 **Straight-faced** — plain and clear, no jokes, no personality — users trust serious tone here (e.g. finance, legal, medical)

Never ask the same question twice in a session.

### Product Profiles

Profiles are shared with messaging-ux. If a `profiles/` folder exists next to this SKILL.md, check for a file matching the current app name (e.g. `profiles/myapp.md`). If found, load it — it contains audience, app type, vibe, jargon swaps, approved example rewrites, and any flow notes already captured.

If no profile exists, infer what you can, ask only what's missing, and offer: *"Want me to save this as a profile so you don't have to answer these again?"* and create `profiles/[appname].md`.

When flow-ux adds to a profile, it adds: existing flow map, drop-off risks identified, and emotional state notes per flow.

Profiles are per-project and never bundled into the shared skill file.

---

## The Golden Rules of Flows

1. **A flow is a journey, not a form.** The user is going somewhere. Every step either moves them closer or it shouldn't exist.

2. **Defer everything that can be deferred.** If you don't need it to deliver value right now, ask later. Progressive profiling beats upfront interrogation.

3. **Every step needs a reason the user can feel.** Not "we need this to set up your account." Use "so we can show you the right templates" instead.

4. **An error is a detour, not a wall.** Every failure state must have a path back to success.

5. **Match the screen to the emotional state.** Excited new user ≠ frustrated user hitting an error ≠ user trying to cancel. Different emotional weight, different design.

6. **Show progress in user terms, not step counts.** "Almost there" beats "Step 4 of 7."

7. **The aha moment comes first. The polish comes later.** Get the user to value before you ask them to customise their avatar.

8. **Leaving should be as easy as joining.** Trust is built at the exit, not the entrance.

---

## Chapter 1: Onboarding Flow Design

**The first 5 minutes decide whether a user stays.** Most products fail here not because the product is bad — but because the user never reaches the moment where they understand why the product matters.

### The North Star: Time to First Value

Every onboarding flow has a single job: get the user to their **aha moment** — the moment they personally experience the product's value — as fast as possible.

Everything else (profile setup, preferences, team invites, integrations) is a distraction from that job. If it doesn't directly enable the aha moment, defer it.

**To design onboarding, first answer:**
> *"What's the smallest possible thing the user can do that makes them go 'oh, I get it'?"*

For an invoicing app: sending one invoice. For a habit tracker: marking one habit done. For a CRM: seeing one deal move forward. For a writing tool: producing one piece of writing they'd actually use.

That's the destination. Everything before it should be ruthlessly trimmed.

### The Onboarding Skeleton

Most human-centric onboarding flows follow this shape:

1. **Welcome** — set expectations, not collect data
2. **The minimum context** — ask only what's needed to personalise the next 2 minutes
3. **First win** — get the user to do *one real thing* that produces a result
4. **Celebrate the first win** — make the moment land emotionally
5. **One next step** — show what's possible, but only one option
6. **Defer everything else** — to in-product moments, not a setup wizard

Anything outside this shape needs justification.

### What to Ask Upfront vs Defer

| Ask upfront only if... | Defer to later if... |
|------------------------|----------------------|
| It's required to show the right thing on the next screen | The user can succeed without it |
| Skipping it would cause an error or empty result | It's "nice to have" for the system |
| The user is already thinking about it (e.g. their goal) | It's about the system's needs, not the user's |
| It takes under 5 seconds to answer | It requires the user to find a piece of info |

**Examples of what to defer:**
- Profile photo (defer to first time they need it)
- Team invites (defer to after they see value alone)
- Notification preferences (defer to after the first notification would have fired)
- Integration setup (defer to when they're in the workflow that needs it)
- Billing info on a free trial (defer until the trial is ending — if at all)
- Detailed preferences (defer to settings, surface contextually)

**Examples of what to ask upfront:**
- The user's primary goal (so you can personalise everything)
- Their role or use case (if it changes the product entirely)
- The single piece of info needed to populate their first real screen

### Framing Every Step Around the User's Goal

Every onboarding step has two possible framings — and the human-centric one always wins.

| System framing (avoid) | User framing (use) |
|------------------------|---------------------|
| "We need your company name" | "What should we put on your invoices?" |
| "Choose your plan" | "Let's pick a plan that fits how you'll use this" |
| "Verify your email" | "Confirm your email so we can send you receipts and reminders" |
| "Upload a profile photo" | "Add a photo so your team recognises you in comments" |
| "Set your timezone" | "Set your timezone so reminders land at the right time" |

Every step answers the user's silent question: *"Why are you asking me this?"*

### Progressive Profiling: Ask Over Time, Not All at Once

Don't ask everything in the welcome flow. Ask the right thing at the right moment.

| Moment | What to ask |
|--------|-------------|
| Sign up | Email, password (or SSO). Nothing else. |
| First screen | The minimum to personalise their next view (goal, use case, or one preference) |
| Right before first action | Only what that action requires |
| After first success | "Want to invite a teammate?" — now they have something to share |
| First time a feature is used | The setting that feature needs, contextually |
| Day 3 or week 1 | Optional profile details, preferences |
| When upgrading | Billing info, company details |

The principle: **the right question at the right moment feels helpful. The same question upfront feels like an interview.**

### Celebrating the First Win

When a user completes their first real action, that moment must feel different from every other screen. This is where retention is built.

A first win moment should:
- **Name what they just did** in human terms — "You sent your first invoice"
- **Connect it to outcome** — "That's money on its way"
- **Show what's next** — one clear, optional follow-up
- **Match the fun level** — celebrations should feel right for the product

Apply the fun level:

| Fun level | First win moment |
|-----------|------------------|
| 🎭 Go for it | "🎉 First invoice sent! That's $1,200 of vibes heading your way. Want to schedule a reminder?" |
| 😊 Warm | "Your first invoice is on its way to Acme Corp. We'll let you know when they open it." |
| 🧱 Straight | "Invoice sent to Acme Corp. You'll receive a notification when it's viewed." |

(For the exact wording on each screen, reference messaging-ux.)

### The "Skip" Option

Every non-essential onboarding step needs an obvious way to skip — without guilt.

- ❌ "Are you sure? You'll miss out on important features."
- ✅ "Skip for now — you can always set this up later."

Skip should never be hidden, greyed out, or smaller than the primary button. The user knows what they need; respect that.

### Empty States as Onboarding Continuations

When a user lands on a screen with no data, that empty state *is* part of onboarding. It must:
- Explain what this screen is for in plain terms
- Show the one action that would fill it
- Match the encouragement level of the rest of onboarding

(See messaging-ux for empty state copy patterns.)

### Onboarding Flow Output Format

When designing an onboarding flow, return:

```
FLOW: [Flow name]
AUDIENCE: [Detected audience]
AHA MOMENT: [The single thing this flow exists to deliver]

STEP 1 — [Screen name]
  Purpose: [What this screen does for the user]
  Entry: [How the user arrives here]
  Exit: [How they get to the next step + skip option if any]
  Asks for: [Only what's needed here]
  User feels: [Emotional state — curious / oriented / uncertain / etc.]

STEP 2 — [Screen name]
  ...

[Continue for each step]

DEFERRED TO LATER:
  - [Thing 1] — defer until [moment]
  - [Thing 2] — defer until [moment]

WHY THIS WORKS:
  [One paragraph on what the flow optimises for and what it sacrifices]
```

---

## Chapter 2: Error Recovery

**An error is not a failure state — it's a fork in the road.** The wrong direction leads to abandonment. The right direction leads back to success.

Most products treat errors as endpoints: show the message, log the issue, hope the user retries. Human-centric products treat errors as moments where trust is either built or broken.

### The Full Error Recovery Path

Every error has four parts, and most products only build two of them:

1. **What happened** — the error message itself (handled by messaging-ux)
2. **Why it happened** — brief, in plain language
3. **What to do right now** — a clear, specific next action
4. **What to do if that doesn't work** — the second-level fallback

Stopping at part 2 leaves the user stranded. The flow continues past the error message.

### Retry Logic from the User's Perspective

Most retry logic is built for the system. The user shouldn't have to think about exponential backoff or retry limits — they should know:
- Is the app doing something right now, or do I need to act?
- How long should I wait before assuming it's broken?
- What's the manual fix if the automatic retry doesn't work?

**Retry patterns by error type:**

| Error type | Retry approach |
|------------|----------------|
| Network blip (transient) | Auto-retry silently 1–2 times. Only show a message if it's still failing after that. |
| Server is slow / overloaded | Show a "this is taking longer than usual" message after 5 seconds. Don't kill the request. |
| User input issue | No retry — the user needs to fix something. Highlight the field, explain how. |
| External service down | Don't auto-retry forever. After 2 attempts, show: "Stripe is having issues. We'll keep trying — or you can try again in a minute." |
| Permission / auth issue | Don't retry. Direct the user to fix access. |
| Hard system failure | One retry button. If that fails, escalate: "This isn't working. Contact support and we'll fix it." |

The principle: **automatic retries should be invisible until they need the user's attention. Manual retries should be one click with a clear next-step backup.**

### Partial Failure: Don't Pretend Everything Worked or Everything Broke

The most confusing UX moment is when *some* of what the user did succeeded and some didn't. Most products either:
- Show "Success!" and silently drop the failed parts, or
- Show "Error!" and roll back everything (including the parts that worked)

Both break trust. The human-centric approach:

> **Tell the user exactly what worked and what didn't, and what to do about the broken parts.**

Example — bulk action:
- ❌ "Failed to delete 3 invoices."
- ❌ "Successfully deleted 3 invoices." (when really 2 of 5 deleted)
- ✅ "Deleted 3 of 5 invoices. The other 2 are still locked because they're already paid. → Review them"

Example — multi-integration setup:
- ✅ "Connected to Stripe and Google. Slack didn't connect — your team's admin needs to approve it first. → Send approval request"

Partial states deserve their own UI treatment, not just a coloured banner.

### Preventing the Same Error Twice

If a user hits the same error a second time in a session, your flow has failed them. The recovery path must learn:

- **First time** — show the error message with the fix
- **Second time same error** — show the fix more prominently, plus an escape hatch ("Still stuck? → Contact support")
- **Third time** — assume the user can't fix it alone. Offer human help, alternative path, or admin escalation.

The flow should track and adapt. A user retrying the same broken thing five times is a flow problem, not a user problem.

### Graceful Degradation: What Still Works When Something Breaks

When a part of the product is broken, the rest shouldn't break with it. Design every flow with the question: *"What can the user still do when this service is unavailable?"*

Examples:
- **Payment processor is down** → User can still create the invoice and save it as a draft. The "Send" button shows: "Sending paused — Stripe is having issues. Your draft is saved. → Try again in a few minutes."
- **AI service unavailable** → Manual entry is still possible. "AI suggestions are offline right now — you can still write this yourself."
- **Real-time sync broken** → Work locally. "Working offline — your changes are saved here and will sync when you reconnect."
- **Notification service failed** → The action still completes. The user just doesn't get notified. Don't fail the action because the notification failed.

The principle: **a failure in one system should never block actions that don't actually depend on it.**

### Anxious Moments Need Reassurance

Some errors are scarier than others. Match the reassurance to the anxiety:

| Error type | Reassurance needed |
|------------|---------------------|
| "Your payment couldn't be processed" | High — money is involved. Reassure: "No charge was made. Your card wasn't billed." |
| "Your work couldn't be saved" | High — fear of data loss. Reassure: "Your work is still here — we just couldn't save to our servers. Copy it to be safe." |
| "Sign in failed" | Medium — friction, not loss. Reassure: "Your account is safe — just try again." |
| "Couldn't load this page" | Low — annoyance. Just: "Try refreshing." |

(messaging-ux handles the exact wording. flow-ux ensures the right *type* of reassurance shows up at the right moment.)

### The Recovery Path Must Lead Back

Every error screen must answer: *"How do I get back to what I was trying to do?"*

- "Try again" → returns the user to the action they attempted
- "Go back" → returns to the previous state (with their work preserved)
- "Get help" → opens support without losing context
- Never: a dead-end error screen with no path forward

If the user can't continue without help, the error screen *is* the help screen — don't make them hunt for support.

### Error Recovery Flow Output Format

When designing or fixing an error recovery flow, return:

```
ERROR: [What can fail]
LIKELIHOOD: [How often this happens — common / occasional / rare]
ANXIETY LEVEL: [Low / medium / high — affects reassurance tone]

WHEN IT FAILS:
  Auto-recovery: [What the system tries silently]
  User-visible message: [Refer to messaging-ux for exact wording]
  Primary action: [What the user can do — one clear option]
  Fallback action: [If primary fails, what's next]
  Escape hatch: [How to get human help]

WHAT STILL WORKS:
  - [Feature 1] — still available
  - [Feature 2] — still available
  - [Feature 3] — temporarily disabled, with explanation

REPEAT-FAILURE HANDLING:
  - 1st time: [response]
  - 2nd time: [escalation]
  - 3rd time: [human escalation]

PARTIAL FAILURE:
  [If applicable — what the user sees when some-but-not-all succeeded]
```

---

## Chapter 3: Progressive Disclosure

**Show users what they need, when they need it.** Not everything on day one. Not buried where they'll never find it. Right when it becomes relevant.

Most products fail in one of two directions:
- **Over-disclosure** — every feature visible on day one, the dashboard looks like a cockpit, new users feel overwhelmed
- **Under-disclosure** — power features hidden so deep users never discover them, the product feels limited

Progressive disclosure is the middle path: simple by default, capable when needed.

### The Three Layers

Every product feature lives in one of three visibility layers:

1. **Always visible** — core actions every user needs, every session
2. **Contextually surfaced** — shown when the user is in a moment where this feature helps
3. **Available on demand** — discoverable via search, settings, or "advanced" sections, but not in the way

When deciding which layer a feature belongs in, ask:
- **What percentage of users need this in their first session?** If under 20%, it's not layer 1.
- **Does it make sense without other context first?** If no, it's layer 2 or 3.
- **Is it dangerous or hard to undo?** If yes, layer 3 with a confirmation.

### When to Hide vs When to Show

**Hide by default if:**
- Less than 20% of users need it in any given session
- It only makes sense after the user has used a related feature first
- Showing it would crowd out the primary action
- It's powerful but rarely needed (bulk operations, advanced filters, integrations setup)

**Show by default if:**
- It's the primary action on this screen
- More than half of users will need it on their first visit
- Hiding it would make the user think the feature doesn't exist
- It's a safety-critical action (cancel, save, exit)

### Contextual Feature Introduction

The best moment to introduce a feature is the moment a user needs it. Not before.

**Examples:**
- A user hits the free-tier limit → *now* introduce the upgrade options, not on day one
- A user creates their fifth project → *now* introduce folders/organisation, not at signup
- A user has 3 unread notifications → *now* show "you can adjust which notifications you get → Settings"
- A user invites a teammate → *now* introduce roles and permissions, not in onboarding
- A user creates the same kind of thing twice → *now* introduce templates
- A user uses a feature for the third time → *now* surface the keyboard shortcut

The principle: **a feature introduced contextually feels like a helpful suggestion. The same feature introduced in a tutorial feels like homework.**

### Empty State as Disclosure Tool

Empty states are the most underused disclosure surface. A blank screen is an invitation to show:
- What this screen is for (orientation)
- What the user can do here (the one CTA)
- A hint at what's possible later (without overwhelming)

Don't try to teach the whole feature on the empty state. Show the one next step.

(messaging-ux covers the words. flow-ux ensures the right *moments* get an empty state design rather than just a blank screen.)

### Tooltips and Coachmarks: Use Sparingly

Tooltips that appear unprompted are a common over-disclosure trap. Rules:

- **One coachmark at a time, never a tour.** If you have five things to show, you have a product problem, not a tooltip problem.
- **Trigger by behaviour, not by time.** Show the tip when the user is about to do the thing it explains — not on a timer.
- **Dismissible and never repeat.** Once dismissed, gone forever. Re-showing a coachmark is condescending.
- **No tooltips for primary actions.** If your "Create Invoice" button needs a tooltip explaining what it does, the button copy is wrong.

The healthiest products use coachmarks rarely and intentionally — usually for genuinely new patterns, not for self-explanatory UI.

### Advanced Settings: Out of the Way, Findable

Power users need advanced controls. New users need to never see them.

The pattern:
- Default to the simplest possible interface
- Group advanced options in a clearly labelled section ("Advanced", "Developer options", "Power features")
- Make them searchable in any global search
- Never put advanced controls next to common ones — separation reduces cognitive load

**Anti-pattern:** a settings page with 40 options, half of which the user will never touch, all displayed at the same visual weight. That's not progressive disclosure — that's an information dump.

### When to Reveal Complexity

Some products *must* eventually expose complexity (legal tools, financial tools, design software). The goal isn't to hide complexity forever — it's to introduce it on the user's terms.

A staircase, not a cliff:

1. **Day one:** the user can do one simple thing well
2. **Week one:** the user discovers two or three more useful patterns
3. **Month one:** the user starts noticing the power features in their natural flow
4. **Power user:** the user finds the advanced section because they're ready

If a feature requires a tutorial to use, it's not yet ready to be shown to a new user.

### Progressive Disclosure Output Format

When auditing or designing for disclosure, return:

```
FEATURE: [Feature name]
CURRENT LAYER: [Always visible / contextually surfaced / available on demand]
RECOMMENDED LAYER: [Where it should live]

REASONING:
  - [Who needs it]
  - [When they need it]
  - [What happens if they don't see it]

CONTEXTUAL TRIGGER (if layer 2):
  Show when: [the specific moment / behaviour]
  Display as: [inline hint / toast / modal / inline upgrade prompt]
  Dismissal: [once-and-done / can be re-triggered if X]

IF MOVING LAYERS:
  Was: [previous placement]
  Becomes: [new placement]
  Migration: [how existing users discover it in its new place]
```

---

## Chapter 4: Offboarding

**Leaving is part of the product.** How a user leaves determines whether they ever come back, whether they recommend you, and whether they trust you the next time they sign up for anything.

Most cancellation flows are designed to prevent the user from leaving. Human-centric cancellation flows are designed to *let them leave well* — and turn a goodbye into a relationship.

### The Goodbye Principle

> A user who leaves easily and respectfully is more likely to return than a user who had to fight their way out.

Every desperate save-attempt — the hidden cancel button, the mandatory phone call, the guilt-trip survey, the "are you really sure" page after page — is a short-term win at the cost of long-term trust. The user remembers it. They tell other people. They don't come back.

Treat the exit like the front door: clean, clear, and well-lit.

### The Cancellation Flow Skeleton

A human-centric cancellation flow has five steps, in this order:

1. **Cancel is one click away** — findable in account/billing settings, not buried
2. **A short, optional reason** — one question, easy to skip
3. **A relevant save offer (only if it fits)** — never the same offer to everyone
4. **Confirmation of what happens next** — when access ends, what to data, how to come back
5. **A graceful goodbye** — short, kind, no guilt

Anything more than five steps is friction the user will resent.

### Step 1: Cancel Must Be Findable

If the user has to search for how to cancel, you've already lost their trust.

- "Cancel subscription" should be in the obvious place — account settings, billing page
- It should be a normal-looking link or button, not a tiny grey footer text
- Don't require a customer service call to cancel anything that can be signed up for online
- Don't require chatting with a bot or filling out a contact form
- One click from "I want to cancel" to "here's the cancellation flow"

The principle: **if it took one click to sign up, it should take one click to start cancelling.**

### Step 2: The Exit Survey

Ask one question. Make it optional. Make it human.

**What to ask:**
- "What made you decide to cancel?" — open and non-judgmental
- A few simple options: too expensive / not using it enough / found something better / temporary break / other
- Optional free-text field for context

**What not to ask:**
- A 10-question survey before they can cancel
- Required fields blocking the cancel button
- Defensive questions like "are you sure you understand what you're losing?"
- Leading questions trying to surface objections you can rebut

The exit survey is for *you* to learn from — not for you to argue with the user. If they fill it out, you got useful data. If they skip it, you respected their time.

### Step 3: Save Offers, Done Respectfully

A save offer is appropriate *only when it actually fits the reason the user gave*. A blanket "20% off if you stay!" thrown at every cancellation is desperate and obvious.

| User's reason | Appropriate save offer (if any) |
|---------------|----------------------------------|
| Too expensive | A discount or a cheaper plan that matches their usage |
| Not using it enough | Pause subscription for 1–3 months instead of cancelling |
| Missing a feature | Roadmap update if it's coming, or honest acknowledgment if not |
| Temporary break | Pause option, "we'll keep your data safe for X months" |
| Found something better | No save offer. Wish them well. Ask one optional question about what they liked there. |
| Just not the right tool | No save offer. Make leaving easy. |

The principle: **a save offer should feel like a thoughtful "what about this instead?" — never like a bargaining tactic.**

If you can't offer something genuinely relevant, skip the save offer entirely. Letting someone leave without a final pitch is itself a trust signal.

### Step 4: Confirmation — What Happens Next

This is the most important screen in the whole flow. The user needs to know exactly:

- **When access ends** — specific date and time
- **What happens to their data** — kept, deleted, exportable, for how long
- **How to come back** — make it easy, no guilt, just the path
- **What's still accessible** — final invoices, exports, account info

Example:
> "Your Pro plan will be cancelled at the end of your billing period — May 31, 2026.
>
> Until then, everything still works as normal. After that, your account becomes read-only — you can still view and export your data for 30 days. After June 30, your data is permanently deleted.
>
> Need anything before then? → Export your data | Download invoices
>
> Change your mind? → Reactivate any time."

No surprises. No hidden timers. No data disappearing without warning.

### Step 5: Data Export — Make Leaving Easy

The single biggest trust signal in any product is how easy it is to take your data with you. Make export:

- **One click from the cancellation flow** — not hidden in another menu
- **Comprehensive** — everything the user created, in formats they can actually use (CSV, JSON, PDF, not a proprietary format)
- **Available before and after cancellation** — give them a 30-day window minimum
- **Without limits** — don't gate exports behind upgrade tiers when someone is cancelling

A user who exports their data and leaves easily is a user who tells friends "I used to use them — they were great, totally fair about it." That's the recommendation you want.

### The Graceful Goodbye Screen

Final screen. Short. Kind. No guilt.

| Fun level | Graceful goodbye |
|-----------|------------------|
| 🎭 Go for it | "You're free! Thanks for being a customer — we hope to see you again someday. Your data is safe for 30 days if you change your mind." |
| 😊 Warm | "You're all set. Your subscription ends on May 31. Thanks for being with us — your data is safe for 30 days if you ever want to come back." |
| 🧱 Straight | "Subscription cancelled. Access ends May 31, 2026. Data available for 30 days." |

No emotional manipulation. No "we'll miss you so much" theatrics. Just a clean close.

### Account Deletion (Distinct from Cancellation)

Cancelling a subscription is not the same as deleting an account. Make both possible, separately:

- **Cancel subscription** = stop paying, keep account, downgrade to free / read-only
- **Delete account** = permanently remove everything

For account deletion, the flow is similar but with stronger confirmation:
- Make it findable (account settings → "Delete account")
- Explain exactly what gets deleted and what doesn't (some data may be legally required to retain)
- Specify the timeline — "Deletion takes 30 days. You can cancel during this window."
- Confirmation screen with the actual word typed out: "Type DELETE to confirm" — high friction for this irreversible action
- Final goodbye after deletion: "Your account has been removed. We're sorry to see you go."

The friction here is appropriate — this is irreversible. But it should be friction the user can complete, not friction designed to block them.

### Win-Back: Earned, Not Aggressive

After a user leaves, the win-back strategy determines whether they ever come back.

**What works:**
- One email at 30 days: "Your data is about to be deleted. Want to grab it or come back?"
- One email at 90 days: "We've shipped these things since you left — want to take another look?"
- A persistent, no-pressure "Reactivate" path in their account if they're still logged in

**What doesn't work:**
- Daily emails for two weeks after cancellation
- Guilt-based subject lines ("We miss you 😢")
- Re-targeting ads that follow them around the internet
- Dark patterns making it hard to unsubscribe from win-back emails

The principle: **make coming back easy. Don't make leaving feel followed.**

### Offboarding Flow Output Format

When designing or auditing an offboarding flow, return:

```
FLOW: Cancellation / Account deletion / Pause
TRUST WEIGHT: [How much this moment shapes long-term reputation — usually: high]

STEP 1 — Initiate
  Findability: [Where the user starts this flow]
  Clicks from account: [Count]

STEP 2 — Optional reason
  Question: [One question, refer to messaging-ux for wording]
  Skippable: [Yes/No — must be yes]

STEP 3 — Save offer (conditional)
  If reason = [X], offer: [matching alternative]
  If reason = [Y], offer: [matching alternative]
  Otherwise: no offer, proceed to confirmation

STEP 4 — Confirmation
  Access ends: [Specific date / timing rule]
  Data retention: [How long, in what state]
  Comeback path: [How to reactivate]
  Final exports: [What's available]

STEP 5 — Goodbye
  Tone: [Match fun level]
  No-guilt: [Confirmed]

POST-EXIT:
  Win-back cadence: [What emails, when]
  Data deletion timing: [When the data is actually gone]
  Reactivation path: [Self-service or required contact]
```

---

## Page-Aware Mode for Flows

**When working inside a codebase, detect what flow the user is working on and apply the right chapter automatically.** Don't wait to be told.

### How to detect the flow type

Read the file and surrounding routes. Look at:

- Route or URL path (`/onboarding`, `/welcome`, `/signup`, `/cancel`, `/error`, `/settings/billing`)
- Component name (`WelcomeFlow`, `CancellationModal`, `ErrorBoundary`, `OnboardingStep3`)
- File structure (`flows/onboarding/`, `flows/cancel/`, `pages/setup/`)
- Content patterns — a 5-step wizard = onboarding, a "reason for cancelling" form = offboarding

### Flow-specific entry points

| Detected flow | Apply chapter |
|---------------|---------------|
| `/onboarding`, `/welcome`, `/setup`, `OnboardingStep`, `Welcome` | Chapter 1: Onboarding |
| `ErrorBoundary`, `/error`, retry handlers, fallback components | Chapter 2: Error Recovery |
| Feature gates, settings layouts, "advanced" sections, coachmarks | Chapter 3: Progressive Disclosure |
| `/cancel`, `CancellationFlow`, `DeleteAccount`, `/account/billing` | Chapter 4: Offboarding |

Apply the relevant chapter's principles automatically. Reference messaging-ux for any specific wording on the screens.

---

## Flow Audit Mode

**When asked to audit a codebase or product for flow issues, produce a Flow Audit Report.**

The audit identifies four categories of issues, in priority order:

### 1. Missing Flows

Flows that should exist but don't. The most common gaps:

- No onboarding at all — users land in an empty product with no orientation
- No empty states for screens that start empty
- No error recovery — errors are dead ends with no path back
- No cancellation flow — users have to contact support to leave
- No "what happens to my data" explanation on cancellation
- No partial-failure handling for bulk actions

### 2. Dead Ends

Screens with no clear path forward. Look for:

- Error pages with no "try again" or "go back"
- Empty states with no CTA
- "Access denied" screens with no path to gaining access
- Loading states that can fail silently with no fallback
- Confirmation screens that don't suggest a next step
- Forms that submit and show nothing

### 3. Anxiety Moments Without Reassurance

High-emotional-weight moments missing the reassurance they need:

- Payment screens without security reassurance
- Destructive actions without clear consequence explanations
- Data deletion without recovery information
- Cancellation without "your data is safe for X days"
- Account changes without a "we sent you a confirmation email" follow-up
- Errors involving money or data loss without explicit "no charge was made" / "your work is saved" reassurance

### 4. Drop-Off Risks

Patterns that make users abandon mid-flow:

- Onboarding longer than 5 steps with no progress indication
- Required fields that should be optional ("Add your company website to continue")
- Asking for information before showing any value
- Steps that don't explain why they exist
- Skip buttons hidden or disabled
- Free-trial flows that demand a credit card before the user has done anything
- Cancellation flows with more than 5 steps or unnecessary friction
- Save offers that don't match the user's stated reason

### Audit Output Format

```
FLOW AUDIT REPORT
App: [Detected app name]
Audience: [Detected audience]
Scanned: [Routes, components, or directories]

═══════════════════════════════════════════
MISSING FLOWS — [N found]
═══════════════════════════════════════════

1. [Flow name]
   WHERE: [Where it should exist in the app]
   WHY IT MATTERS: [What breaks without it]
   RECOMMENDED: [The flow skeleton — refer to relevant chapter]

═══════════════════════════════════════════
DEAD ENDS — [N found]
═══════════════════════════════════════════

1. [Screen / component name] — [file location]
   PROBLEM: [What happens / what's missing]
   FIX: [Specific next-step to add]

═══════════════════════════════════════════
ANXIETY MOMENTS WITHOUT REASSURANCE — [N found]
═══════════════════════════════════════════

1. [Moment] — [file location]
   USER FEELS: [Emotional state]
   MISSING: [What reassurance is absent]
   ADD: [Specific addition — refer to messaging-ux for exact words]

═══════════════════════════════════════════
DROP-OFF RISKS — [N found]
═══════════════════════════════════════════

1. [Flow / step] — [file location]
   RISK: [What's likely making users abandon]
   FIX: [Specific change]

═══════════════════════════════════════════
PRIORITISED RECOMMENDATIONS
═══════════════════════════════════════════

Quick wins (under 1 day each):
  1. [Item]
  2. [Item]

Medium efforts (1–3 days):
  1. [Item]

Larger restructures (more than 3 days):
  1. [Item]
```

Always provide concrete fixes — never just flag problems without solutions. For any wording changes, defer to messaging-ux and note: *"See messaging-ux for the exact copy."*

---

## How flow-ux and messaging-ux Work Together

These two skills are designed to be used in tandem. They never overlap — they handle different layers of the same problem.

| Question | Skill to use |
|----------|--------------|
| What screens should this flow have? | flow-ux |
| What should this screen say? | messaging-ux |
| In what order should these steps go? | flow-ux |
| How should this error message be worded? | messaging-ux |
| Should this error have a retry, a fallback, or both? | flow-ux |
| What's the tooltip on this field? | messaging-ux |
| Should this field be in onboarding or settings? | flow-ux |
| What does the "Saved!" confirmation say? | messaging-ux |
| Should there be a confirmation at all? | flow-ux |
| Where does the cancellation button live? | flow-ux |
| What does the cancellation button say? | messaging-ux |

When designing a new flow from scratch, the natural flow of work is:

1. flow-ux maps the screens, the order, the logic
2. messaging-ux fills in the words on each screen
3. Both reference the same product profile in `profiles/`

When auditing an existing product:

1. flow-ux runs the Flow Audit — finds missing flows, dead ends, anxiety moments, drop-off risks
2. messaging-ux runs the Copy Audit — finds doubtful labels, missing help text, error wording
3. Combined report shows both layers of issues, prioritised together

---

## Quick Reminders

- A flow is a journey, not a form. Every step earns its place.
- Defer everything that can be deferred. Ask later, not now.
- An error is a detour, not a wall. Always provide a way back.
- Make leaving as easy as joining. Trust is built at the exit.
- The aha moment comes first. Polish comes later.
- If you can't explain why a step exists, delete the step.
- The best flows feel invisible. Users shouldn't notice the journey — they should just arrive.
