# Web Screen Hierarchy

Full inventory of all screens in the Continuum web platform.

---

## Screen Tree

```
WEB PLATFORM
│
├── Auth
│   └── LinkedIn OAuth (system — shared with mobile)
│
├── Shell (persistent on all screens)
│   ├── Sidebar (240px, fixed left)
│   │   ├── Navigation items (Today, Plans, Profiles, Gap Assessment,
│   │   │   Resume Studio, Pipeline, Voice Inbox)
│   │   └── User section (avatar, name, status, Settings link)
│   └── TopBar (sticky, full width above content)
│       ├── Context pill (Real Plan · Ideal Profile · Search Status)
│       ├── Market Readiness indicator
│       ├── [Pipeline] shortcut
│       ├── [Needs attention: N] dropdown
│       └── Settings gear
│
├── Primary Navigation (Sidebar links)
│   ├── Today (/)
│   │   ├── Preparing Mode
│   │   │   ├── Vacancies Collected module
│   │   │   ├── Readiness Checklist
│   │   │   ├── Next Best Step card (accent border)
│   │   │   ├── Next Voice Prompts
│   │   │   ├── Voice Sync card
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
│   │       ├── Must-haves list with frequency
│   │       ├── Coverage vs Career Profile
│   │       └── Vacancy Batch editor
│   │
│   ├── Gap Assessment (/gap-assessment)
│   │   ├── Skill cluster matrix
│   │   └── Top gaps summary + CTA
│   │
│   ├── Resume Studio (/resume-studio)
│   │   ├── Tab: Summary (editable + AI variants)
│   │   ├── Tab: Structure (role entries)
│   │   ├── Tab: XYZ (achievement bank)
│   │   │   └── XYZ Editor modal
│   │   ├── Tab: STARL (story bank)
│   │   │   └── STARL Editor modal
│   │   └── Tab: Versions (resume versions list)
│   │       └── Version detail / editor
│   │
│   ├── Pipeline (/pipeline)
│   │   ├── List view (default)
│   │   └── Kanban view (toggle)
│   │
│   └── Voice Inbox (/voice-inbox)
│       └── Item inline expand
│
├── Secondary Screens (from Pipeline / Today)
│   ├── Application Draft (/application-draft/:id)
│   ├── Application Detail (/application/:id)
│   │   └── Stage Update modal
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

---

## Screen Inventory

### Primary (Sidebar Navigation)

| Screen | Route | Notes |
|---|---|---|
| Today — Preparing | `/` | Shown when searchStatus = preparing |
| Today — Active | `/` | Shown when searchStatus = active |
| Plans | `/plans` | 4-plan framework |
| Profiles | `/profiles` | Ideal Profile list |
| Profile Detail | `/profiles/:id` | Must-haves, vacancy batch |
| Gap Assessment | `/gap-assessment` | Skill matrix |
| Resume Studio | `/resume-studio` | 5-tab content builder |
| Pipeline | `/pipeline` | Application tracker |
| Voice Inbox | `/voice-inbox` | Coaching session output |

### Secondary (Deep Navigation)

| Screen | Route | Entry point |
|---|---|---|
| Application Draft | `/application-draft/:id` | Today → [Prepare draft] |
| Application Detail | `/application/:id` | Pipeline row |
| Prep Pack | `/prep-pack/:id` | Application Detail |

### Utility

| Screen | Route | Entry point |
|---|---|---|
| Target Picker | `/target-picker` | TopBar context pill |
| Skill Plan | `/skill-plan` | Gap Assessment CTA |
| Settings | `/settings` | TopBar gear / Sidebar |

**Total: 15 distinct screens + 6 modals**
