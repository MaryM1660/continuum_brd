# Overview

## What It Is

The Continuum web platform is a **career management workspace** — the place where all the career capital built through mobile coaching sessions is organized, refined, and deployed into a job search.

If the mobile app is where you talk, the web is where you strategize, build, and track.

***

## Role in the System

| Dimension        | Description                                                      |
| ---------------- | ---------------------------------------------------------------- |
| Primary use case | At-desk, focused career management work                          |
| Session type     | Structured work (building resumes, reviewing pipeline, planning) |
| Data source      | Voice Inbox (from mobile sessions) + user input                  |
| Primary output   | Resume versions, job applications, interview prep                |
| Usage frequency  | Weekly (Preparing phase) to daily (Active phase)                 |

***

## Platform Architecture

```
┌──────────────────────────────────────────────────────────────┐
│  SIDEBAR (240px)     │  TOP BAR (sticky)                     │
│                      │  Context: Real Plan · Ideal Profile   │
│  • Today             │  Market Readiness: 62%                │
│  • Plans             │  [Pipeline] [Needs attention: 2]      │
│  • Profiles          │─────────────────────────────────────  │
│  • Gap Assessment    │                                        │
│  • Resume Studio     │  CONTENT AREA (scrollable)            │
│  • Pipeline          │                                        │
│  • Voice Inbox  (5)  │  [Current page content]               │
│                      │                                        │
│  ──────────────────  │                                        │
│  Alex Johnson        │                                        │
│  Senior PM · Prep.   │                                        │
└──────────────────────────────────────────────────────────────┘
```

***

## Navigation Structure

### Sidebar (Primary Navigation)

| Item           | Route             | Badge                  |
| -------------- | ----------------- | ---------------------- |
| Today          | `/`               | dot (new items)        |
| Plans          | `/plans`          | 1 (calibration needed) |
| Profiles       | `/profiles`       | —                      |
| Gap Assessment | `/gap-assessment` | —                      |
| Resume Studio  | `/resume-studio`  | —                      |
| Pipeline       | `/pipeline`       | —                      |
| Voice Inbox    | `/voice-inbox`    | 5 (new items)          |

Settings accessible via gear icon (bottom of sidebar or TopBar).

### Top Bar (Always Visible)

* **Context pill:** "Real plan: Senior Product Manager (3 years) · Ideal Profile: Fintech PM"
* **Search Status badge:** `[Preparing ▾]` — amber for Preparing, green for Active
* **Market Readiness:** "62%" with arc/bar
* **\[Pipeline]** shortcut button
* **\[Needs attention: 2]** dropdown — shows items requiring user action
* **Settings gear** icon

***

## Screens

| Screen                                                             | Route                    | Phase     | Description                               |
| ------------------------------------------------------------------ | ------------------------ | --------- | ----------------------------------------- |
| [Today (Preparing)](../web-screens-details/today.md)               | `/`                      | Preparing | Vacancies, readiness checklist, next step |
| [Today (Active)](../web-screens-details/today.md)                  | `/`                      | Active    | Apply queue, follow-ups, calendar         |
| [Plans](../web-screens-details/plans.md)                           | `/plans`                 | Both      | 4-plan framework                          |
| [Target Picker](../web-screens-details/target-picker.md)           | `/target-picker`         | Both      | Select active Real Plan + Ideal Profile   |
| [Profiles](../web-screens-details/profiles.md)                     | `/profiles`              | Both      | Ideal Profiles / vacancy batches          |
| [Gap Assessment](../web-screens-details/gap-assessment.md)         | `/gap-assessment`        | Both      | Skills vs Ideal Profile                   |
| [Resume Studio](../web-screens-details/resume-studio.md)           | `/resume-studio`         | Both      | XYZ, STARL, resume versions               |
| [Pipeline](../web-screens-details/pipeline.md)                     | `/pipeline`              | Active    | All applications + tracking               |
| [Voice Inbox](../web-screens-details/voice-inbox.md)               | `/voice-inbox`           | Both      | Items from coaching sessions              |
| [Application Draft](../web-screens-details/application-draft.md)   | `/application-draft/:id` | Active    | Vacancy + cover letter + resume selection |
| [Application Detail](../web-screens-details/application-detail.md) | `/application/:id`       | Active    | Stage timeline, notes, follow-ups         |
| [Prep Pack](../web-screens-details/prep-pack.md)                   | `/prep-pack/:id`         | Active    | Interview prep for specific role          |
| [Skill Plan](../web-screens-details/skill-plan.md)                 | `/skill-plan`            | Preparing | 8-week skill development plan             |
| [Settings](../web-screens-details/settings.md)                     | `/settings`              | Both      | Thresholds, calendar, preferences         |

***

## Design System

Full design system documented at: [Design System](design-system.md)

**Summary:**

* Dark glassmorphism theme
* Base color: `#0a0612` (cosmos-900)
* Accent: amber-glow (`#e8933a`)
* Glass cards with backdrop-filter blur
* Inter font
* Framer Motion page transitions (fade + y-shift)

***

## Key UX Patterns

### Glass Cards

All content is presented in glass-effect cards — semi-transparent, blurred background. Provides depth and visual hierarchy on the dark background.

### Context Awareness

The TopBar always shows the active target context. The user always knows what they're optimizing for.

### Progressive Disclosure

Screens show the most important information first (e.g., Next Best Step at top of Today sidebar). Detailed views accessible via navigation.

### Market Readiness as North Star

The 62% score is always visible. Every action on the platform should visibly move this number.

### Demo Mode

For the PoC/demo, all data is mocked with the Alex Johnson persona. The Preparing/Active mode can be toggled (likely via Settings). The readiness score, pipeline, voice inbox items — all hardcoded to tell a consistent story.
