# Voice Session Mechanics

## Overview

The voice session is the core interaction on mobile. It's a real-time conversation between the user and an AI career coach. The coach asks questions, the user answers, and structured career data is extracted in the background.

---

## Session Lifecycle

```
1. PRE-SESSION
   ─────────────────────────────────
   User taps "Talk" or "Start session"
   Coach context loaded from backend:
     - Previous session summaries
     - Current Career Profile state (what's missing)
     - Active target (Real Plan + Ideal Profile)
     - Pending follow-ups from last session

2. SESSION OPENING
   ─────────────────────────────────
   Coach greets (uses user's name)
   Coach sets context or asks opening question
   Microphone activates

3. ACTIVE CONVERSATION
   ─────────────────────────────────
   User speaks → STT converts to text
   LLM processes user text in context of full conversation
   Coach responds (text → TTS → audio output)
   AI extraction pipeline runs in background:
     - Identifies XYZ candidates
     - Identifies STARL threads
     - Flags plan insights
     - Notes skill evidence

4. SESSION END
   ─────────────────────────────────
   Triggered by:
     - User taps stop button
     - Session time limit reached (paywall trigger — TBD)
     - Network interruption

5. POST-SESSION
   ─────────────────────────────────
   Session summary generated
   Extracted items synced to backend
   Voice Inbox updated on web
   Summary screen shown to user
```

---

## The Talk Screen

The main UI during a session:

```
┌─────────────────────────────────────┐
│                                      │
│     [Coach name / avatar]            │
│                                      │
│  ┌─────────────────────────────────┐ │
│  │  Live transcript or waveform    │ │
│  │  visualization                  │ │
│  └─────────────────────────────────┘ │
│                                      │
│     Coach's current question:        │
│  ┌─────────────────────────────────┐ │
│  │  "What was the specific impact  │ │
│  │   of that project? Any numbers  │ │
│  │   you can share?"               │ │
│  └─────────────────────────────────┘ │
│                                      │
│           ┌───────────┐              │
│           │  ●  MIC   │              │  ← Primary CTA (large, pulsing when active)
│           └───────────┘              │
│                                      │
│    [⏸ Pause]  [📄 Teleprompter]  [⏹ End] │
└─────────────────────────────────────┘
```

**States of the mic button:**
- Idle: static button, "Tap to start"
- Recording: pulsing animation + audio waveform
- Coach speaking: different animation (listening state)
- Processing: loading indicator

---

## Teleprompter Mode

The Teleprompter Panel is an optional overlay that shows the coach's question/prompt as large text on screen. Designed for:
- Hands-free use (phone propped up, user talks while walking/commuting)
- Users who prefer reading the question while formulating their answer
- Accessibility (hearing coach audio might be difficult in noisy environments)

**Toggle:** Small button on Talk Screen. Opens as a panel overlay, semi-transparent.

```
┌─────────────────────────────────────┐
│  ░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░   │  ← dimmed background
│  ░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░   │
│                                     │
│  ┌─────────────────────────────┐   │
│  │                             │   │
│  │   What was the impact       │   │  ← Large, readable text
│  │   of that project?          │   │
│  │                             │   │
│  │   Any numbers you can       │   │
│  │   share?                    │   │
│  │                             │   │
│  └─────────────────────────────┘   │
│                                     │
│          [● MIC  ●]                 │  ← Mic still visible
│          [Close teleprompter]       │
└─────────────────────────────────────┘
```

---

## How the Coach Works

### Context the Coach Has
- Full career profile to date (XYZ bank, STARL bank, plans)
- All previous session summaries
- Active target (Real Plan + Ideal Profile)
- Ideal Profile must-haves (knows what's still missing in coverage)
- Gap Assessment state (knows which skills are weak)

### Coach Behavior
The coach is **proactive and structured** — it has a plan. It doesn't wait for the user to know what to say.

**Principles:**
1. **Always have a goal for the session.** Coach starts with an intent (e.g., "Today I want to try to capture 2 more XYZ achievements from your DataFlow experience").
2. **Ask one question at a time.** No overwhelming multi-part questions.
3. **Drill down for specifics.** If user gives a vague answer ("We improved performance"), coach asks for the number ("What was the actual improvement? Any benchmarks?").
4. **Use the STARL frame.** When user tells a story, coach guides through S→T→A→R→L without making it feel like an interview.
5. **Reference previous sessions.** "Last time you mentioned the migration project — I'd love to dig into that more today."
6. **End with synthesis.** At end of session, briefly recaps what was captured.

### Topics the Coach Covers
Rotates based on what the Career Profile needs most:
- Work achievements (XYZ mining)
- Behavioral stories (STARL development)
- Career plans (calibration, horizon discussion)
- Target role research (what does the user know about their target?)
- Skill gaps (evidence gathering for weak areas)
- Interview preparation (practice questions for upcoming interviews)
- Market insights (what the user is seeing in their job search)

---

## Document Upload During Session

> **Status: Open question** — UX not yet designed. See [Open Questions](../open-questions.md).

Documents that can be shared with the coach:
- User's current resume (coach can reference specific roles, help update language)
- A job posting (coach can identify gaps, prep questions for that specific role)
- A performance review (coach can help translate to XYZ/STARL)

**Candidate UX patterns:**
- A) User says "I want to talk about my resume" → coach asks "Can you share it?" → upload button appears
- B) Persistent paper clip icon on Talk Screen → taps anytime to upload
- C) Upload happens before session starts (in pre-session setup screen)

---

## Session Summary Screen

Shown after every session:

```
┌─────────────────────────────────────┐
│  SESSION COMPLETE                   │
│  Duration: 18 minutes               │
│                                     │
│  Captured today:                    │
│  ┌─────────────────────────────┐   │
│  │ ✦ 2 XYZ achievements        │   │
│  │ ✦ 1 STARL story (draft)     │   │
│  │ ○ 1 plan insight             │   │
│  └─────────────────────────────┘   │
│                                     │
│  Synced to your web workspace ✓    │
│                                     │
│  [View summaries]   [Done]          │
└─────────────────────────────────────┘
```

---

## Error & Edge Cases

| Scenario | Handling |
|---|---|
| Microphone permission denied | Explain why needed, link to settings |
| Network drops mid-session | Continue recording locally, sync when connection restores |
| STT fails / low confidence | Coach asks user to repeat ("Could you say that again?") |
| Session ends unexpectedly | Partial session saved, extracted items still synced |
| Paywall limit reached mid-session | TBD — see [Open Questions](../open-questions.md) |
| User is in a noisy environment | Coach detects poor audio quality, suggests moving to quieter place |
