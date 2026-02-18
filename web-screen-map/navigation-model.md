# Web Navigation Model

## Primary: Sidebar (Fixed Left, 240px)

The main navigation on web is a persistent sidebar, always visible on the left.

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

**Visual:**
- Background: `bg-cosmos-950/80 backdrop-blur-xl`
- Right border: `border-r border-glass-border`
- Width: 240px, fixed (not collapsible in MVP)

**Active state:**
- Left border accent: `border-l-2 border-amber-glow`
- Background: `bg-glass-strong`
- Text: full opacity (`text-primary`)
- Inactive: `text-secondary`

**Badge types:**
- Amber number circle: count of items requiring attention
- Small amber dot: notification present (no count)

---

## Secondary: TopBar (Sticky, Full Width)

Always visible above the content area. Shows active target context + key metrics.

```
┌──────────────────────────────────────────────────────────────────────┐
│  ℹ️  Real plan: Senior PM (3y)  ·  Ideal: Fintech PM  [Preparing ▾]  │  62% ████░  [Pipeline]  [⚠ 2]  ⚙
└──────────────────────────────────────────────────────────────────────┘
```

**Left section:**
- ℹ️ icon + context string: "Real plan: [name] (horizon) · Ideal: [profile name]"
- Search Status pill (clickable → Target Picker): amber border = Preparing, green = Active

**Right section:**
- Market Readiness: "62%" + thin progress bar
- [Pipeline] button → /pipeline
- [Needs attention: N] → dropdown or flyout with flagged items
- ⚙ gear → /settings

**Visual:**
- Glass background (semi-transparent, blurred)
- Sticky: stays at top while content scrolls below
- Height: ~56px

---

## Tertiary: In-Page Tab Navigation

Some screens have internal tab navigation:

| Screen | Tabs |
|---|---|
| Resume Studio | Summary · Structure · XYZ · STARL · Versions |

Tab bar: glass background, animated active indicator (sliding underline).

---

## In-Page View Toggles

| Screen | Toggle |
|---|---|
| Pipeline | List view ≡ ↔ Kanban ⊞ |

---

## Route Map

| Route | Screen | Accessed via |
|---|---|---|
| `/` | Today | Sidebar — Today |
| `/plans` | Plans | Sidebar — Plans |
| `/profiles` | Profiles | Sidebar — Profiles |
| `/profiles/:id` | Profile Detail | Profiles → View profile |
| `/gap-assessment` | Gap Assessment | Sidebar — Gap Assessment |
| `/resume-studio` | Resume Studio | Sidebar — Resume Studio |
| `/resume-studio?tab=summary` | Resume Studio → Summary | Direct link |
| `/resume-studio?tab=structure` | Resume Studio → Structure | Readiness Checklist CTA |
| `/resume-studio?tab=xyz` | Resume Studio → XYZ | Readiness Checklist CTA |
| `/resume-studio?tab=starl` | Resume Studio → STARL | Readiness Checklist CTA |
| `/resume-studio?tab=versions` | Resume Studio → Versions | Readiness Checklist CTA |
| `/pipeline` | Pipeline | Sidebar / TopBar button |
| `/voice-inbox` | Voice Inbox | Sidebar — Voice Inbox |
| `/application-draft/:id` | Application Draft | Today → [Prepare draft] |
| `/application/:id` | Application Detail | Pipeline row click |
| `/prep-pack/:id` | Prep Pack | Application Detail → [Open Prep Pack] |
| `/target-picker` | Target Picker | TopBar context pill |
| `/skill-plan` | Skill Plan | Gap Assessment → [Build skill plan] |
| `/settings` | Settings | TopBar gear / Sidebar bottom |

---

## Deep Links

Key URL patterns used in notifications and cross-platform links:

| Purpose | URL |
|---|---|
| Open Voice Inbox (from push) | `/voice-inbox` |
| Open specific application | `/application/:id` |
| Open pipeline (attention filter) | `/pipeline?filter=needs-attention` |
| Open Resume Studio at XYZ | `/resume-studio?tab=xyz` |
| Open specific prep pack | `/prep-pack/:id` |
