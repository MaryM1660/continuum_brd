# Glossary

Key terms used across the Continuum product. All future sessions and documents should use these definitions consistently.

---

## Career Strategy Terms

### Real Plan
One of the four strategic career plans. Describes a concrete, achievable career goal with a defined time horizon (e.g., "Get a Senior PM role at a fintech company — 3 years"). This is the plan actively being executed. Multiple Real Plans can exist; one is selected as the **active target** at a time.

### Ideal Plan
One of the four strategic career plans. Describes the aspirational, long-term career goal — the best possible outcome (e.g., "Become CPO at a leading fintech company"). Serves as a north star, not an immediate target. Typically 5–10+ years out.

### Compromise Plan
One of the four strategic career plans. Describes an acceptable fallback — what the user would be willing to do if the Real Plan proves too slow or blocked (e.g., "Accept PM role in adjacent domain like e-commerce"). Has explicit activation conditions and trade-offs acknowledged upfront.

### Anti-Plan
One of the four strategic career plans. Describes what the user explicitly wants to avoid — roles, environments, or trajectories that would be bad outcomes (e.g., "No legacy enterprise PM, no waterfall, no bureaucracy"). Used to filter out bad-fit opportunities.

### Target
The combination of a **Real Plan** and an **Ideal Profile** currently selected as active. The Target determines which job listings are relevant, which resume version to use, and what the Market Readiness score measures against. Selected via the **Target Picker**.

### Search Status
The current phase of the user's job search. Affects which view of the Today dashboard is shown:
- **Preparing** — building career capital before actively applying
- **Active** — actively applying to jobs
- **Paused** — search paused (on break, accepted offer, etc.)

---

## Profile Terms

### Career Profile
The accumulated body of structured career data for a user. Consists of the XYZ achievement bank and the STARL story bank. Built through voice coaching sessions and manual entry. Used as the source material for resume generation and interview prep.

### Ideal Profile
A structured model of what a target job requires, built by analyzing real job vacancies. Contains must-have skills (with frequency counts), nice-to-haves, and typical experience requirements. One Ideal Profile can be created per target job type (e.g., "Fintech PM", "B2B SaaS PM"). Used as the standard against which the user's Career Profile is assessed.

### Vacancy Batch
A collection of job postings analyzed to create an Ideal Profile. The user pastes or imports job links; the system extracts requirement patterns to build the profile.

---

## Achievement & Story Terms

### XYZ Achievement
A structured achievement statement in the format:
> "Accomplished **[X]** as measured by **[Y]** by doing **[Z]**"

Example: "Launched payment processing integration (X) serving 50K merchants and reducing settlement time by 40% (Y) by leading a cross-functional squad of 8 across 3 time zones (Z)."

XYZ achievements are the atoms of a resume. Each one should map to one or more must-haves from the Ideal Profile. Coverage is tracked as a percentage.

### STARL Story
A structured behavioral interview story in the format:
> **Situation** → **Task** → **Action** → **Result** → **Learning**

STARL extends the classic STAR format by adding the **Learning** — what the candidate took away from the experience. This makes stories more authentic and demonstrates self-awareness.

Each STARL story maps to competency tags (e.g., "cross-functional leadership", "conflict resolution", "data-driven decisions") and is used to prepare for behavioral interview questions.

---

## Readiness Terms

### Market Readiness
A percentage score (0–100%) measuring how prepared a user is to successfully apply for their target role. Calculated based on:
- Plans calibrated
- Ideal Profile created
- Gap assessment completed
- Resume skeleton ready
- Resume version created
- XYZ coverage (achieved / required)
- STARL coverage (stories / target)
- Skill plan status

### Gap Assessment
A comparison between the user's self-assessed skill levels and the requirements of the Ideal Profile. Shows which must-haves are strong, adequate, or weak, and highlights the most critical gaps to close before applying.

### Readiness Checklist
A specific list of 8 items tracked on the Today (Preparing) screen. Each item has a status: complete, warning, partial, or incomplete. Shows progress toward being "ready to start job search."

---

## Application Terms

### Pipeline
The full list of active job applications across all stages of the hiring process. Stages are numbered 1–8:
1. Discovered
2. Saved
3. Applied
4. Screening
5. Interview Round 1
6. Interview Round 2+
7. Offer
8. Closed

### Resume Version
A targeted version of the user's resume, generated for a specific Ideal Profile. Each version selects the most relevant XYZ achievements and structures them to match the target job's must-haves. Coverage is tracked (must-have coverage %, behavioral coverage %).

### Prep Pack
A curated set of interview preparation materials assembled for a specific job application. Contains: relevant STARL stories, relevant XYZ achievements, likely tested competencies, small talk prep, checklist.

---

## Platform Terms

### Voice Inbox
A feed of structured items automatically extracted from mobile voice coaching sessions. Items appear on the web platform and are automatically added to the relevant part of the Career Profile:
- XYZ candidates → Resume Studio / XYZ bank
- STARL candidates → Resume Studio / STARL bank
- Plan insights → Plans
- Skill evidence → Gap Assessment
- Interview prep notes → Prep Pack

> **Open question:** Do items auto-accept or require user review? Currently leaning toward automatic, but UX needs to be defined.

### Target Picker
The screen (web) where the user selects which Real Plan and Ideal Profile to use as their active target. This combination drives all readiness calculations, resume recommendations, and pipeline filtering.

### Voice Session
A coaching session on the mobile app. The user talks; the AI coach asks structured questions, reflects back, and extracts structured data in the background. Sessions can be open-ended or focused on a specific topic (e.g., "Tell me about your last project").
