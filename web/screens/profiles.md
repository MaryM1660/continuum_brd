# Profiles Screen (Ideal Profiles / Vacancy Batches)

**Route:** `/profiles`

## Overview

The Profiles screen manages **Ideal Profiles** — data-driven models of what target roles require. Each profile is built from a batch of real job vacancies.

This is the "market intelligence" section: instead of guessing what fintech PMs need, the user analyzes real postings and gets a ranked list of must-haves with frequency data.

---

## Layout

**Header:**
- Title: "Profiles"
- Subtitle: "Build Ideal Profiles from real job postings to understand exactly what the market wants."
- [+ Create new batch] button (top right, primary)

**Body:** List of Ideal Profile cards (glass)

---

## Profile Card

Each profile card shows:

```
┌──────────────────────────────────────────────────────────────┐
│  [FP]  Fintech PM                          ● Selected target  │
│        Based on 10 vacancies                                  │
│                                                               │
│  Must-haves: 6  |  Coverage: 72%  |  Top gap: Regulatory     │
│                                                               │
│  [View profile]  [Edit batch]  [Create resume version]        │
└──────────────────────────────────────────────────────────────┘
```

**Fields:**
- Avatar (initials, colored)
- Profile name
- "Selected target" badge (amber) if this is the active Ideal Profile
- "Based on N vacancies"
- Summary stats: Must-haves count | Coverage % | Top gap skill
- Actions:
  - [View profile] → Ideal Profile detail view
  - [Edit batch] → Add/remove vacancies from the batch
  - [Create resume version] → navigates to Resume Studio → Versions tab with this profile pre-selected

---

## Alex Johnson mock data

| Profile | Vacancies | Must-haves | Coverage | Top Gap |
|---|---|---|---|---|
| Fintech PM ● | 10 | 6 | 72% | Regulatory compliance |
| B2B SaaS PM | — | — | — | (not built yet) |
| EdTech PM | — | — | — | (not built yet) |
| Travel Tech PM | — | — | — | (not built yet) |

---

## Profile Detail View

Clicking [View profile] opens an inline detail view or sub-route (`/profiles/:id`):

**Content:**
- Profile name + vacancy count
- **Must-haves list** (ranked by frequency):
  1. Product management 5+ years — 10/10 postings (100%)
  2. Cross-functional leadership — 8/10 (80%)
  3. Data-driven decision making — 7/10 (70%)
  4. Fintech/payments domain — 7/10 (70%)
  5. Stakeholder management C-level — 6/10 (60%)
  6. Regulatory compliance — 5/10 (50%)
- **Nice-to-haves:** Python/SQL, API design, Agile certification
- **Coverage against user's Career Profile:**
  - Each must-have: covered ✅ | weak ⚠️ | missing ○
  - Overall: 72%
- [Build skill plan for gaps] → /skill-plan
- [Go to Gap Assessment] → /gap-assessment

---

## Creating a New Ideal Profile

Clicking [+ Create new batch]:

1. Name the profile (text field: "Fintech PM", "Engineering Manager", etc.)
2. Paste vacancy links (multi-line input)
3. Or: import from saved (if integration exists — post-MVP)
4. [Analyze batch] → system processes vacancies, extracts must-haves
5. Review extracted must-haves, edit if needed
6. [Save profile]

> **MVP note:** Analysis may be manual/prompted (user pastes job descriptions rather than URLs if scraping is complex).
