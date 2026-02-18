# Mobile App — Overview

## What It Is

The Continuum mobile app is a **voice-first AI career coaching application**. Its sole purpose is to make it easy for the user to build their Career Profile through natural conversation — no forms, no typing, no structured input required.

The mobile app is the **input** side of the Continuum system. The web platform is the **output** side.

---

## Role in the System

| Question | Answer |
|---|---|
| What is the mobile for? | Building career capital through voice coaching |
| What is the web for? | Deploying career capital into job search |
| How do they connect? | Voice Inbox — extracted items sync automatically |
| Who leads the conversation? | The AI coach (proactive, structured) |
| What does the user do? | Talk. The coach does the work. |

---

## Core Loop (Mobile)

```
1. User opens app (LinkedIn auth complete)
2. User taps "Talk"
3. Coach greets, asks opening question
4. Conversation unfolds (5–30 min)
5. AI extracts structured data in background
6. Session ends (user taps stop, or session time limit)
7. Session summary shown
8. Extracted items synced to web Voice Inbox
9. User returns later, new session picks up where left off
```

---

## Key Screens

| Screen | Purpose |
|---|---|
| [Onboarding / LinkedIn Auth](onboarding.md) | First launch — auth, context setup |
| Talk Screen | Main coaching interface — mic button, live transcript |
| Teleprompter Panel | Shows coach's question/prompt on screen (for hands-free reference) |
| Session Summary | Post-session recap: what was captured |
| Summaries (history) | Past session summaries and extracted items |
| Side Drawer | Navigation: account, history, settings |
| Welcome Back | Returning user screen — quick re-entry to session |
| Account Screen | Profile, subscription status, settings |

See [Screens](screens.md) for full detail.

---

## What Makes It Different

### Voice-first, not voice-added
Most productivity apps add voice as an afterthought. Continuum is voice-native — the entire UX is designed around speaking, not tapping.

### Coach leads, user responds
Users don't have to think "what should I tell the coach today?" The coach has a plan. It knows what data is missing from the Career Profile and asks targeted questions to fill gaps.

### Extraction is invisible
The user never has to say "that was an XYZ achievement, please capture it." The AI identifies, structures, and tags automatically. The conversation feels natural, not like filling out a form.

### Sessions build on each other
The coach remembers everything from previous sessions. It references past discussions, follows up on things mentioned before, and tracks what's been covered and what hasn't.

---

## Design Language

- **Visual:** Dark, minimal, focus on the voice interaction
- **Colors:** Cosmos palette (same as web: `#0a0612` base, amber-glow accents)
- **Typography:** Clean, readable in any lighting condition
- **Animations:** Breathing/pulsing mic indicator during active recording; subtle waveform visualization
- **Key UI element:** Large central mic button — the primary CTA

---

## Tech Notes (PoC reference)

- React Native (mobile framework — to confirm for production)
- Speech-to-text: device STT + cloud API
- Text-to-speech: ElevenLabs or similar (coach voice output)
- AI backend: Claude API for coaching conversation + extraction
- Auth: LinkedIn OAuth

> **Note:** Production tech stack TBD. PoC is reference for UX patterns, not implementation.
