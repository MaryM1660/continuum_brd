# Core Concept

This document explains the conceptual framework that Continuum is built on. Understanding this is required context for all future design and development sessions.

---

## The Four-Plan Framework

Career thinking is usually binary: "I want to stay" or "I want to leave." Continuum replaces this with a structured four-plan model that clarifies the full strategic landscape simultaneously.

All four plans exist at once, and the user actively maintains them:

### 1. Ideal Plan
> "If everything went perfectly over the next 10 years, what would I become?"

The aspirational north star. This isn't what you're aiming for right now — it's what motivates the entire journey. Having it explicit prevents short-term compromises that foreclose long-term possibilities.

*Alex Johnson's Ideal Plan:* Become CPO at a leading fintech company. Board visibility, equity stake, managing a team of PMs, speaking at conferences.

### 2. Real Plan
> "What's the next concrete career step I'm actually going to pursue? In what timeframe?"

This is the active plan — the one being executed. It has a specific role, company tier, skill requirements, and time horizon. Market Readiness measures progress against this plan.

Multiple Real Plans can exist (e.g., "Fintech PM" AND "Tech Lead" AND "Startup Founder"), but only one is selected as the **active target** at a time via the Target Picker.

*Alex Johnson's Real Plan:* Senior PM at a fintech company (Stripe, Revolut, Wise tier). Fintech domain experience, payments, team of 8+. Time horizon: 3 years.

### 3. Compromise Plan
> "If the Real Plan doesn't work out in time, what's the fallback I'd accept without regret?"

Named explicitly to avoid accidentally accepting a compromise without having thought through the trade-offs. This plan has activation conditions — specific things that would make the user shift to it.

*Alex Johnson's Compromise Plan:* Accept PM role in adjacent domain (e-commerce, logistics). Lower seniority acceptable. Build transferable domain skills, then re-target fintech later.

### 4. Anti-Plan
> "What am I specifically trying to avoid? What would be a bad outcome?"

Making the anti-goals explicit prevents the user from sleepwalking into bad situations — accepting a role because they were flattered or desperate, not because it fits their actual criteria.

*Alex Johnson's Anti-Plan:* No monotonous enterprise PM. No legacy systems, no waterfall process, no excessive bureaucracy, no environment without product culture.

---

## The Career Profile

The Career Profile is the user's accumulated body of structured career evidence. It's built over time through voice coaching sessions. It contains:

### XYZ Achievement Bank
Individual achievement statements in the format:
> "Accomplished **[X]** as measured by **[Y]** by doing **[Z]**"

Each XYZ covers a specific accomplishment with a metric. The bank grows with each coaching session. Achievements are tagged to skills/competencies and map to must-haves in the Ideal Profile.

**Why XYZ:**
- Forces specificity and quantification
- Directly usable in resumes (each bullet is an XYZ)
- Comparable across candidates (structured format enables AI matching)

### STARL Story Bank
Behavioral interview stories in the format:
> **S**ituation → **T**ask → **A**ction → **R**esult → **L**earning

STARL extends classic STAR by adding **Learning** — this makes stories more authentic and shows self-awareness, which modern interviewers value highly.

Each STARL is tagged to one or more competencies (e.g., "stakeholder management", "conflict resolution", "leading under ambiguity"). In a Prep Pack, the system surfaces the most relevant stories for a specific role and interview type.

**Why STARL over STAR:**
- Learning element differentiates strong candidates
- Demonstrates growth mindset
- More authentic — hard to fake

---

## Ideal Profile

The Ideal Profile is a data-driven model of what a specific target role requires. It's built from analyzing real job postings — not from intuition or guess.

**Construction process:**
1. User collects 10–15 job postings for their target role
2. User pastes links into the Profiles / Vacancy Batches screen
3. System extracts requirement patterns: what skills appear in how many postings
4. Output: a ranked list of must-haves (with frequency) and nice-to-haves

**Why data-driven:**
Most people have a vague sense of what they need. The Ideal Profile makes it concrete: "Fintech/payments domain appears in 7 of 10 postings — that's a must-have, not optional."

---

## Target = Real Plan × Ideal Profile

The **Target** is the combination of a Real Plan and an Ideal Profile currently selected as active:

```
Target = Real Plan (direction + timeline) × Ideal Profile (specific role requirements)
```

Example: Alex's target is "Senior Product Manager" (Real Plan) × "Fintech PM" (Ideal Profile).

This combination determines:
- What Market Readiness measures against
- Which vacancies are relevant
- Which resume version to recommend
- Which STARL stories to surface in interview prep

Multiple targets can exist simultaneously (e.g., targeting both fintech PM and B2B SaaS PM). One is selected as "active" at a time via the Target Picker.

---

## Market Readiness Score

A single number (0–100%) that answers: **"How ready are you to start applying for your target role?"**

Calculated from the Readiness Checklist (8 items):

| Item | Status Logic |
|---|---|
| Plans calibrated | All 4 plans defined and not empty |
| Ideal Profile created | At least one vacancy batch analyzed |
| Gap Assessment completed | Self-assessment done for all must-haves |
| Skill plan created | At least one skill goal defined |
| Resume skeleton ready | Work history structure entered |
| Resume version created | At least one resume version for target |
| XYZ achievements coverage | X of Y must-haves covered by at least one XYZ |
| STARL stories coverage | X of Y target stories written |

**Alex Johnson demo:** 62% (plans done, profile done, gap done, skeleton in progress, no fintech-specific resume yet)

The score is prominently displayed in the TopBar on web (visible on every screen) and in the Today Active dashboard.

---

## Search Phases

The product maps to three phases of a job search. The user declares which phase they're in:

### Preparing
> "I'm building my career capital before I start applying."

- Today dashboard shows: Vacancy collection, Readiness Checklist, Next Best Step
- Focus: building XYZ bank, writing STARL stories, creating Ideal Profile, filling gaps
- Market Readiness is the primary metric
- Gate to transition: Market Readiness reaches threshold + user makes deliberate decision to go Active

### Active
> "I'm actively applying and managing my pipeline."

- Today dashboard shows: Apply Queue, Follow-ups, Calendar, Market Readiness panel
- Focus: applying, tracking, preparing for interviews, updating pipeline
- Pipeline becomes the primary operational tool
- Market Readiness continues to update (more XYZ/STARL written during active search)

### Paused
> "Search is on hold."

- Could be: accepted offer, life event, strategic pause
- Data persists, no daily urgency

**Key insight:** Most products assume users are always "Active." Continuum recognizes that Preparing is its own distinct phase — and arguably the most important one to support well.

---

## Voice → Web Data Flow

The mobile coaching sessions generate structured data that automatically flows into the web platform:

```
Mobile voice session
    ↓ (real-time AI extraction during conversation)
Structured items:
  - XYZ candidates
  - STARL candidates
  - Plan insights
  - Skill evidence
  - Interview prep notes
    ↓ (sync on session end)
Web: Voice Inbox (notification badge updates)
    ↓ (automatic routing)
  - XYZ → Resume Studio / XYZ bank
  - STARL → Resume Studio / STARL bank
  - Plan insights → Plans (for review)
  - Skill evidence → Gap Assessment
  - Interview prep → Prep Pack context
```

This is the core flywheel: the more you talk to the coach, the richer your web profile becomes, the better your resumes and interview prep get.
