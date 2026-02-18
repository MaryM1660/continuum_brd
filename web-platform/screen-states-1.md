# Mobile Screen States

All meaningful states for each mobile screen with visual and behavioral differences.

---

## Global Mobile States

### Authentication State

| State | Screen shown | Behavior |
|---|---|---|
| Not authenticated | Welcome / Splash | [Continue with LinkedIn] is the only action |
| Auth in progress | LinkedIn OAuth (system) | Wait for result |
| Authenticated, first time | Context Setup | One-time onboarding |
| Authenticated, returning | Welcome Back | Normal re-entry |
| Session token expired | Silent re-auth attempt | If fails → LinkedIn OAuth |

### Network State

| State | Indicator | Behavior |
|---|---|---|
| Online | None (normal) | Full functionality |
| Offline | Banner: "No connection" | Session recording continues locally |
| Reconnected | Brief "Back online" toast | Auto-sync pending items |

---

## Talk Screen

The most state-rich screen on mobile — 9 distinct states:

| State | Mic visual | Behavior |
|---|---|---|
| Idle | Static button, "Tap to start" | Tap to begin session |
| Starting | Loading animation | Wait |
| Recording (user speaking) | Pulsing animation + waveform | STT active, coach listening |
| Coach responding | Listening indicator | TTS playing coach response |
| Processing | Spinner on mic | AI processing input |
| Paused | Paused icon, static | Resume / End available |
| Limit approaching | Warning banner: "X min remaining" | Session continues normally |
| Limit reached | Session auto-ends | → Paywall Screen |
| Network lost | Banner: "Saving locally" | Local buffer, auto-sync on reconnect |

---

## Welcome Back Screen

| State | Trigger | Content |
|---|---|---|
| Standard | Normal return (< 14 days) | Last session date + items captured + CTA |
| Long absence | No session in 14+ days | Softer re-engagement message |
| Pre-interview | Interview scheduled in next 24h | Interview highlighted at top, Prep Pack CTA |
| Unsynced items | Web not opened since last session | "N items waiting in your workspace" note |

---

## Session Summary Screen

| State | Trigger | Content |
|---|---|---|
| Items captured | Normal session end | Count by type (XYZ: N, STARL: N, etc.) |
| Nothing captured | Short session or poor audio | "Short session — try again with more detail" |
| Sync complete | Items sent to backend | "Synced to your web workspace ✓" |
| Sync pending | Offline at session end | "Will sync when connected" |
| Paywall triggered | Limit reached during session | Session summary + paywall CTA inline |

---

## Account Screen

| State | Content |
|---|---|
| Free tier | "Free · 1 session included" |
| Subscribed | Plan type + next renewal date + [Manage] |
| Subscription cancelled | "Access continues until [date]" |
| Subscription expired | "Your subscription has expired" + [Renew] CTA |

---

## Paywall Screen

| State | Trigger | Emphasis |
|---|---|---|
| End of free session | Limit reached mid-session | Show items captured (proof of value first) |
| Pre-session gate | Returning after limit | Clean upsell, no session context needed |
| Post-lapse | Subscription expired | Shorter message, focused on renewal |

---

## Side Drawer

| State | Indicator |
|---|---|
| New Voice Inbox items (web) | Badge on "Open web workspace →" |
| Active session in progress | Pulsing dot on Coach item |
| Subscription expired | Warning badge on Account item |
