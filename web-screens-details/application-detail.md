# Application Detail Screen

**Route:** `/application/:id`

## Overview

The Application Detail screen is the full record for a single job application. Tracks stage history, contacts, notes, follow-ups, and linked resume/cover letter.

---

## Header

- Company name + role (large)
- Company avatar
- Current stage badge (e.g., "Stage 5 — Interview Round 1")
- Match score
- [Update stage →] button (amber-glow)

---

## Stage Timeline

Horizontal stepper showing progression:

```
Applied  →  Screening  →  Interview 1  →  Interview 2  →  Offer  →  Closed
   ✅              ✅            ●              ○               ○        ○
  Feb 1           Feb 5       Feb 12         —               —        —
```

- Completed stages: filled circle + date
- Current stage: pulsing/highlighted circle
- Future stages: empty circle
- Rejected at any stage: red X at that stage

---

## Stage Update Modal

Clicking [Update stage] opens a modal:
- Select new stage (radio group)
- Add note about what happened (textarea)
- Set next follow-up date (date picker)
- [Save]

---

## Contact Log

Glass card:

- List of all interactions (newest first):
  - Date + type (phone call, email, interview, note)
  - Short description
  - [Add note] button
- Each entry: timestamp + icon + content

---

## Attached Resume & Cover Letter

Glass card:

- Resume version: "PM Resume" + [Preview] link
- Cover letter: "View cover letter" (if written)

---

## Follow-up Scheduler

Glass card:

- Current follow-up: "Send follow-up email — Due Feb 15"
- Status: Due today | Overdue (red) | Upcoming (green)
- [Send] → opens email template (mock)
- [Reschedule] → date picker
- [Mark as done]

---

## Interview Prep Link

If an interview is scheduled:
- "Interview on Feb 12, 10am"
- [Open Prep Pack →] → navigates to `/prep-pack/:id` for this application

---

## Notes

Glass card:

- Free-text notes area (editable)
- [Save notes] button
- Timestamp of last edit
