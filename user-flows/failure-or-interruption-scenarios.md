# Failure & Interruption Scenarios

## Overview

How the product handles errors, network failures, interruptions, and edge cases. Designed to maintain user trust and prevent data loss.

---

## Mobile Scenarios

### Network lost mid-session
**Scenario:** Internet drops while coaching session is active.
```
Network drops
    │
    ▼
Continue recording locally (audio buffer)
Coach detects loss → stops responding
Banner: "Connection lost — your session is being saved locally"
    │
    ▼
Network restores within session
    │ yes → resume seamlessly, sync buffered audio
    │ no (user ends session)
    ▼
Session ends with partial data
Local extraction runs on available transcript
Items synced when connection restores
Session summary shows "partial sync" warning
```

### Microphone permission denied
```
User taps "Start session"
    │
    ▼
App checks microphone permission
    │
    ├── Denied → Explain why needed:
    │           "Continuum needs microphone access to work as a voice coach."
    │           [Open Settings]  [Not now]
    │
    └── Granted → Session starts normally
```

### STT failure (speech not recognized)
```
User speaks but STT returns low-confidence or empty result
    │
    ▼
Coach: "Sorry, I didn't catch that — could you say that again?"
    │
If repeated failure (3x):
    │
    ▼
Coach: "It seems the audio quality isn't great right now.
        Are you in a noisy environment? Try moving somewhere quieter."
    │
If still failing:
    ▼
Offer text input fallback (MVP: TBD whether text input exists)
```

### Paywall limit reached mid-session
**Status: Design TBD** — see [Open Questions](../open-questions.md) and [Paywall](../business/paywall.md).

**Candidate behaviors:**
- A) Coach finishes current sentence, then gracefully transitions: "I'd love to continue — let's set you up with a subscription"
- B) Session ends naturally; paywall appears before next session start

### App crashes during session
```
App crashes
    │
    ▼
On relaunch:
"It looks like your last session was interrupted."
"We've saved everything up to [timestamp]."
[Review what was saved]  [Start new session]
```

---

## Web Scenarios

### Network drops on web
```
User is editing XYZ achievement
Network drops
    │
    ▼
Unsaved changes highlighted
"Connection lost — changes not saved"
Retry animation (auto-retry every 5s)
    │
On reconnect:
Auto-save attempt
"Changes saved" confirmation
```

### LinkedIn auth expires (session timeout)
```
User opens web after long absence
Auth token expired
    │
    ▼
Redirect to LinkedIn OAuth re-auth
Re-auth is quick (LinkedIn already logged in)
User lands back on the page they were trying to visit
```

### Voice Inbox sync fails
```
Mobile session complete
Sync to backend fails
    │
    ▼
Retry automatically (up to 3 times)
    │
If all retries fail:
Mobile: "Sync failed — items saved locally. Will retry when connected."
Web: Voice Inbox badge shows stale count with warning icon
    │
On next mobile connection:
Auto-retry sync
Web updates
```

### Resume export fails
```
User clicks [Export PDF]
PDF generation fails (server error)
    │
    ▼
Toast: "Export failed — please try again"
[Retry] button
If repeated failure: "Having trouble? Contact support."
```

### Application submitted but no confirmation
```
User clicks [Send application →] in Application Draft
Network issues — uncertain if submitted
    │
    ▼
Show: "Sending..."
Timeout after 10 seconds
"We're not sure if your application was sent. Check your email for confirmation."
[Mark as sent anyway]  [Try again]
```

---

## Data Integrity

### Prevent duplicate XYZ/STARL
If Voice Inbox sync attempts to add an item that's already in the bank (detected by content similarity):
- Skip duplicate silently
- OR: surface as "Possible duplicate — review" (with diff view)

### Orphaned Voice Inbox items
If an item is routed to XYZ bank but XYZ bank is later cleared:
- Item remains in Voice Inbox history
- Can be re-routed

---

## General Error Principles

1. **Never lose user data** — local buffer, retry logic, graceful degradation
2. **Always explain what happened** — no silent failures
3. **Always offer a path forward** — every error state has an action
4. **Don't block the user** — errors are warnings, not walls (except auth)
5. **Be honest about uncertainty** — "we're not sure" is better than false confirmation
