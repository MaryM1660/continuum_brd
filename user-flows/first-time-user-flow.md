# First-Time User Flow

## Overview

The first-time user flow covers everything from app install to the moment a user has completed their first coaching session and understands the platform's value. Split into mobile and web onboarding.

---

## Mobile — First-Time Flow

```
1. User downloads Continuum mobile app
        │
        ▼
2. WELCOME SCREEN
   "Your AI career coach"
   [Continue with LinkedIn]
        │
        ▼
3. LINKEDIN OAUTH FLOW
   System browser / in-app LinkedIn auth
   User grants permissions (name, email, profile)
        │
   ✅ Auth success
        │
        ▼
4. [OPTIONAL] CONTEXT SETUP SCREEN
   "What are you working toward?"
   Current role (pre-filled from LinkedIn if available)
   Target direction (text or dropdown)
   [Start my first session →]
        │
   [OR: coach gathers this in first session — open question]
        │
        ▼
5. FIRST COACHING SESSION
   Coach greets by name
   Coach asks opening question (career direction, current situation)
   Conversation unfolds (10–20 min recommended for first session)
   Coach extracts first XYZ/STARL candidates
        │
        ▼
6. SESSION ENDS
   User taps [End session] or time limit reached
        │
        ▼
7. SESSION SUMMARY SCREEN
   "Session complete — 3 items captured"
   XYZ: 1 | STARL: 1 | Plan insights: 1
   "Synced to your web workspace ✓"
   [View summaries] [Done]
        │
        ▼
8. WELCOME BACK SCREEN (ready for next session)
```

**Key outcome:** User has experienced the core loop (talk → capture → sync) and knows the platform works.

**Critical success metric:** At least 1 XYZ or 1 STARL captured in first session.

---

## Web — First-Time Flow

```
1. User opens Continuum web (link from email / app recommendation)
        │
        ▼
2. LINKEDIN OAUTH (same account as mobile)
   Recognized as existing user (from mobile auth)
   OR: New user creating account on web first
        │
        ▼
3. TODAY SCREEN (Preparing mode)
   User lands on Today screen
   Market Readiness: shows % based on data from mobile sessions
        │
   If coming from mobile: some data already populated
   If web-first: near-empty state with clear onboarding prompts
        │
        ▼
4. ONBOARDING PROMPTS (first visit)
   "Welcome to your web workspace" banner
   Checklist of setup steps:
   ○ Set your active target (Target Picker)
   ○ Review items from your voice sessions (Voice Inbox)
   ○ Check your Gap Assessment
   ○ Start your Resume Studio
   [Close — I'll explore on my own]
        │
        ▼
5. USER EXPLORES
   Typically follows: Voice Inbox → Resume Studio → Plans → Gap Assessment
        │
        ▼
6. FIRST RESUME VERSION
   User creates their first resume version in Resume Studio
   Market Readiness score increases
```

---

## Key Decision Points

| Decision | What Happens |
|---|---|
| LinkedIn auth cancelled on mobile | Return to welcome screen, can retry |
| User skips context setup | Coach asks during first session (more friction in session start) |
| No mobile session before web | Web shows near-empty states with prompts to start mobile session |
| User starts on web (no mobile) | Can manually enter XYZ/STARL, but primary flow is mobile-first |

---

## Empty State Strategy (Web, No Mobile Data)

If user opens web without having done any mobile sessions:

- Voice Inbox: "No items yet. Start a coaching session on your mobile to fill this up."
- XYZ bank: "No achievements yet. Talk to your coach to capture your first XYZ."
- STARL bank: "No stories yet. Ask your coach to help you structure a behavioral story."
- Gap Assessment: "Complete your Ideal Profile first to see your gaps."
- Market Readiness: "0% — let's build your profile."

Empty states always have a clear CTA — either to mobile ("Start a session") or to the relevant web screen.
