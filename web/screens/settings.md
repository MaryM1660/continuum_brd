# Settings Screen

**Route:** `/settings`

## Overview

Settings for the web platform. Covers behavior configuration, integrations, and account management.

---

## Layout

Single-column, sectioned glass cards.

---

## Section: Job Search Behavior

### Stuck Threshold
"Flag application as 'stuck' after:"
- ○ 7 days (default)
- ○ 10 days
- ○ 14 days

Controls when the "⚠ Stuck N days" flag appears in Pipeline.

### Daily Routine Mode
"Prioritize apply queue by:"
- ○ Top Roles (highest match score first)
- ● Standard Roles (chronological / balanced)

---

## Section: Search Status

"Current search status:"
- ● Preparing
- ○ Active
- ○ Paused

> **Note:** This is the demo toggle for switching between Preparing and Active modes on the Today screen. In production, switching to Active is a deliberate transition with a confirmation step.

---

## Section: Integrations

### Google Calendar
- "Google Calendar: Connected" (green badge) + [Disconnect] button
- Shows last sync time
- If not connected: [Connect Google Calendar] button

### LinkedIn
- "LinkedIn: Connected as Alex Johnson" + profile link
- [Disconnect LinkedIn] → warning modal (this will log you out)

---

## Section: Notifications

> **Open question:** Push notifications design TBD.

Placeholder section — checkboxes for:
- [ ] Session reminders (mobile push)
- [ ] Follow-up due reminders
- [ ] New Voice Inbox items

---

## Section: Data

- [Export my data] — downloads Career Profile as JSON/ZIP (mock button)
- [Delete account] — destructive, requires typing "DELETE" to confirm

---

## Section: About

- App version: 1.0.0-mvp
- [Terms of Service] [Privacy Policy] links
