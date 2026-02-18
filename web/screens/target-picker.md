# Target Picker Screen

**Route:** `/target-picker`

## Overview

The Target Picker is where the user selects their active **Target** — the combination of a Real Plan and an Ideal Profile that drives all calculations, recommendations, and filtering across the web platform.

Think of it as "currently I'm optimizing for [this career direction] targeting [this specific role type]."

---

## When It's Used

- First time setup (after creating Real Plans and Ideal Profiles)
- When user wants to switch focus (e.g., shift from targeting "Fintech PM" to "B2B SaaS PM")
- Accessible via: TopBar context pill → click → opens Target Picker

---

## Layout

**Centered 2-column layout:**

```
┌─────────────────────────────────────┬──────────────────────────────────────┐
│  SELECT REAL PLAN                   │  SELECT IDEAL PROFILE                │
│  "What career direction are         │  "What type of role are you          │
│   you pursuing?"                    │   targeting?"                        │
│                                     │                                       │
│  [Real Plan cards list]             │  [Ideal Profile cards list]          │
│                                     │                                       │
│  + Create new real plan             │  + Create new ideal profile          │
└─────────────────────────────────────┴──────────────────────────────────────┘

                    [Set active target]  ← full-width amber-glow button
```

---

## Left Column: Select Real Plan

**Header:** "Select Real Plan"
**Subtext:** "Choose which career direction you're currently optimizing for"

**Plan cards (glass):**
Each card shows:
- Avatar circle (initial letter of plan name, colored)
- Plan name
- Horizon (e.g., "3 years")
- Selected state: amber-glow border + checkmark

**Alex Johnson mock data:**

| Initial | Plan Name | Horizon |
|---|---|---|
| A | Senior Product Manager | 3 years |
| T | Tech Lead | 2 years |
| S | Startup Founder | 5+ years |
| C | Corporate Strategy Director | 4 years |

**Selected:** Senior Product Manager (amber-glow border)

**Bottom link:** "+ Create new real plan" → navigates to Plans screen

---

## Right Column: Select Ideal Profile

**Header:** "Select Ideal Profile"
**Subtext:** "Choose which role type's requirements you're preparing against"

**Profile cards (glass):**
Each card shows:
- Avatar circle (initials)
- Profile name (e.g., "Fintech PM")
- Based on N vacancies
- Resume draft info: "Draft: PM Resume" or "No draft yet"
- [Edit] button (navigates to Profiles screen)
- [→] button (navigates to Profile detail)
- Selected state: checkmark icon + amber-glow border

**Alex Johnson mock data:**

| Profile | Based On | Draft Resume | Status |
|---|---|---|---|
| Fintech PM | 10 vacancies | — (no draft) | Selected ✓ |
| B2B SaaS PM | — | PM Resume | — |
| EdTech PM | — | Fintech PM Resume | — |
| Travel Tech PM | — | Fintech PM Resume | — |

**Selected:** Fintech PM (amber-glow border + checkmark)

**Bottom link:** "+ Create new ideal profile" → navigates to Profiles screen

---

## Bottom CTA

**[Set active target]** — full-width amber-glow button

On click:
- Saves the selected Real Plan + Ideal Profile combination as the active target
- Updates TopBar context pill: "Senior Product Manager (3 years) · Fintech PM"
- Recalculates Market Readiness score against the new target
- Returns user to previous screen (or Today)
- Toast: "Target updated — optimizing for Fintech PM"
