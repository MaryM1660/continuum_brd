# Today Screen

## Overview

The Today screen is the daily dashboard — the first thing a user sees when they open the web platform. It adapts completely based on the user's **Search Status**.

| Search Status | Mode | Focus |
|---|---|---|
| Preparing | [Preparing mode](#preparing-mode) | Build career capital, track readiness |
| Active | [Active mode](#active-mode) | Manage applications, execute job search |
| Paused | Simplified view | Resume when ready |

The same route `/` renders different layouts. The active target context (Real Plan + Ideal Profile) is always visible in the TopBar.

---

## Preparing Mode

**Goal for the user:** "Build your career capital until you're ready to start applying."

### Layout: 2 columns (~60% + ~40%)

```
┌────────────────────────────────────────────────────────────────────┐
│  LEFT COLUMN (main)                │  RIGHT COLUMN (sidebar)       │
│                                    │                               │
│  A. Vacancies Collected            │  C. Next Best Step           │
│  B. Readiness Checklist            │  D. Next Voice Prompts       │
│                                    │  E. Voice Sync               │
│                                    │  F. Ready to Start (banner)  │
└────────────────────────────────────────────────────────────────────┘
```

---

### A. Vacancies Collected

**Purpose:** Collect raw vacancies (job postings) for classification and Ideal Profile building.

**Visual:** Glass card

**Content:**
- Header: "Vacancies collected" + info icon (tooltip: "Paste job links here to classify and build your Ideal Profile")
- Input bar: text field "Paste job link here and process" + `[+ Add vacancy]` button + `Import saved →` link
- Vacancy table (glass-strong rows):
  - Company avatar (colored circle + letter) + Company name + Role title
  - Match status pill:
    - "Unclassified" (amber border) — not yet analyzed
    - "Classified 82%" (green) — analyzed, match score calculated
  - Action button:
    - [Classify] — for unclassified vacancies
    - [Prepare draft] — for classified vacancies (navigates to Application Draft)
- "5 more →" link at bottom (expands list or navigates to Profiles)

**Mock data (Alex Johnson):**
| Company | Role | Status |
|---|---|---|
| InnovateX | Senior Product Manager | Unclassified |
| NeoBank | Senior PM | Classified 82% |
| TechFin Solutions | Product Manager | Unclassified |
| FinVest Capital | Finvest | Classified 71% |
| + 5 more | | |

---

### B. Readiness Checklist

**Purpose:** Track the 8 items that make up Market Readiness. Shows exactly what's done and what's blocking progress.

**Visual:** Glass card

**Content:**
- Header: "Readiness checklist"
- 8 items, each row:
  - Status icon: ✅ complete (green) | ⚠️ warning (amber) | 📊 partial (with fraction) | ○ incomplete
  - Item label
  - CTA link (navigates to the right screen to fix it)

**Alex Johnson's checklist:**
| # | Label | Status | CTA | Route |
|---|---|---|---|---|
| 1 | Plans calibrated | ✅ complete | Fix plan gaps | /plans |
| 2 | Ideal Profile created | ✅ complete | Create vacancy batch | /profiles |
| 3 | Gap assessment completed | ✅ complete | Self-assess | /gap-assessment |
| 4 | Skill plan created | ✅ complete | Build skill plan | /skill-plan |
| 5 | Resume skeleton ready | ⚠️ warning | Build resume structure | /resume-studio?tab=structure |
| 6 | Resume version created | ○ incomplete | Build resume version | /resume-studio?tab=versions |
| 7 | XYZ achievements coverage | 📊 3.3/8 | Add XYZ | /resume-studio?tab=xyz |
| 8 | STARL stories coverage | 📊 3.8/27 | Add STARL | /resume-studio?tab=starl |

---

### C. Next Best Step Card

**Purpose:** A single, clear recommendation for what to do next to move Market Readiness forward.

**Visual:** Prominent glass card with **amber-glow top border** (accent variant) — visually distinct from other cards.

**Content:**
- Label: "Next best step"
- Task title: "Build resume version for Fintech PM"
- Effect: "+8% readiness · Closes 2 must-haves"
- [▶ Start] button (amber-glow primary style)
- Timestamp: "Updated 2 hours ago"

**Logic:** Determined by the system based on highest-impact incomplete item. For Alex: creating a Fintech-specific resume version is the next step (currently only has generic "PM Resume").

---

### D. Next Voice Prompts

**Purpose:** Gives the user specific questions to discuss in their next mobile coaching session. The coach will ask these, but having them visible on web helps the user prepare.

**Visual:** Glass card

**Content:**
- Header: "Next voice prompts"
- 2–3 prompt strings (e.g., "Tell me about a time you influenced a decision without authority", "What was the most complex product you shipped at DataFlow?")
- [Send to mobile] button — pushes prompts to the mobile app's queue
- [Copy] — copies prompts to clipboard
- [Download checklist] — downloads as PDF/text
- Sync timestamp: "Updated from last session"

---

### E. Voice Sync

**Purpose:** Quick status of the mobile → web data sync.

**Visual:** Small glass card

**Content:**
- "Last voice sync: 2:02 PM yesterday"
- "New items from last call: 5" — clickable → navigates to /voice-inbox

---

### F. Ready to Start Job Search Banner

**Purpose:** Conditional banner — shows when Market Readiness crosses a threshold (e.g., 75%). Prompts user to transition from Preparing to Active.

**Visual:** Full-width glass card with amber-glow border

**Content:**
- Header: "Ready to start job search"
- Gate checklist (3 critical items with ✅/⚠️):
  - Resume version created ✅
  - Gap assessment done ✅
  - Plans calibrated ⚠️
- [→ Start job search] arrow button

**When shown:** Conditional — only when readiness is above threshold AND not already Active.

---

## Active Mode

**Goal for the user:** "Execute your job search efficiently — apply, follow up, prep for interviews."

### Layout: 2 columns (~60% + ~40%)

```
┌────────────────────────────────────────────────────────────────────┐
│  LEFT COLUMN (main)                │  RIGHT COLUMN (sidebar)       │
│                                    │                               │
│  A. Apply Queue                    │  D. Market Readiness Panel   │
│  B. Follow-ups Due                 │  E. Interview Prep Blocks    │
│  C. Next Voice Prompts (compact)   │  F. Calendar Strip           │
│                                    │  G. Voice Sync (compact)     │
└────────────────────────────────────────────────────────────────────┘
```

---

### A. Apply Queue

**Purpose:** Prioritized list of vacancies ready to apply to. The user's daily apply task.

**Visual:** Glass card

**Content:**
- Header: "Apply queue" + sort toggle (by match score / by date added)
- Table rows (4–5 visible):
  - Company avatar + name + role + experience requirement ("5+ years")
  - Match score pill:
    - Green "Match 85%" — strong match, apply now
    - Amber "Needs 68%" — possible, review first
  - Resume version pill (which version is recommended: "PM Resume", "Fintech PM Resume")
  - [Send →] button — marks as applied, moves to Pipeline

**Alex Johnson mock data:**
| Company | Role | Match | Resume | Action |
|---|---|---|---|---|
| Acme Inc. | Product Manager | 85% | PM Resume | [Send →] |
| Continuum Bank | Senior PM | 82% | PM Resume | [Send →] |
| OrbitPay | Product Manager | 68% | PM Resume | [Send →] |
| Volt Financial | Fintech PM | 77% | Fintech PM Resume | [Send →] |

---

### B. Follow-ups Due

**Purpose:** Reminds user which applications need a follow-up today.

**Visual:** Glass card

**Content:**
- Header: "Follow-ups due"
- Items (company/role + due date + action):
  - Acme Inc. · Product Manager — Due today → [Send] | [Open template]
  - Continuum Bank · Senior PM — Due tomorrow → [Send] | [Open template]
  - OrbitPay · Product Manager — Due in 3 days → [Send] | [Open template]

---

### C. Next Voice Prompts (Compact)

Same as Preparing mode but compact: 1–2 prompts + [Send to mobile] button only.

---

### D. Market Readiness Panel

**Purpose:** Quick overview of the search health.

**Visual:** Glass card

**Content:**
- Large: "Market readiness: 62%"
- Stats row:
  - "Active: 14" (applications)
  - "Needs attention: 2" (stuck or overdue)
- Competency check: "✅ STARL competencies" (enough stories to cover common questions)

---

### E. Interview Prep Blocks

**Purpose:** Alert if any upcoming interviews have preparation gaps.

**Visual:** Glass card

**Content:**
- Stage transition info (e.g., "3 applications moving to interview stage")
- Warning card: "Acme Inc. interview in 2 days — STARL coverage: 60%"
- [Fix] button → navigates to Prep Pack for that interview

---

### F. Calendar Strip

**Purpose:** Upcoming scheduled events (interviews, calls) in a compact strip.

**Visual:** Glass card

**Content:**
- "Google Calendar connected" badge (green)
- 2–3 upcoming events:
  - Tomorrow 2pm — Acme Inc. phone screen
  - Thu 10am — Continuum Bank technical interview
- Quick outcome buttons per event: [Proceeded] [Waiting] [Rejected] [Reschedule]

---

### G. Voice Sync (Compact)

Small status line: "New items from last call: 5" → link to /voice-inbox

---

## Mode Toggle

**For demo:** Toggling between Preparing and Active is done via Settings → "Search Status" selector.
**In production:** User explicitly transitions from Preparing to Active (via the Ready to Start banner CTA or Settings). Switching back to Preparing is possible but should require confirmation.

> **Open question:** How to surface the toggle cleanly for demo without making it feel like a dev feature. See [Open Questions](../../open-questions.md).
