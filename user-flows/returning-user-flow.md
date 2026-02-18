# Returning User Flow

## Overview

A returning user is someone who has already completed onboarding and at least one coaching session. This covers re-entry patterns for both mobile and web.

---

## Mobile — Returning User

### Standard return (daily habit user)
```
Open app
    │
    ▼
Welcome Back screen
  "Good morning, Alex"
  Last session: Yesterday 2:02 PM
  "You captured 2 XYZ and 1 STARL. Ready to continue?"
  [▶ Start session]  [View summaries]
    │
    ▼
Coaching session starts
Coach references previous session:
  "Last time we were talking about the platform migration —
   I'd love to get more detail on the outcome today."
```

### Return after long absence (>2 weeks)
```
Open app
    │
    ▼
Welcome Back screen (adapted messaging)
  "Welcome back, Alex — it's been a while."
  "Last session: 3 weeks ago"
  "You have 4 items in your web workspace."
  [▶ Start session]
    │
    ▼
Session opening (coach acknowledges the gap):
  "Good to see you back. A lot can happen in a few weeks —
   any updates on the DataFlow situation you mentioned?"
```

### Return before an interview
```
Open app (user has interview tomorrow)
    │
    ▼
Welcome Back screen (interview-aware)
  "Acme Inc. interview tomorrow at 10am"
  "Prep Pack ready: 3 STARL stories + 2 XYZ"
  [▶ Start interview prep session]  [View Prep Pack (web)]
    │
    ▼
Session focuses on interview preparation:
  Coach runs mock behavioral questions
  Helps refine weak STARL stories
  Captures any new XYZ from recent experience
```

---

## Web — Returning User

### Standard return (weekly check-in)
```
Open web platform → LinkedIn auth (already authenticated, skip if session active)
    │
    ▼
Today screen loads
  - Voice Inbox badge: "5 new items" from recent mobile session
  - Readiness Checklist updated
  - Next Best Step recommendation (possibly changed)
    │
    ▼
User checks Voice Inbox first (badge draws attention)
    │
    ▼
Reviews new items, edits as needed
    │
    ▼
Works on Next Best Step (e.g., creates Fintech PM Resume version)
    │
    ▼
Market Readiness updates: 62% → 68%
```

### Return specifically to manage pipeline (Active mode)
```
Open web → Today (Active mode)
  - Apply Queue shows queued applications
  - Follow-ups: "1 due today — Acme Inc."
  - Calendar: interview tomorrow
    │
    ▼
User sends 2 applications from Apply Queue
    │
    ▼
User logs follow-up for Acme Inc.
    │
    ▼
User opens Prep Pack for tomorrow's interview
    │
    ▼
Done — 20 minutes total
```

---

## Re-engagement After Inactivity

When a user hasn't opened the web platform for >7 days:

**On next web open:**
- "Welcome back" banner (non-intrusive)
- "Since your last visit: N items in Voice Inbox, M days in Active mode"
- Suggested action: "You have 2 applications stuck — check your Pipeline"

**Email / push notification (if enabled):**
- "Alex, you have a follow-up due today for Acme Inc."
- "3 new items captured in your last coaching session are ready to review"

> **Open question:** Email / push notification design TBD. See [Open Questions](../open-questions.md).
