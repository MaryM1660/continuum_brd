# Pipeline Screen

**Route:** `/pipeline`

## Overview

The Pipeline is the application tracking system — all active job applications in one place, with stage tracking, attention flags, and navigation to individual application details.

---

## Header

- Title: "Pipeline"
- Stats row:
  - Active: 14
  - Stage 3: 5 (Applied)
  - Interviews: 3
  - Offers: 0

---

## Filter Bar

```
[Active target ▾] [Stage ▾] [⚠ Needs attention] [List ≡] [Kanban ⊞]
```

- **Active target dropdown:** Filter by which target the application is for
- **Stage filter:** Filter to specific stage(s)
- **Needs attention toggle:** Show only applications that are stuck or have overdue follow-ups
- **View toggle:** List view (default) or Kanban view

---

## List View (Default)

Glass-background table. Columns:

| Column | Description |
|---|---|
| Company | Avatar + company name |
| Role | Role title |
| Stage | Stage pill (color-coded) |
| Match | Match score pill |
| Resume | Which resume version used |
| Last Update | Days since last activity |
| Next Action | What needs to happen |
| Status | Normal / Needs attention / Stuck |

**Stage colors:**
- Stage 1–2 (Discovered/Saved): muted
- Stage 3 (Applied): info blue
- Stage 4–5 (Screening/Interview): success green
- Stage 6–7 (Round 2+/Offer): amber
- Stage 8 (Closed): danger red (rejected) or success (accepted)

**Stuck flag:** "⚠ Stuck 12 days" in danger/amber when no update for > threshold days (threshold configurable in Settings, default 7 days)

**Alex Johnson mock data:**

| Company | Role | Stage | Match | Resume | Last Update | Status |
|---|---|---|---|---|---|---|
| Acme Inc. | Product Manager | 3 – Applied | 85% | PM Resume | 2 days | Normal |
| Continuum Bank | Senior PM | 3 – Applied | 82% | PM Resume | 1 day | Normal |
| OrbitPay | Product Manager | 5 – Interview | 68% | PM Resume | 12 days | ⚠ Stuck |
| Volt Financial | Fintech PM | 3 – Applied | 77% | Fintech PM Resume | 3 days | Normal |
| NeoBank | Senior PM | 4 – Screening | 82% | PM Resume | 5 days | Normal |
| FinVest Capital | Fintech PM | 3 – Applied | 71% | PM Resume | 8 days | ⚠ Needs attention |
| InnovateX | Senior PM | 2 – Saved | 79% | — | — | — |
| ... | ... | ... | ... | ... | ... | ... |

(14 total active applications)

---

## Row Actions

Clicking a row navigates to [Application Detail](application-detail.md) (`/application/:id`).

Right-click or swipe reveals quick actions:
- [Update stage] → stage increment buttons
- [Log follow-up]
- [Archive] (move to closed)

---

## Kanban View

Alternative view — columns = stages, cards draggable between columns.

Each card:
- Company + role (compact)
- Match score badge
- Days in stage indicator
- Stuck badge if overdue

**Note:** Kanban view is a nice-to-have; list view is the primary and must be implemented first.

---

## Needs Attention Logic

An application "needs attention" when any of these are true:
- Stuck in same stage > N days (N = stuck threshold from Settings, default 7)
- Follow-up scheduled for today or overdue
- Interview scheduled in next 24h without Prep Pack opened
- Stage changed to "Rejected" without being acknowledged

The TopBar always shows total needs-attention count: "Needs attention: 2"
