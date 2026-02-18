# Application Draft Screen

**Route:** `/application-draft/:id`

## Overview

The Application Draft screen is where the user prepares a job application — selecting the right resume version, reviewing the match, and optionally writing a cover letter — before sending.

This screen bridges "vacancy discovered" and "application submitted."

---

## Header

- Company name + role title (from vacancy)
- Company avatar (colored circle)
- Job link: [View original posting →] (external)
- Draft status badge: "Ready to send" (green) | "Needs edits" (amber) | "Draft" (muted)

---

## Match Summary

Glass card:

```
┌──────────────────────────────────────────────────┐
│  Match Analysis — NeoBank · Senior PM            │
│                                                   │
│  Overall match: 82%  ████████░░                  │
│                                                   │
│  Must-haves covered:                             │
│  ✅ Product management 5+ years                  │
│  ✅ Cross-functional leadership                   │
│  ✅ Data-driven decisions                         │
│  ⚠️  Fintech domain — indirect experience        │
│  ✅ Stakeholder management C-level               │
│  ○  Regulatory compliance — not covered          │
└──────────────────────────────────────────────────┘
```

---

## Resume Version Selector

Glass card:

- "Select resume version to use:"
- Dropdown or radio group:
  - PM Resume (72% coverage) — [currently selected]
  - Fintech PM Resume (not yet created) — [Create →]
- [Preview resume] button → opens resume preview modal
- Coverage indicator updates based on selection

---

## Cover Letter Editor

Glass card (optional section):

- "Cover letter" header + [Skip] toggle
- Textarea (glass style, editable)
- [Generate draft] button → AI generates cover letter based on:
  - Vacancy requirements
  - User's Career Profile (XYZ and STARL most relevant to this role)
  - Summary from Resume Studio
- Character count / word count

> **MVP note:** Generation may be simplified (template-based) or skipped entirely. See [Open Questions](../../open-questions.md).

---

## Bottom Actions

- [Save draft] — saves without submitting
- [Send application →] — marks as applied, moves to Pipeline at Stage 3, creates Application Detail record

---

## Navigation

- Accessible from: Today Preparing (vacancy table → [Prepare draft]), Pipeline (row action), Today Active (Apply Queue)
- After sending: navigates to Application Detail (`/application/:id`)
