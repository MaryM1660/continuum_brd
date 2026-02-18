# Resume Studio Screen

**Route:** `/resume-studio`

## Overview

Resume Studio is where the Career Profile data (XYZ achievements, STARL stories) is assembled into actual resume versions. It's the primary output of the Continuum system.

**Tab structure:** Summary | Structure | XYZ | STARL | Versions

---

## Header (Always Visible)

- Title: "Resume Studio"
- Active target context: "Fintech PM · Senior Product Manager"
- Coverage indicators:
  - "Must-have: 72%" — how many must-haves are covered by current XYZ bank
  - "Behavioral: 45%" — how many common behavioral questions can be answered with current STARL bank

---

## Tab: Summary

**Purpose:** Write and refine the professional summary section — the 3–5 line introduction at the top of the resume.

**Content:**
- Summary text editor (glass card, editable textarea)
  - Current text: "Senior Product Manager with 6 years of experience building data-driven products at B2B SaaS companies..."
  - Character count
  - [Save] button
- "Suggested variants" section:
  - 2–3 AI-generated alternative summaries (tailored to different emphases)
  - Each: "Use this" button to replace current
  - Label: e.g., "Fintech-focused variant", "Leadership-focused variant"

---

## Tab: Structure

**Purpose:** Manage the resume structure — work history, role descriptions, organizational skeleton. This is the "bones" before the XYZ bullets.

**Content:**
- List of role entries (glass cards, most recent first):
  - Company + Role title + Dates
  - Completeness bar (how many XYZ bullets filled in for this role)
  - [Edit] button → opens role editing modal
  - Drag to reorder

**Alex Johnson structure:**
| Company | Role | Dates | Completeness |
|---|---|---|---|
| DataFlow | Senior Product Manager | 2022–present | 60% |
| Nexus Inc. | Product Manager | 2019–2022 | 40% |
| StartupCo | Associate PM | 2017–2019 | 20% |

---

## Tab: XYZ

**Purpose:** Manage the XYZ achievement bank — the core content atoms for resume bullets.

**Content:**
- Coverage indicator: "3 of 8 must-haves covered"
- XYZ achievement cards (glass):

```
┌──────────────────────────────────────────────────────────────┐
│  ✦ XYZ Achievement                                           │
│                                                              │
│  "Accomplished reduction in settlement time as measured by   │
│   processing 50K merchant transactions with 40% faster       │
│   clearing by building and shipping payment integration"      │
│                                                              │
│  Competency tags: [fintech] [delivery] [cross-functional]    │
│  Covers must-have: ✅ Fintech/payments domain                │
│  Source: Voice session · Jan 15                              │
│                                                              │
│  [Edit]  [Delete]  [Use in resume]                          │
└──────────────────────────────────────────────────────────────┘
```

**Card fields:**
- Full XYZ text
- Competency tags
- Must-have coverage: which Ideal Profile must-haves this covers
- Source: voice session date, or "manual entry"
- Actions: Edit, Delete, Use in resume (marks for inclusion in active version)

**Alex Johnson XYZ bank:**
4 achievements written. 3 of 8 must-haves covered. Need 5 more for full coverage.

**Bottom:** [+ Add XYZ] button → opens XYZ editor modal
- Fields: Accomplished (X), As measured by (Y), By doing (Z)
- Competency tag selector
- Preview formatted output

---

## Tab: STARL

**Purpose:** Manage the STARL story bank — behavioral interview preparation material.

**Content:**
- Coverage indicator: "5 stories written · 3.8 of 8 target competencies covered"
- STARL story cards (glass):

```
┌──────────────────────────────────────────────────────────────┐
│  📖 Led cross-functional team through platform migration      │
│                                                               │
│  Competency tags: [cross-functional] [stakeholder mgmt]      │
│                   [delivery under pressure]                   │
│                                                               │
│  S: Platform migration at DataFlow serving 200K users        │
│  T: Coordinate 3 engineering teams and 2 business units      │
│  A: Daily standups, shared risk register, weekly exec updates │
│  R: Completed 2 weeks early, zero downtime incidents         │
│  L: Proactive communication > reactive updates               │
│                                                               │
│  Completeness: ████████░░ 80% (Result needs more detail)    │
│                                                               │
│  [Expand]  [Edit]  [Delete]  [Add to prep pack]             │
└──────────────────────────────────────────────────────────────┘
```

**Card fields:**
- Story title
- Competency tags (editable)
- S/T/A/R/L breakdown (collapsed by default, [Expand] to see full)
- Completeness bar (which components are strong vs. thin)
- Source: voice session date or manual
- Actions: Expand, Edit, Delete, Add to prep pack

**Bottom:** [+ Add STARL] button → opens STARL editor
- Fields: Situation, Task, Action, Result, Learning
- Competency tag selector
- Completeness check as user types

---

## Tab: Versions

**Purpose:** Create and manage targeted resume versions — one per Ideal Profile / target.

**Content:**
- List of resume version cards:

```
┌──────────────────────────────────────────────────────────────┐
│  PM Resume                                     [Default]      │
│  Target: General PM                                           │
│                                                               │
│  Must-have coverage: ████████░░ 72%                          │
│  Behavioral coverage: ████░░░░░░ 45%                         │
│                                                               │
│  Last updated: Jan 20, 2025                                   │
│                                                               │
│  [Export PDF]  [Edit]  [Duplicate]                           │
└──────────────────────────────────────────────────────────────┘

┌──────────────────────────────────────────────────────────────┐
│  Fintech PM Resume                             ← Needed!      │
│  (Not yet created)                                            │
│                                                               │
│  [+ Create for Fintech PM target]                            │
└──────────────────────────────────────────────────────────────┘
```

**Alex Johnson versions:**
- "PM Resume" — 72% must-have coverage (exists)
- "Fintech PM Resume" — not yet created (**this is the Next Best Step**)

**Creating a new version:**
1. Select Ideal Profile to target (Fintech PM)
2. System suggests which XYZ achievements to include (by must-have coverage)
3. User reviews and confirms selection
4. System generates draft resume structure
5. User reviews, edits summary, reorders bullets
6. [Export PDF] when ready

**Coverage tracking per version:**
- Must-have coverage %: how many Ideal Profile must-haves are covered by included XYZ bullets
- Behavioral coverage %: how many common behavioral questions can be answered with included STARL stories
- Both displayed as progress bars on the version card
