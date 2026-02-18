# Notifications Strategy

## Overview

Notifications are the external trigger that brings users back to the product between natural usage moments. Done right, they feel helpful and timely. Done wrong, they feel spammy and get disabled.

**Core principle:** Every notification must be actionable and contextually relevant. No vanity notifications ("Check out what's new!").

---

## Notification Channels

| Channel | Platform | When Available |
|---|---|---|
| Push notifications | Mobile | After first session, if permission granted |
| In-app banners | Mobile | Always (during app use) |
| In-app badges | Web (sidebar) | Always (during web use) |
| Web browser notifications | Web | After permission granted (optional) |
| Email | Both | After account creation |

> **Open question:** Which channels are in MVP? Minimum viable = push (mobile) + email. Web browser notifications are lowest priority. See [Open Questions](../open-questions.md).

---

## Permission Strategy

### Mobile Push Permission
**When to ask:** After the first session ends, on the Session Summary screen — not before.
**Framing:** "Get notified when it's time to follow up on your applications" (benefit-first, not "allow notifications")
**If denied:** Fall back to in-app prompts only. Do not repeatedly ask.

### Email
Collected at LinkedIn auth time. Used for:
- Account confirmation
- Re-engagement sequences (see below)
- Critical alerts (subscription expiry, etc.)

Users can unsubscribe from non-critical emails.

---

## Notification Taxonomy

### A. Action Required (highest priority)
Notifications that require user action today.

| Trigger | Channel | Message | CTA |
|---|---|---|---|
| Follow-up due today | Push + Email | "Follow-up with [Company] due today" | Open application |
| Follow-up overdue | Push + Email | "Overdue: follow up with [Company] (was due [date])" | Open application |
| Interview tomorrow | Push | "Interview with [Company] tomorrow at [time] — Prep Pack ready" | Open Prep Pack |
| Interview in 2 hours | Push | "Interview with [Company] in 2 hours. All set?" | Open Prep Pack |
| Application stuck >N days | Push (weekly digest) | Included in weekly digest | Open Pipeline |

### B. Progress & Momentum (medium priority)
Notifications that reinforce progress and encourage continued use.

| Trigger | Channel | Message | CTA |
|---|---|---|---|
| New Voice Inbox items synced | Push | "5 new items from your coaching session are in your workspace" | Open Voice Inbox |
| Market Readiness milestone (+10%) | Push (once per milestone) | "You hit 70% market readiness — keep going!" | Open Today |
| First XYZ created | Push (once) | "First achievement captured! Your career profile is taking shape." | Open Resume Studio |
| Resume version created | Push (once) | "Your [name] resume is ready — 72% match for your target" | Open Resume Studio |
| Weekly progress summary | Email (weekly) | "This week: 2 sessions, 3 new items, readiness +5%" | Open Today |

### C. Re-engagement (lower priority, time-delayed)
Triggered by inactivity. Goal: bring user back before they fully churn.

| Trigger | Delay | Channel | Message | CTA |
|---|---|---|---|---|
| No mobile session | 7 days | Push | "Your coach is ready when you are" | Start session |
| No mobile session | 14 days | Push + Email | "You have [N] unfinished items waiting. Pick up where you left off." | Start session |
| No mobile session | 30 days | Email | "Alex, your career profile is [X]% complete. 15 minutes could change that." | Deep link to app |
| No web open | 7 days | Email | "You have [N] new items in your Voice Inbox" | Open web |
| No web open | 30 days | Email | "[N] coaching session items haven't been reviewed yet" | Open web |
| Subscription expires soon | 7 days before | Push + Email | "Your subscription renews in 7 days" | Manage subscription |
| Subscription expired | Day of | Email | "Your subscription has expired — your data is safe" | Renew |

### D. In-App Only (no push/email)
These are surfaced only when user is already in the app.

| Trigger | Where | Message |
|---|---|---|
| New Voice Inbox items | Sidebar badge (web) | Badge count updates |
| Application needs attention | TopBar (web) | "Needs attention: 2" |
| Pipeline stuck | Today Active (web) | "2 applications stuck — check your pipeline" |
| Plans need calibration | Sidebar Plans badge | Badge "1" |
| Next Best Step changed | Today Preparing | Card updates automatically |

---

## Frequency Caps

To prevent notification fatigue:

| Category | Max frequency |
|---|---|
| Action required (follow-up due) | 1 push per application per day |
| Progress notifications | 1 push per day maximum |
| Re-engagement | Max 1 push per week, max 2 emails per month |
| Weekly digest | 1 email per week (opt-out available) |
| Any channel combined | Max 3 push notifications per day |

---

## Quiet Hours

Push notifications should respect device quiet hours settings.
Default quiet hours: 10pm–8am local time.
Override: only for interview reminders (user explicitly scheduled).

---

## Personalization

Notifications should use user data where available:

- Always use first name: "Alex, your coach is ready..."
- Reference specific company names: "Follow-up with NeoBank due today"
- Reference actual counts: "5 new items" not "new items"
- Reference specific readiness %: "You're at 62% — here's what to do next"

Generic notifications ("Check out the app!") are never sent.

---

## Email Templates

### Weekly Progress Digest
**Subject:** "Your week in Continuum, [Name]"
**Send day:** Monday morning (7–9am local)
**Content:**
- Sessions this week: N
- Items captured: N XYZ, N STARL
- Market Readiness: X% (was Y%)
- Next Best Step: [specific task]
- Follow-ups due this week: N

**Opt-out:** Available per-email and in Settings

### Re-engagement (day 7)
**Subject:** "Ready when you are, [Name]"
**Content:**
- Simple, warm, not pushy
- What was captured in last session (proof of value)
- One clear CTA to start a session
- No bulleted feature list

### Re-engagement (day 14)
**Subject:** "[N] items are waiting in your workspace"
**Content:**
- Specific items that are in Voice Inbox / Career Profile
- Frame as "things that exist but aren't being used yet"
- Clear CTA

### Re-engagement (day 30)
**Subject:** "Is now still the right time, [Name]?"
**Content:**
- Acknowledge the gap without guilt-tripping
- Ask if their situation changed (job search paused? got a new role?)
- If not: give them a reason to come back
- If they've moved on: easy unsubscribe, "we'll be here when you're ready"

---

## What We Don't Send

- Promotional / marketing emails to existing users (spam)
- "Feature update" notifications (unless a critical fix)
- Notifications without a clear action
- More than 1 push per day in non-urgent scenarios
- Any notification before the first session is completed

---

## MVP Scope

> **Open question:** Which notifications are in MVP? See [Open Questions](../open-questions.md).

**Recommended MVP minimum:**
1. Follow-up due (push + email) — directly drives job search outcomes
2. Interview tomorrow reminder (push) — directly drives interview prep
3. New Voice Inbox items synced (push) — closes the mobile→web loop
4. Re-engagement at 7 days (push) — retention
5. Re-engagement at 14 days (email) — retention

**Defer to post-MVP:**
- Weekly digest email
- Progress milestone notifications
- Web browser notifications
- Subscription reminders (needed at scale, not day 1)
