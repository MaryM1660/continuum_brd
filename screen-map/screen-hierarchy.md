# Screen Hierarchy

Full inventory of all screens across both platforms.

---

## Mobile App

```
MOBILE
│
├── Auth
│   ├── Welcome / Splash
│   ├── LinkedIn OAuth (system)
│   └── Context Setup (post-auth, first time only)
│
├── Core
│   ├── Welcome Back (returning user home)
│   ├── Talk Screen (active coaching session)
│   │   └── Teleprompter Panel (overlay)
│   └── Session Summary (post-session)
│
├── History
│   └── Summaries Screen (past sessions list)
│       └── Session Detail (individual session items)
│
├── Account
│   └── Account Screen (profile, subscription, settings)
│       └── Subscription / Paywall Screen
│
└── Navigation
    └── Side Drawer (nav overlay)
```

**Total mobile screens: 10**

---

## Web Platform

```
WEB
│
├── Auth
│   └── LinkedIn OAuth (system)
│
├── Shell (present on all screens)
│   ├── Sidebar (primary navigation)
│   └── TopBar (context + readiness + shortcuts)
│
├── Primary Navigation
│   │
│   ├── Today (/)
│   │   ├── Preparing Mode
│   │   │   ├── Vacancies Collected module
│   │   │   ├── Readiness Checklist
│   │   │   ├── Next Best Step card
│   │   │   ├── Next Voice Prompts
│   │   │   ├── Voice Sync
│   │   │   └── Ready to Start banner (conditional)
│   │   └── Active Mode
│   │       ├── Apply Queue
│   │       ├── Follow-ups Due
│   │       ├── Next Voice Prompts (compact)
│   │       ├── Market Readiness Panel
│   │       ├── Interview Prep Blocks
│   │       ├── Calendar Strip
│   │       └── Voice Sync (compact)
│   │
│   ├── Plans (/plans)
│   │   ├── Ideal Plan card
│   │   ├── Real Plan card
│   │   ├── Compromise Plan card
│   │   └── Anti-Plan card
│   │
│   ├── Profiles (/profiles)
│   │   ├── Ideal Profile list
│   │   └── Profile Detail (/profiles/:id)
│   │       ├── Must-haves list (with frequency)
│   │       ├── Coverage vs Career Profile
│   │       └── Vacancy Batch editor
│   │
│   ├── Gap Assessment (/gap-assessment)
│   │   ├── Skill cluster matrix
│   │   └── Top gaps summary
│   │
│   ├── Resume Studio (/resume-studio)
│   │   ├── Tab: Summary
│   │   ├── Tab: Structure
│   │   ├── Tab: XYZ
│   │   │   └── XYZ Editor (modal)
│   │   ├── Tab: STARL
│   │   │   └── STARL Editor (modal)
│   │   └── Tab: Versions
│   │       └── Version Detail (modal or sub-view)
│   │
│   ├── Pipeline (/pipeline)
│   │   ├── List view
│   │   └── Kanban view
│   │
│   └── Voice Inbox (/voice-inbox)
│       └── Item detail (inline expand)
│
├── Secondary Navigation (accessible from pipeline / today)
│   │
│   ├── Application Draft (/application-draft/:id)
│   │
│   ├── Application Detail (/application/:id)
│   │   └── Stage Update modal
│   │
│   └── Prep Pack (/prep-pack/:id)
│
├── Utility Screens
│   ├── Target Picker (/target-picker)
│   ├── Skill Plan (/skill-plan)
│   └── Settings (/settings)
│
└── Modals (overlay, no dedicated route)
    ├── Resume Preview
    ├── Plan Calibration editor
    ├── Stage Update
    ├── XYZ editor
    ├── STARL editor
    └── Confirm (destructive actions)
```

**Total web screens: 14 main + 6 modals**

---

## Summary Table

### Mobile
| Screen | Type | First seen |
|---|---|---|
| Welcome / Splash | Auth | First launch |
| LinkedIn OAuth | Auth (system) | First launch |
| Context Setup | Onboarding | Post-auth (once) |
| Welcome Back | Home | Every return |
| Talk Screen | Core | Every session |
| Teleprompter Panel | Overlay | During session |
| Session Summary | Post-session | After session |
| Summaries | History | Via drawer |
| Session Detail | History | Via summaries |
| Account Screen | Settings | Via drawer |
| Paywall Screen | Monetization | Limit reached |
| Side Drawer | Navigation | Anytime |

### Web
| Screen | Route | Section |
|---|---|---|
| Today (Preparing) | `/` | Primary |
| Today (Active) | `/` | Primary |
| Plans | `/plans` | Primary |
| Profiles | `/profiles` | Primary |
| Profile Detail | `/profiles/:id` | Primary |
| Gap Assessment | `/gap-assessment` | Primary |
| Resume Studio | `/resume-studio` | Primary |
| Pipeline | `/pipeline` | Primary |
| Voice Inbox | `/voice-inbox` | Primary |
| Application Draft | `/application-draft/:id` | Secondary |
| Application Detail | `/application/:id` | Secondary |
| Prep Pack | `/prep-pack/:id` | Secondary |
| Target Picker | `/target-picker` | Utility |
| Skill Plan | `/skill-plan` | Utility |
| Settings | `/settings` | Utility |
