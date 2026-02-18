# Open Questions

All unresolved design, product, and business decisions. Each question has a dedicated future session topic. Status: `open` | `decided` | `in-progress`.

---

## Paywall & Monetization

### [open] Paywall trigger — exact moment
**Question:** When exactly does the paywall appear?
- After 1 complete session?
- After 30 minutes of total talk time?
- After the first session ends and user tries to start a second?

**What we know:** "After 1 session or 30 minutes." Needs to be reconciled — these are different triggers.

**Impact:** UX of the paywall screen, session state management, backend billing integration.

**Future session topic:** `paywall-design`

---

### [open] Paywall — in-session experience
**Question:** What happens to a session that's mid-conversation when the limit is hit?
Options:
- A) Coach mid-sentence stops, hard paywall appears
- B) Coach finishes the current thought, then says "I'd love to continue — let's set you up with a subscription"
- C) Session continues until a natural break point, then paywall on next session start
- D) User gets a warning with N minutes remaining

**Impact:** Session architecture, coach dialogue design, user trust.

**Future session topic:** `paywall-design`

---

### [open] Free tier definition
**Question:** What does the free tier include beyond the first session? Or is it strictly: 1 session free, then paid?

**Impact:** Top-of-funnel conversion, onboarding experience, value demonstration.

---

### [open] Pricing model
**Question:** Subscription (monthly/annual)? One-time? Freemium with feature gates?

**Impact:** Web paywall UX, backend billing, AppStore/PlayStore setup.

---

## Mobile App — Sessions & Coaching

### [open] Document upload — exact UX
**Question:** When user wants to discuss a document (resume, job posting), how does upload work in a voice-first interface?

Options:
- A) Coach proactively asks "Would you like to share your resume?" → button appears
- B) User-initiated: taps a paperclip/upload icon mid-session
- C) Pre-session: upload happens before starting the session, available as context throughout
- D) Not in mobile MVP — documents handled on web only

**What we know:** Document upload is in mobile MVP scope.

**Impact:** Mobile UI (TalkScreen), session architecture, file handling.

**Future session topic:** `mobile-document-upload`

---

### [open] Session structure — scripted vs. free-form
**Question:** Does the coach follow a script for the first session, or is it fully free-form from the start?

Hypothesis: First session has a guided onboarding arc (collect baseline info: current role, target, timeline), subsequent sessions are free-form with optional focus topics.

**Impact:** AI prompt design, session state management, first-time user flow.

---

### [open] Coach personality & name
**Question:** Does the coach have a name/persona? Or is it just "Continuum Coach"?

---

### [open] Session summary — what gets shown
**Question:** After a session, what does the user see in the Summaries screen? Full transcript? Key bullets? Structured data extracted?

---

### [open] Push notifications
**Question:** Does the mobile app send reminders? ("Time for your coaching session," "You have 3 items in your Voice Inbox")

---

## Mobile App — Onboarding

### [open] LinkedIn auth — exact data pulled
**Question:** What data do we pull from LinkedIn at auth time?
- Profile basics (name, headline, current role)?
- Work history (to pre-populate career profile)?
- Connections (for network features)?
- Nothing beyond identity (name + email)?

**Impact:** Onboarding experience, privacy/permissions, data model.

**Future session topic:** `onboarding-flow`

---

### [open] First session — what happens immediately after LinkedIn auth
**Question:** Does the user land immediately in a voice session, or is there an onboarding screen first?

**What we know:** LinkedIn auth is the first step. After that, we want minimal friction to first voice session.

---

## Web Platform

### [open] Voice Inbox — auto-accept vs. review
**Question:** When coaching session extracts an XYZ candidate or STARL story, does it:
- A) Auto-add to the bank immediately (no user action needed)
- B) Land in Voice Inbox as a pending item for user to review and accept/edit/reject
- C) Auto-add with notification, but user can edit/remove later

**What we know:** User said items appear "automatically." This implies option A or C. Details TBD.

**Impact:** Voice Inbox screen purpose, notification design, data quality expectations.

**Future session topic:** `voice-inbox-design`

---

### [open] Web MVP scope — which screens are P1
**Question:** The PoC has ~15 screens. Are all of them in MVP, or is there a phased rollout?

**Current assumption:** All screens are in scope for MVP (as per user instruction "write everything"). But priority order within MVP is TBD.

**Candidates for post-MVP:**
- Prep Pack (nice to have, but not critical for core loop)
- Application Draft (detailed view — Pipeline covers the basics)
- Skill Plan (can be manual initially)

**Future session topic:** `web-screen-prioritization`

---

### [open] Resume export format
**Question:** When exporting a resume version, what formats are supported?
- PDF only?
- PDF + DOCX?
- Copy to clipboard?
- Google Docs integration?

---

### [open] Calendar integration
**Question:** Is Google Calendar integration required for MVP, or optional?
- Used for: interview scheduling display, "Calendar connected" badge on Today Active screen
- If not available at MVP: show empty state gracefully

---

## Data & Privacy

### [open] Multi-language
**Question:** English only for MVP?

---

### [open] Data storage — where are voice recordings stored?
**Question:** Are raw audio recordings stored, or just transcripts + extracted data?

**Impact:** Privacy policy, storage costs, GDPR compliance (if EU users).

---

### [open] Account deletion — what happens to data?
**Question:** If user deletes account, what happens to their Career Profile, STARL bank, XYZ bank?

---

## Team & Collaboration

### [open] Sharing and team features
**Question:** Any sharing features in MVP? (E.g., share resume version with recruiter, share plan with mentor)

**Current assumption:** No — single-user product in MVP.

---

## UX / Design

### [open] Mobile ↔ Web sync frequency
**Question:** How quickly do Voice Inbox items appear on web after a mobile session?
- Real-time (websocket/push)?
- On next web page load?
- Manual sync button?

---

### [open] Today screen toggle for demo
**Question:** In the demo/PoC, how does the user switch between Preparing and Active mode?
- Toggle in Settings?
- Accessible from TopBar (Search Status pill)?
- Hardcoded for demo?

---

## Tracking

| Question | Status | Future Session |
|---|---|---|
| Paywall trigger exact moment | open | paywall-design |
| In-session paywall experience | open | paywall-design |
| Document upload UX (mobile) | open | mobile-document-upload |
| LinkedIn data pulled at auth | open | onboarding-flow |
| Voice Inbox: auto-accept vs review | open | voice-inbox-design |
| Web MVP screen priority | open | web-screen-prioritization |
| Resume export formats | open | resume-studio-design |
| Calendar integration (MVP?) | open | web-screen-prioritization |
| Coach name/persona | open | mobile-coaching-design |
| Push notifications | open | mobile-coaching-design |
| Multi-language | open | — |
