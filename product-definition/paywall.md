# Paywall

## Overview

The paywall is the monetization gate in the mobile app. It triggers after the free tier limit is reached. The design must:
1. Feel earned, not punishing
2. Demonstrate value (user has already gotten something useful)
3. Convert efficiently
4. Not destroy trust

**Status:** Core mechanism is decided (paywall exists after free use), but critical design details are open questions. This document captures what's known and frames the open questions for a dedicated design session.

---

## What We Know

| Decision | Status | Detail |
|---|---|---|
| Paywall exists | Decided | Free → Paid after some usage |
| Trigger: sessions | Decided direction | "After 1 session" — exact definition TBD |
| Trigger: time | Decided direction | "After 30 minutes" — exact definition TBD |
| Both triggers apply | Unclear | Are these AND or OR? |
| Free tier beyond first session | Open | Is it strictly 1 session, or is there some residual free access? |
| Pricing | Open | Monthly / annual / one-time — TBD |
| In-session behavior | Open | What happens when limit is hit mid-conversation? |

---

## Trigger Options

### Option A: Session-count based
User gets N full sessions free. After that, paywall on next session start.

**Pros:** Simple, predictable, user knows what they get
**Cons:** Sessions vary in length (5 min vs 30 min) — feels arbitrary

### Option B: Time-based
User gets N minutes of total talk time. Counter runs across all sessions.

**Pros:** More fair (reflects actual product usage)
**Cons:** Feels like a metered utility — psychological friction

### Option C: Hybrid (likely)
"1 free session" where a session = until the session naturally ends (user taps stop, or time limit per session). After that first session, paywall on next start.

**Most likely approach based on stated "1 session or 30 minutes":**
- Free: 1 session, max 30 minutes
- If session exceeds 30 minutes: paywall triggered at the 30-minute mark within that session

---

## In-Session Paywall Experience

> **Open question — critical to design.** How the paywall is surfaced mid-session determines user trust and conversion.

### Candidate Option 1: Hard cut
At 30 minutes, session abruptly ends. Paywall screen appears.

**Assessment:** Poor UX. Feels punishing. Will create negative emotions. Not recommended.

### Candidate Option 2: Warning + graceful finish
At 25 minutes, a subtle warning appears ("5 minutes remaining in your free session").
At 30 minutes, coach delivers a natural closing:
> "That's a great place to pause. I'd love to continue this with you — we covered a lot today. Let me walk you through your options for keeping the momentum going."
Then paywall screen appears.

**Assessment:** Best UX. Respectful. Coach's voice makes it feel like a natural part of the experience, not a product interruption.

### Candidate Option 3: End-of-session gate
First session completes normally (no mid-session interruption).
When user tries to start a second session, paywall appears.

**Assessment:** Cleaner, but user has to wait until they want a second session to hit the gate. Less urgency. Could lead to churn (user doesn't come back for second session).

### Recommendation (pending decision)
**Option 2 is recommended:** Warning at -5 min, graceful coach close at limit, then paywall. Ensures the first session always completes cleanly and creates a natural emotional hook for conversion.

---

## Paywall Screen Design

**Triggered:** After free limit reached (mid-session or pre-session)

**Content:**
```
┌─────────────────────────────────────────────────────────────┐
│                                                              │
│  [Coach avatar]                                             │
│                                                              │
│  "You've made great progress today."                        │
│                                                              │
│  In this session, we captured:                              │
│  ✦ 2 XYZ achievements                                      │
│  ✦ 1 STARL story                                           │
│  ✦ 1 plan insight                                           │
│                                                              │
│  Ready to keep building?                                    │
│                                                              │
│  ┌──────────────────────┐  ┌──────────────────────┐        │
│  │  Monthly             │  │  Annual (Save 40%)   │        │
│  │  $X/month           │  │  $Y/year             │        │
│  └──────────────────────┘  └──────────────────────┘        │
│                                                              │
│  [Subscribe →]  amber-glow button                          │
│                                                              │
│  [Not now — remind me later]  (text link, not prominent)   │
│                                                              │
│  No commitment. Cancel anytime.                             │
└─────────────────────────────────────────────────────────────┘
```

**Key design decisions:**
- Show what was captured (proof of value) before asking for money
- Coach avatar/voice present (continuity of experience)
- Not a dead end — "Not now" is available but de-emphasized
- Social proof / reassurance: "No commitment. Cancel anytime."

---

## Web Paywall

> **Open question:** Does the web platform have its own paywall gate, or does it rely entirely on mobile subscription?

**Hypothesis:** Web platform access is gated behind mobile subscription. You can't use the web without subscribing. LinkedIn auth creates the account; subscription unlocks full access.

**Alternative:** Web has a separate limited free tier (e.g., view-only, limited resume exports) that's unlocked by subscription.

---

## Post-Paywall State

After subscribing:
- Mobile: Return to session (or continue in new session)
- Web: Full access to all screens
- Account screen shows: subscription type + renewal date

If subscription lapses:
- Mobile: Can still view Session Summaries and Account (read-only)
- Can't start new sessions
- Web: Read-only access to Career Profile (can't add/edit XYZ, STARL, etc.)

---

## Open Questions Summary

| Question | Priority | Notes |
|---|---|---|
| Paywall trigger: session count vs. time | HIGH | "1 session or 30 min" — reconcile these |
| In-session experience (Option 1/2/3) | HIGH | Recommend Option 2, needs decision |
| Free tier: what's available after paywall? | HIGH | Summaries read-only? Nothing? |
| Pricing: monthly/annual amounts | HIGH | Needs business decision |
| Web paywall: separate or shared with mobile? | MEDIUM | Affects web onboarding design |
| Subscription platform: App Store / Stripe / both | MEDIUM | Affects implementation |
| Trial period: 7-day free trial instead of free session? | MEDIUM | Alternative monetization model |

**Future session topic:** `paywall-design`
