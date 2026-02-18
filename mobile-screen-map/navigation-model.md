# Mobile Navigation Model

## Primary Navigation: Side Drawer

The main navigation pattern on mobile is a **Side Drawer** — accessible by swiping from the left edge or tapping the ☰ menu icon.

```
┌──────────────────────────┐
│  SIDE DRAWER             │
│  ─────────────────────── │
│  [Avatar]  Alex Johnson  │
│            Senior PM     │
│  ─────────────────────── │
│  🎙 Coach                │ → Talk Screen
│  📋 Summaries            │ → Summaries Screen
│  👤 Account              │ → Account Screen
│  ─────────────────────── │
│  🌐 Open web workspace → │ → browser deep link
│                          │
│  [Sign out]              │
└──────────────────────────┘
```

**Gesture:** Swipe from left edge (primary) | tap ☰ icon (secondary)
**Dismiss:** Swipe right, tap outside drawer, or tap active item
**Active state:** Current screen item highlighted

---

## Secondary: Screen-Level Navigation

Some screens have internal navigation that doesn't use the drawer:

| From | To | Mechanism |
|---|---|---|
| Talk Screen | Teleprompter Panel | Button overlay |
| Talk Screen | Session Summary | End session button |
| Session Summary | Summaries | [View summaries] button |
| Summaries | Session Detail | Tap list item |
| Account Screen | Paywall Screen | [Manage subscription] |

---

## Back Navigation

- **iOS:** Swipe right from left edge (system back gesture)
- **Android:** Hardware/gesture back button

No custom back button needed — use system native behavior.

---

## Home Screen Logic

| User state | Landing screen |
|---|---|
| First launch, not authenticated | Welcome / Splash |
| First launch, just authenticated | Context Setup |
| Returning, has sessions | Welcome Back |
| Returning, session in progress (interrupted) | Talk Screen (with recovery banner) |

---

## Deep Links (Mobile)

| Action | Deep link |
|---|---|
| Open web workspace | Opens browser to web platform URL |
| Start session (from notification) | Opens Talk Screen directly |
| View prep pack (from notification) | Opens browser to web `/prep-pack/:id` |
