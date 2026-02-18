# Voice to Web Bridge

## Overview

The Voice to Web Bridge is the mechanism that makes coaching sessions on mobile automatically enrich the web platform. It's the core flywheel of Continuum.

**The promise to the user:**
> "You talk to the coach. Next time you open the web app, everything you discussed is already there — organized and ready to use."

---

## Data Flow

```
MOBILE — during session
─────────────────────────────────────
User talks naturally
    ↓
AI coach asks clarifying questions
    ↓
LLM processes conversation in real-time
    ↓
Extraction pipeline identifies:
  ├── XYZ achievement candidates
  ├── STARL story candidates
  ├── Plan calibration insights
  ├── Skill evidence statements
  └── Interview prep notes
    ↓
Items tagged with:
  - Type (XYZ / STARL / Plan / Skill / Interview)
  - Confidence score
  - Source quote from conversation
  - Competency tags (for STARL)
  - Timestamp

─────────────────────────────────────
SYNC — on session end (or streaming)
─────────────────────────────────────
    ↓
Items pushed to backend Voice Inbox queue
    ↓
Web platform notified (push / polling)
    ↓
Voice Inbox badge count updates

─────────────────────────────────────
WEB — next time user opens web
─────────────────────────────────────
    ↓
Voice Inbox screen shows new items
    ↓
Items auto-routed to destination sections:
  ├── XYZ → Resume Studio / XYZ bank
  ├── STARL → Resume Studio / STARL bank
  ├── Plan insight → Plans (for calibration)
  ├── Skill evidence → Gap Assessment
  └── Interview prep → Prep Pack context pool
```

---

## Voice Inbox Item Types

### 1. XYZ Achievement Candidate
**What it is:** A specific work accomplishment that can be formatted as an XYZ statement.
**Source:** User mentions a project outcome, metric, or impact during session.
**How it's extracted:** Coach asks "What was the impact?" "How was it measured?" "What specifically did you do?" — then synthesizes into XYZ structure.
**Destination:** Resume Studio → XYZ bank (pending review or auto-added).

**Example:**
```
Type: XYZ
Extracted: "Launched payment processing integration serving 50K merchants"
Draft XYZ: "Accomplished reduction in settlement time (X) as measured by processing
           50K merchant transactions with 40% faster clearing (Y) by building
           and shipping payment integration in Q3 (Z)"
Source quote: "Yeah so we shipped that integration in Q3, it ended up serving
               like 50 thousand merchants..."
Competency tags: [delivery, fintech, cross-functional]
```

### 2. STARL Story Candidate
**What it is:** A behavioral story that can be structured as STARL.
**Source:** User describes a challenging situation, a decision they made, or a conflict they navigated.
**How it's extracted:** Coach uses the STARL frame to ask follow-up questions. Synthesizes after enough detail collected.
**Destination:** Resume Studio → STARL bank.

**Example:**
```
Type: STARL
Title: "Led cross-functional team through platform migration"
Competency tags: [cross-functional leadership, stakeholder management, delivery under pressure]
Situation: "We were migrating our core platform to a new infra while maintaining 100% uptime..."
Task: "As PM, I was responsible for coordinating 3 engineering teams and 2 stakeholders..."
Action: "I set up a daily 15-min standup, built a shared risk register, ran weekly exec check-ins..."
Result: "Completed migration 2 weeks ahead of schedule, zero downtime incidents..."
Learning: "I learned that proactive stakeholder communication is more valuable than reactive updates..."
Completeness: 85% (Result needs more quantification)
```

### 3. Plan Insight
**What it is:** A reflection or observation about the user's career direction that should update their Plans.
**Source:** User expresses uncertainty, discovers new information, or recalibrates.
**Destination:** Plans screen (for user to review and incorporate).

**Example:**
```
Type: Plan insight
Content: "Consider API-first companies (Plaid, Stripe, Braintree) — stronger technical
         PM fit given your B2B SaaS background"
Suggested action: Review Real Plan to add "API-first" as a qualifier for target companies
```

### 4. Skill Evidence
**What it is:** A concrete example of using a specific skill that can strengthen the Gap Assessment.
**Source:** User mentions an instance of using a skill that appears as a gap.
**Destination:** Gap Assessment (raises self-assessment evidence for that skill).

**Example:**
```
Type: Skill evidence
Skill: Stakeholder management (C-level)
Evidence: "Weekly exec check-ins with VP of Product and CTO during the migration project"
Impact on Gap Assessment: Elevates self-score for "Stakeholder management at C-level" from 3 → 4
```

### 5. Interview Prep Note
**What it is:** A coaching tip, common question, or preparation note relevant to the user's upcoming interviews.
**Source:** Coach surfaces common interview patterns for target role, or user mentions an upcoming interview.
**Destination:** Prep Pack context pool (surfaced when relevant interview is scheduled).

**Example:**
```
Type: Interview prep
Content: "Practice explaining product metrics to non-technical audience — common at fintech
         companies where PM interfaces with compliance and legal teams"
Relevant for: All fintech interviews
Tags: [metrics communication, non-technical stakeholders]
```

---

## Auto-Routing Logic

Items are automatically routed without requiring user action:

| Item Type | Auto-destination | User action needed |
|---|---|---|
| XYZ candidate | Added to XYZ bank with "from session" tag | Can edit, delete |
| STARL candidate | Added to STARL bank with "from session" tag | Can edit, delete |
| Plan insight | Added to Plans as annotation | Can incorporate or dismiss |
| Skill evidence | Updates Gap Assessment evidence | Can accept or reject |
| Interview prep | Added to prep context pool | Surfaces in Prep Pack |

> **Open question:** The exact UX of "auto-added" vs. "pending review." User said items appear automatically. But for XYZ/STARL, the drafts extracted by AI may need refinement before use. Do we auto-add as drafts? Or auto-add as "pending" with different visual treatment? See [Open Questions](../open-questions.md).

---

## Voice Inbox Screen (Web)

The Voice Inbox screen is the visible manifestation of this bridge. It shows:
- All items from the most recent sync
- Item type badges (XYZ / STARL / Plan / Skill / Interview)
- Content preview
- Timestamp of session
- Quick actions: Edit, Route to..., Archive

Even though items auto-route, the Voice Inbox gives the user visibility and control:
- Review what was captured
- Edit AI drafts before they become "official"
- See source quotes from the conversation

**Badge in sidebar:** Shows count of new items since last web visit. Clears when Voice Inbox is opened.

---

## Sync Timing

> **Open question:** Sync frequency and mechanism not yet specified. Options:
>
> - **Real-time streaming:** Items appear in web Voice Inbox as they're extracted during session (requires websocket connection)
> - **End-of-session push:** Items sync when session ends (simpler, slight delay)
> - **On next web open:** Items sync lazily when user opens web (acceptable for MVP)
>
> For MVP, "on next web open" (polling on load) is likely sufficient.
