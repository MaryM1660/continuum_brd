# Navigation Model

## Mobile — Navigation

### Primary: Side Drawer
The main navigation on mobile is a **Side Drawer** — accessible by swiping from the left edge or tapping a menu icon.

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

**Gesture:** Swipe from left edge (primary) or tap ☰ icon (secondary)
**Active state:** Current screen item highlighted

### Secondary: Screen-Level Navigation
Some screens have internal navigation:
- Talk Screen → Teleprompter (overlay)
- Summaries → Session Detail (drill-down)
- Account → Subscription/Paywall (drill-down)

### Back Navigation
Standard platform back gesture (swipe right on iOS, back button on Android).

---

## Web — Navigation

### Primary: Sidebar (Fixed Left, 240px)

```
┌──────────────────────────────┐
│  [Logo] Continuum            │
│  ──────────────────────────  │
│                              │
│  ● Today              [dot]  │  → /
│    Plans              [1]    │  → /plans
│    Profiles                  │  → /profiles
│    Gap Assessment            │  → /gap-assessment
│    Resume Studio             │  → /resume-studio
│    Pipeline                  │  → /pipeline
│    Voice Inbox        [5]    │  → /voice-inbox
│                              │
│  ──────────────────────────  │
│                              │
│  [A]  Alex Johnson           │
│       Senior PM · Preparing  │
│                              │
│  ⚙️ Settings                 │  → /settings
└──────────────────────────────┘
```

**Active state:** Item has amber-glow left border accent + glass-strong background
**Badge types:**
- Number badge (amber circle): count of items needing attention
- Dot badge (small amber dot): notification, no count

**Sidebar visual:**
- Background: `bg-cosmos-950/80 backdrop-blur-xl`
- Right border: `border-r border-glass-border`
- Nav item text: `text-secondary` (inactive) / `text-primary` (active)

### Secondary: TopBar (Sticky, Full Width)

```
┌──────────────────────────────────────────────────────────────────┐
│ ℹ️ Real plan: Senior PM (3 years) · Ideal: Fintech PM  [Preparing▾] │ [62%] [Pipeline] [⚠ 2] [⚙]
└──────────────────────────────────────────────────────────────────┘
```

**Left section:**
- ℹ️ icon + context string (Real Plan + Ideal Profile)
- Search Status pill (clickable → Target Picker or Settings)

**Right section:**
- "Market readiness: 62%" (with progress indicator)
- [Pipeline] shortcut button → /pipeline
- [Needs attention: N] dropdown → shows items needing action (inline or flyout)
- Settings gear icon → /settings

**TopBar visual:**
- Background: glass (semi-transparent, blurred)
- Sticky: stays at top on scroll
- Responsive: may collapse on smaller viewports

### Tertiary: In-Page Navigation

Some screens have internal navigation:
- **Resume Studio:** Tab bar (Summary | Structure | XYZ | STARL | Versions)
- **Pipeline:** View toggle (List | Kanban) + filter bar
- **Application Detail → Prep Pack:** linked via button

---

## Web — Route Map

| Route | Screen | Access via |
|---|---|---|
| `/` | Today | Sidebar — Today |
| `/plans` | Plans | Sidebar — Plans |
| `/profiles` | Profiles | Sidebar — Profiles |
| `/profiles/:id` | Profile Detail | Profiles → View profile |
| `/gap-assessment` | Gap Assessment | Sidebar — Gap Assessment |
| `/resume-studio` | Resume Studio | Sidebar — Resume Studio |
| `/resume-studio?tab=xyz` | Resume Studio → XYZ tab | Readiness Checklist CTAs |
| `/resume-studio?tab=starl` | Resume Studio → STARL tab | Readiness Checklist CTAs |
| `/resume-studio?tab=versions` | Resume Studio → Versions tab | Readiness Checklist CTAs |
| `/resume-studio?tab=structure` | Resume Studio → Structure tab | Readiness Checklist CTAs |
| `/pipeline` | Pipeline | Sidebar — Pipeline / TopBar |
| `/voice-inbox` | Voice Inbox | Sidebar — Voice Inbox |
| `/application-draft/:id` | Application Draft | Today → [Prepare draft] |
| `/application/:id` | Application Detail | Pipeline row click |
| `/prep-pack/:id` | Prep Pack | Application Detail → [Open Prep Pack] |
| `/target-picker` | Target Picker | TopBar context pill |
| `/skill-plan` | Skill Plan | Gap Assessment → [Build skill plan] |
| `/settings` | Settings | TopBar gear / Sidebar bottom |

---

## Deep Linking

The web platform supports URL-based navigation. Key deep links:
- `/resume-studio?tab=xyz` — opens Resume Studio at XYZ tab
- `/voice-inbox` — opens Voice Inbox (use for "N new items" notifications)
- `/pipeline?filter=needs-attention` — opens Pipeline filtered to stuck items

---

## Mobile ↔ Web Navigation

The Side Drawer on mobile includes "Open web workspace →" which deep-links to the web platform. The web platform shows a prompt on Summaries page to return to mobile if needed.

No shared in-app navigation between platforms — they are separate applications sharing the same backend and auth.
