# Plans Screen

**Route:** `/plans`

## Overview

The Plans screen is where the user defines and maintains their 4-plan career strategy. It forces clarity about direction by requiring all four plans — Ideal, Real, Compromise, and Anti — to be articulated simultaneously.

See [Core Concept](../../product-definition/core-concept.md) for the full framework explanation.

---

## Layout

**Header:**
- Title: "Plans"
- Subtitle: "Calibrate your career by defining four parallel plans — where you're aiming, what's realistic, what you'd accept, and what to avoid."

**Body:**
4 cards in a responsive grid (2×2 on desktop, 1-column on mobile):

```
┌─────────────────┐  ┌─────────────────┐
│  ⭐ IDEAL PLAN  │  │  📋 REAL PLAN   │
│                 │  │                 │
│  [content]      │  │  [content]      │
│  [Calibrate]    │  │  [Calibrate]    │
└─────────────────┘  └─────────────────┘

┌─────────────────┐  ┌─────────────────┐
│  🤝 COMPROMISE  │  │  ❌ ANTI-PLAN   │
│                 │  │                 │
│  [content]      │  │  [content]      │
│  [Calibrate]    │  │  [Avoid path]   │
└─────────────────┘  └─────────────────┘
```

**Bottom bar:**
- "Send calibration questions to your mobile" + [Send to mobile] button

---

## Plan Cards

### Ideal Plan Card
**Accent:** Amber star icon (⭐)
**Badge:** None (or "I" for Ideal in amber)
**Border:** Default glass

**Content:**
- "Your ideal scenario" label
- Title: "Become a CPO at a leading fintech company"
- Success criteria list:
  - Equity stake in the company
  - Board-level visibility and reporting
  - Conference speaking and thought leadership
  - Managing a team of product managers
- [Calibrate] button (secondary style)

---

### Real Plan Card
**Accent:** Blue "R" badge
**Border:** Info-colored border (blue) OR default glass
**Special:** Warning if horizon > 5 years ("Long horizon — consider splitting into milestones")

**Content:**
- "What you're actually pursuing" label
- Title: "Get a Senior PM role at a fintech company"
- Horizon tag: "3 years" (with amber ⚠️ if > 5 years)
- Success criteria list:
  - Fintech domain experience (payments)
  - Managing a product squad of 8+
  - Working at a company with strong product culture
  - Visa/sponsorship optional
- [Calibrate] button

---

### Compromise Plan Card
**Accent:** Gray "C" badge
**Border:** Default glass

**Content:**
- "Acceptable fallback" label
- Title: "Accept PM role in adjacent domain (e-commerce, logistics)"
- Trade-offs acknowledged:
  - Lower seniority acceptable
  - Domain is different from fintech
  - Build transferable skills, re-target later
- Conditions to activate:
  - "If no fintech offer after 8 months of active search"
- [Calibrate] button

---

### Anti-Plan Card
**Accent:** Red "✕" badge
**Border:** Danger-colored border (subtle red glow)

**Content:**
- "What you're avoiding" label
- Title: (can be blank — defined by risks list)
- Risks / what to avoid:
  - Legacy enterprise PM roles
  - Waterfall development environments
  - Companies without product culture
  - Pure project management (no ownership)
  - Excessive bureaucracy and slow decision-making
- [Avoid this path] button (danger style, secondary)

---

## Calibration Flow

When user taps [Calibrate] on any card:
- Opens a modal or inline edit form
- For MVP: simple text editing of the plan fields
- Later: AI-assisted calibration guided by coach questions

The "Send calibration questions to mobile" bottom bar button queues a set of calibration questions for the next voice coaching session, so the coach can help refine the plans through conversation.

---

## Sidebar Badge

The Plans nav item in the sidebar shows a badge of `1` when a plan needs attention (e.g., Real Plan horizon > 5 years, or a plan is empty/incomplete).
