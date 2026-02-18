# Gap Assessment Screen

**Route:** `/gap-assessment`

## Overview

The Gap Assessment shows exactly how the user's skills compare to what their target role requires. It turns the abstract question "am I qualified?" into a structured, visual answer.

Input: Ideal Profile must-haves (from Profiles screen) + user's self-assessment.
Output: Clear gap map showing what to work on before applying.

---

## Layout

**Header:**
- Title: "Gap Assessment"
- Context: "Fintech PM · Senior Product Manager" (active target)
- Subtitle: "How your skills match up against the Fintech PM must-haves"

**Body:**
- Skill cluster matrix (glass cards, 2–3 column responsive grid)
- Each must-have from the Ideal Profile = one card
- [Build skill plan →] CTA at bottom (navigates to /skill-plan)

---

## Skill Card

Each skill from the Ideal Profile gets a card:

```
┌──────────────────────────────────────────────┐
│  Product management 5+ years                 │
│  Frequency: 10/10 postings ████████████ 100% │
│                                               │
│  Your level:  ● ● ● ● ○  (4/5)              │
│                                               │
│  Evidence:                                    │
│  "6 years total PM experience, 3 at DataFlow" │
│                                               │
│  Status: ✅ Strong                            │
└──────────────────────────────────────────────┘
```

**Card fields:**
- Skill name
- Frequency bar (how many postings mention this skill / total)
- Self-assessment: 1–5 dots or stars (editable by user)
- Evidence: text from Career Profile or from skill evidence captured in coaching
- Status: Strong (4–5) | Adequate (3) | Weak (1–2) | Missing (0)
- [Add evidence] link → opens modal or navigates to voice prompts

---

## Status Colors

| Rating | Dots | Status | Color |
|---|---|---|---|
| 4–5 / 5 | ● ● ● ● ● or ● ● ● ● ○ | Strong | Success green |
| 3 / 5 | ● ● ● ○ ○ | Adequate | Info blue |
| 1–2 / 5 | ● ● ○ ○ ○ or ● ○ ○ ○ ○ | Weak | Warning amber |
| 0 | ○ ○ ○ ○ ○ | Missing | Danger red |

---

## Alex Johnson Assessment

| Skill | Frequency | Alex's Level | Status |
|---|---|---|---|
| Product management 5+ years | 10/10 | 4/5 | ✅ Strong |
| Cross-functional leadership | 8/10 | 4/5 | ✅ Strong |
| Data-driven decision making | 7/10 | 5/5 | ✅ Strong |
| Fintech/payments domain | 7/10 | 3/5 | ○ Adequate |
| Stakeholder management C-level | 6/10 | 4/5 | ✅ Strong |
| Regulatory compliance | 5/10 | 2/5 | ⚠️ Weak |

**Top gaps highlighted in amber:** Regulatory compliance (most important weakness).
**Adequate (needs development):** Fintech domain — close but needs explicit evidence.

---

## Top Gaps Section

A summary section at the top (or bottom) of the screen:

**"Top 2 gaps for Fintech PM:"**
1. Regulatory compliance (2/5) — 5/10 postings require this
2. Fintech/payments domain (3/5) — 7/10 postings require this — need stronger evidence

**Recommended actions:**
- "Add 2 more XYZ achievements mentioning fintech/payments context" → /resume-studio?tab=xyz
- "Build skill plan to address regulatory gap" → /skill-plan
- "Talk to coach about your regulatory experience" → [Send to mobile]

---

## Bottom CTA

**[Build skill plan →]** — navigates to /skill-plan with pre-populated gaps from this assessment
