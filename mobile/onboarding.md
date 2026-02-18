# Mobile Onboarding

## Overview

Onboarding is the first experience a new user has with Continuum on mobile. The design goal: **get from zero to first coaching session as fast as possible**, while establishing the identity foundation the whole platform needs.

---

## Decided

- **LinkedIn authentication is mandatory.** No guest mode in MVP.
- **LinkedIn auth is the first screen.** User cannot skip or defer it.
- **Goal:** Minimize friction between LinkedIn auth and first voice session.

---

## Onboarding Flow

```
App launch (first time)
    │
    ▼
┌─────────────────────────────────┐
│  WELCOME SCREEN                 │
│  "Your AI career coach"         │
│  Brief value prop (1-2 lines)   │
│  [Continue with LinkedIn]       │
└─────────────────────────────────┘
    │
    ▼
LinkedIn OAuth flow (system browser / in-app)
    │
    ▼
Auth success → backend creates account
    │
    ▼
┌─────────────────────────────────┐
│  CONTEXT SETUP (1 screen only)  │
│  "What are you working toward?" │
│  • Current role (pre-filled     │
│    from LinkedIn if available)  │
│  • Target direction (text input │
│    or dropdown: "Fintech PM",   │
│    "Engineering Manager", etc.) │
│  [Start my first session →]     │
└─────────────────────────────────┘
    │
    ▼
First coaching session begins
(Coach greets, references context just entered)
```

> **Open question:** Does the context setup screen exist at all, or does the coach gather this information through the first conversation? The session-first approach is lower friction but gives the coach less context to start with. See [Open Questions](../open-questions.md).

---

## LinkedIn Auth — What We Use

| Data | Used for |
|---|---|
| Name | Account display, coach greeting |
| Email | Account identity |
| Current role / company | Pre-fill career context, reduce first-session setup questions |
| Profile headline | Additional context hint for coach |

> **Open question:** Exact scope of data requested from LinkedIn OAuth permissions. Requesting too much can reduce auth conversion. Minimum viable: name + email. See [Open Questions](../open-questions.md).

---

## First Session Experience

The first session is critical for demonstrating value. Design goals:
1. User feels heard and understood within the first 2 minutes
2. Coach quickly establishes what the user is working toward
3. At least one XYZ or STARL captured before session ends
4. User understands what just happened — the summary screen shows it clearly

**Hypothetical opening (if context screen was skipped):**
> Coach: "Hi Alex, welcome to Continuum. I'm your career coach. Before we dive in — in one sentence, what career move are you thinking about right now?"

**Hypothetical opening (if context was provided):**
> Coach: "Hi Alex — I see you're a Senior PM at DataFlow, and you're interested in making a move into fintech. That's a great direction. Tell me — what's driving that interest? Is this something recent, or has it been on your mind for a while?"

---

## Returning User (Welcome Back)

After the first session, returning users see a **Welcome Back** screen instead of onboarding:

```
┌─────────────────────────────────┐
│  WELCOME BACK                   │
│  "Good morning, Alex"           │
│  Last session: Yesterday 2:02PM │
│  "You captured 3 items — 2 XYZ  │
│   and 1 STARL. Ready to         │
│   continue?"                    │
│                                 │
│  [▶ Start session]              │
│  [View summaries]               │
└─────────────────────────────────┘
```

The Welcome Back screen reduces the cognitive load of re-entry: user doesn't have to remember where they left off.

---

## Error States

| Scenario | Handling |
|---|---|
| LinkedIn auth cancelled | Return to welcome screen with "Sign in to continue" message |
| LinkedIn auth fails (network) | Error screen with retry button |
| Account creation fails | Error with "Try again" — support contact link |
| First session network error | Graceful degradation — explain session can't start, try again |
