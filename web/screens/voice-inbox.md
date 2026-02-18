# Voice Inbox Screen

**Route:** `/voice-inbox`

## Overview

Voice Inbox is the bridge between mobile coaching sessions and the web platform. It shows all structured items extracted from recent voice sessions, already routed to their appropriate section of the Career Profile.

The user comes here to see what the coach captured, review AI-drafted XYZ/STARL items, and confirm the data is correct.

See also: [Voice to Web Bridge](../../architecture/voice-to-web-bridge.md)

---

## Header

- Title: "Voice Inbox"
- Sync metadata: "Last sync: Yesterday 2:02 PM · 5 new items"
- [Sync now] button (manual refresh)

---

## Item List

Items displayed as glass cards, newest session first. Within a session, grouped by type.

**Session group header:** "Session · Jan 17 · 18 minutes · 5 items extracted"

---

## Item Card Structure

```
┌──────────────────────────────────────────────────────────────┐
│  [XYZ]  XYZ Achievement candidate                            │
│                                                               │
│  "Launched payment processing integration serving            │
│   50K merchants, reducing settlement time by 40%"            │
│                                                               │
│  Draft XYZ:                                                   │
│  Accomplished [reduction in settlement time] as measured by   │
│  [50K merchants, 40% faster clearing] by doing [building      │
│  and shipping payment integration in Q3]                      │
│                                                               │
│  → Routed to: Resume Studio / XYZ bank                       │
│  Source: "Yeah so we shipped that in Q3, ended up at like    │
│           50K merchants..."                                   │
│                                                               │
│  [Edit]  [View in XYZ bank]  [Archive]                       │
└──────────────────────────────────────────────────────────────┘
```

---

## Item Types and Badges

| Type | Badge Color | Destination |
|---|---|---|
| XYZ | Amber | Resume Studio → XYZ bank |
| STARL | Blue | Resume Studio → STARL bank |
| Plan | Purple | Plans screen |
| Skill | Green | Gap Assessment |
| Interview | Gray | Prep Pack context pool |

---

## Alex Johnson — 5 Mock Items

### Item 1: XYZ
**Badge:** [XYZ] amber
**Content:** "Launched payment processing integration serving 50K merchants"
**Draft XYZ:** "Accomplished reduction in settlement time as measured by processing 50K merchant transactions with 40% faster clearing by building and shipping payment integration in Q3"
**Routed to:** Resume Studio / XYZ bank
**Source quote:** "Yeah so we shipped that integration in Q3, it ended up serving like 50 thousand merchants..."

### Item 2: STARL
**Badge:** [STARL] blue
**Title:** "Led cross-functional team of 12 through platform migration"
**Completeness:** 85% (Result needs more quantification)
**Routed to:** Resume Studio / STARL bank
**Competency tags:** [cross-functional leadership] [delivery under pressure]

### Item 3: Plan Insight
**Badge:** [Plan] purple
**Content:** "Consider API-first companies (Plaid, Stripe, Braintree) for stronger technical PM fit given your B2B SaaS background"
**Suggested action:** Update Real Plan to add "API-first" as a company-type qualifier
**Routed to:** Plans (as annotation)

### Item 4: Skill Evidence
**Badge:** [Skill] green
**Skill:** Stakeholder management (C-level)
**Evidence:** "Weekly exec check-ins with VP of Product and CTO during the migration project"
**Impact:** Elevates evidence for "Stakeholder management at C-level" in Gap Assessment
**Routed to:** Gap Assessment

### Item 5: Interview Prep
**Badge:** [Interview] gray
**Content:** "Practice explaining product metrics to non-technical audience — common at fintech companies where PM interfaces with compliance and legal teams"
**Relevant for:** All fintech interviews
**Tags:** [metrics communication] [non-technical stakeholders]
**Routed to:** Prep Pack context pool

---

## Actions Per Item

- **[Edit]** — Opens inline editor to refine AI-drafted content
- **[View in XYZ bank / STARL bank / etc.]** — Navigates to where the item was routed
- **[Archive]** — Hides the item (doesn't delete from Career Profile)

---

## Empty State

When no new items:
```
Voice Inbox is empty.
New items appear here after your next coaching session on mobile.

[Open Continuum on mobile]
```

---

## Badge on Sidebar

Voice Inbox nav item shows the count of new items since last visit (e.g., `5`). Clears when user opens Voice Inbox.
