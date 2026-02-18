# Skill Plan Screen

**Route:** `/skill-plan`

## Overview

The Skill Plan is a time-boxed development plan addressing the user's identified skill gaps. Generated from the Gap Assessment — specifically the weak/missing must-haves from the Ideal Profile.

---

## Header

- Title: "Skill Plan"
- Context: "Closing gaps for Fintech PM target"
- Time box selector: "8 weeks ▾" (options: 4 / 8 / 12 weeks)
- [Add to calendar] button (mock — exports plan to Google Calendar)

---

## Plan Overview

Top-level summary:

```
┌────────────────────────────────────────────────────┐
│  8-week plan to close 2 critical gaps              │
│                                                    │
│  Gap 1: Regulatory compliance (2/5 → target: 3/5) │
│  Gap 2: Fintech domain evidence (3/5 → target: 4/5)│
└────────────────────────────────────────────────────┘
```

---

## Plan Items

Glass cards — one per goal:

### Card 1: Regulatory Compliance

```
┌──────────────────────────────────────────────────────┐
│  Goal: Understand fintech regulatory landscape       │
│  Covers: Regulatory compliance (2/5 → 3/5)          │
│  Weeks: 1–4                                          │
│                                                      │
│  Resources:                                          │
│  • Read: "The Payment Card Industry Data Security    │
│    Standard (PCI-DSS)" overview                      │
│  • Course: "Fintech Compliance Essentials" (Coursera)│
│  • Talk to coach: "Tell me about any compliance      │
│    exposure you had at DataFlow"                     │
│                                                      │
│  Outcome: 2 XYZ achievements mentioning compliance  │
│           context; 1 STARL with compliance theme     │
│                                                      │
│  Status: Not started                                 │
│  [Mark as started]  [Send to mobile]                 │
└──────────────────────────────────────────────────────┘
```

### Card 2: Fintech Domain Evidence

```
┌──────────────────────────────────────────────────────┐
│  Goal: Build explicit fintech/payments narrative     │
│  Covers: Fintech/payments domain (3/5 → 4/5)        │
│  Weeks: 1–8                                          │
│                                                      │
│  Resources:                                          │
│  • Review existing work: DataFlow payments features  │
│  • Read: Stripe, Revolut, Wise product blogs         │
│  • Talk to coach: "Walk me through your experience   │
│    with payment flows at DataFlow"                   │
│                                                      │
│  Outcome: 3 XYZ achievements with payments/fintech  │
│           context; 2 STARL with domain framing       │
│                                                      │
│  Status: In progress                                 │
│  [Mark complete]  [Send to mobile]                  │
└──────────────────────────────────────────────────────┘
```

---

## Must-Have Mapping

Shows which plan items address which Ideal Profile must-haves:

| Must-have | Current | Target | Plan item |
|---|---|---|---|
| Regulatory compliance | 2/5 | 3/5 | Card 1 |
| Fintech/payments domain | 3/5 | 4/5 | Card 2 |

---

## Bottom Actions

- [+ Add custom goal] — user can add a plan item not derived from gap assessment
- [Add all to calendar] — exports plan timeline to Google Calendar (mock)
- [Send plan to coach] — queues plan review for next mobile session
