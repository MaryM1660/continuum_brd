# Mobile Screen Hierarchy

Full inventory of all screens in the Continuum mobile app.

---

## Screen Tree

```
MOBILE APP
│
├── Auth
│   ├── Welcome / Splash
│   │   └── [Continue with LinkedIn] → LinkedIn OAuth
│   ├── LinkedIn OAuth (system browser / in-app)
│   └── Context Setup (post-auth, first time only)
│       └── [Start my first session →] → Talk Screen
│
├── Core — Session
│   ├── Welcome Back (returning user home screen)
│   │   ├── [▶ Start session] → Talk Screen
│   │   └── [View summaries] → Summaries
│   ├── Talk Screen (active coaching session)
│   │   ├── Teleprompter Panel (overlay, toggle during session)
│   │   └── [End session] → Session Summary
│   └── Session Summary (post-session recap)
│       ├── [View summaries] → Summaries
│       └── [Done] → Welcome Back
│
├── History
│   └── Summaries Screen (all past sessions)
│       └── Session Detail (single session expanded view)
│
├── Account & Settings
│   └── Account Screen
│       └── Subscription / Paywall Screen
│
└── Navigation
    └── Side Drawer (overlay, swipe from left or ☰ tap)
        ├── → Talk Screen
        ├── → Summaries
        ├── → Account Screen
        └── → Open web workspace (browser deep link)
```

---

## Screen Inventory

| Screen | Type | Entry Point | First Shown |
|---|---|---|---|
| Welcome / Splash | Auth | App launch | First launch only |
| LinkedIn OAuth | Auth (system) | Welcome screen | First launch only |
| Context Setup | Onboarding | Post-auth | First launch only (once) |
| Welcome Back | Home | App launch (returning) | After first session |
| Talk Screen | Core | Welcome Back / Drawer | Every session |
| Teleprompter Panel | Overlay | Talk Screen button | During session |
| Session Summary | Post-session | Talk Screen end | After every session |
| Summaries | History | Drawer / Session Summary | Any time |
| Session Detail | History drill-down | Summaries list | On tap |
| Account Screen | Settings | Side Drawer | Any time |
| Paywall Screen | Monetization | Free limit reached | When limit hit |
| Side Drawer | Navigation overlay | Swipe / ☰ icon | Any time |

**Total: 12 screens** (including overlays and drawer)

---

## Depth Map

| Level | Screens |
|---|---|
| L0 — Entry | Welcome, LinkedIn OAuth |
| L1 — Home | Welcome Back |
| L2 — Core | Talk Screen, Summaries, Account Screen |
| L3 — Overlays & drill-down | Teleprompter Panel, Session Detail, Paywall Screen |
| L2 — Post-session | Session Summary |
