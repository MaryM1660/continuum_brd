# Mobile Screens

## Screen Inventory

| Screen | Route / State | Status |
|---|---|---|
| Welcome / Splash | first launch | MVP |
| LinkedIn Auth | first launch | MVP |
| Context Setup | post-auth, first time | MVP (open question: skip?) |
| Talk Screen | main session UI | MVP — core |
| Teleprompter Panel | overlay on Talk | MVP |
| Session Summary | post-session | MVP |
| Summaries (history) | side drawer → summaries | MVP |
| Welcome Back | returning user | MVP |
| Side Drawer | navigation overlay | MVP |
| Account Screen | side drawer → account | MVP |
| Paywall Screen | limit reached | MVP (design TBD) |

---

## Screen Descriptions

### Welcome / Splash
**When:** App launch (first time only after that goes to Welcome Back)
**Content:**
- Continuum logo / wordmark
- One-line value prop: "Your AI career coach"
- [Continue with LinkedIn] button (amber, full width)
- Brief note: "Sign in to save your coaching progress"

**Transitions to:** LinkedIn OAuth flow

---

### LinkedIn Auth
**When:** After welcome screen tap
**Content:** Standard LinkedIn OAuth — handled by system (in-app browser or native SDK)
**On success:** Creates account → Context Setup (or directly to first session)
**On cancel/fail:** Returns to Welcome screen with error state

---

### Context Setup
**When:** After first-time auth (one-time only)
**Purpose:** Give the coach minimal starting context so first session isn't cold-start
**Content:**
- "What are you working toward?" (headline)
- Current role (pre-filled from LinkedIn if available, editable)
- Target direction (text field with suggestions: "Fintech PM", "Engineering Manager", etc.)
- [Start my first session →] button

> **Open question:** May be removed entirely — coach can gather this through conversation.

---

### Talk Screen (Core)
**When:** Active coaching session
**See:** [Voice Session mechanics](voice-session.md) for full detail

**Key elements:**
- Coach avatar / name at top
- Live transcript or waveform visualization
- Coach's current question (displayed as text below waveform)
- Large mic button (pulsing animation when recording)
- Secondary controls: Pause, Teleprompter toggle, End session
- Session duration timer (subtle, in corner)

**Paywall state:** When time/session limit approached — banner appears "X minutes remaining" (design TBD)

---

### Teleprompter Panel
**When:** User taps teleprompter button during active session
**Purpose:** Display coach's question as large, readable text — for hands-free use
**Layout:** Full-screen overlay with dark background
- Large text: current coach question
- Mic button still accessible at bottom
- [Close] to return to Talk Screen

---

### Session Summary
**When:** Immediately after session ends
**Content:**
- "Session complete" header
- Duration
- Items captured (grouped by type): XYZ (N), STARL (N), Plan insights (N), etc.
- "Synced to your web workspace ✓" confirmation
- [View summaries] → navigates to Summaries screen
- [Done] → returns to Welcome Back

---

### Summaries (History)
**When:** User navigates from Side Drawer or Session Summary
**Content:**
- List of past sessions, newest first
- Each session card:
  - Date + duration
  - Items captured (brief list)
  - [View details] → shows full extracted items for that session
- Scroll to load more

---

### Welcome Back
**When:** App launch for returning user (after first session)
**Content:**
- "Good morning / afternoon / evening, [Name]"
- Last session info: date, duration, items captured
- Optional: "New in your web workspace: N items" (if sync pending)
- [▶ Start session] — primary CTA
- [View summaries] — secondary

---

### Side Drawer
**When:** Swiped from left edge or menu icon tapped
**Content (top to bottom):**
- User avatar + name + current role
- Navigation links:
  - Coach (Talk Screen)
  - Summaries
  - Account
- Divider
- "Open web workspace →" (deep link to web platform)
- Sign out (bottom)

---

### Account Screen
**When:** Side Drawer → Account
**Content:**
- Profile: Name, email, LinkedIn badge
- Subscription status: Free / Premium + renewal date
- Plan: active target (synced from web)
- [Manage subscription] → paywall / billing
- [Disconnect LinkedIn] (with confirmation)
- [Delete account] (with confirmation + warning)
- App version

---

### Paywall Screen
**When:** User reaches free tier limit (session count or time limit)
**Design:** TBD — see [Open Questions](../open-questions.md) and [Paywall](../business/paywall.md)

**Known requirements:**
- Must communicate value clearly before asking for money
- Should show what was already captured in free session (proof of value)
- CTA: Subscribe to continue
- Pricing options: monthly / annual (pricing TBD)
- [Maybe later] — not a full dead end

---

## Navigation Model

```
App launch
    │
    ├── First time → Welcome → LinkedIn Auth → Context Setup → Talk Screen
    │
    └── Returning → Welcome Back ─────────────────────────────┐
                                                               │
                            ┌──────────────────────────────── ▼ ────┐
                            │           TALK SCREEN (core)           │
                            │         ┌─────────────────┐           │
                            │         │ Teleprompter     │           │
                            │         │ (overlay)        │           │
                            │         └─────────────────┘           │
                            └──────────────────┬────────────────────┘
                                               │ session ends
                                               ▼
                                        Session Summary
                                               │
                            ┌──────────────────┼──────────────────┐
                            ▼                  ▼                   ▼
                       View summaries      Done (Welcome Back)  [Other nav]

Side Drawer (accessible from any screen):
    ├── Coach → Talk Screen
    ├── Summaries → Summaries Screen
    ├── Account → Account Screen
    └── Open web workspace → browser
```
