# MVP Scope

## Scope Definition

The MVP includes both the mobile coaching app and the web career management platform. The goal is to validate the core loop:

> **Voice coaching → structured Career Profile → targeted resume → better job applications**

***

## Mobile MVP

### In Scope

| Feature                       | Notes                                                                                               |
| ----------------------------- | --------------------------------------------------------------------------------------------------- |
| **LinkedIn authentication**   | Mandatory first step. No guest mode in MVP.                                                         |
| **Voice coaching sessions**   | Core feature. AI coach leads conversation.                                                          |
| **STARL extraction**          | Coach extracts Situation/Task/Action/Result/Learning from conversation                              |
| **XYZ extraction**            | Coach extracts achievement statements during conversation                                           |
| **Plan insights extraction**  | Career direction notes captured during session                                                      |
| **Skill evidence extraction** | Evidence of competencies noted during conversation                                                  |
| **Teleprompter mode**         | User can see coach's questions/prompts on screen during session                                     |
| **Session summaries**         | Post-session summary screen showing what was captured                                               |
| **Voice Inbox sync**          | Extracted items sent to web Voice Inbox automatically                                               |
| **Document upload**           | User can share a document (resume, job posting) during session                                      |
| **Paywall**                   | After N sessions / N minutes of talk time. Details TBD — see [open questions](../open-questions.md) |
| **Welcome back screen**       | Returning user experience                                                                           |
| **Account screen**            | Basic profile, settings                                                                             |

### Out of Scope (Mobile MVP)

| Feature                         | Reason                                              |
| ------------------------------- | --------------------------------------------------- |
| Guest mode                      | Decided against — LinkedIn auth required from start |
| Direct resume editing on mobile | Web-only feature                                    |
| Pipeline management on mobile   | Web-only feature                                    |
| Push notifications (reminders)  | Open question — likely post-MVP                     |
| Multiple languages              | English only in MVP                                 |
| Apple Watch / other wearable    | Post-MVP                                            |

***

## Web MVP

> **Note:** Per product direction, all screens from the PoC are in scope for web MVP. Priority order within MVP is TBD — see [open questions](../open-questions.md).

### In Scope — All Screens

| Screen                    | Route                    | Priority  |
| ------------------------- | ------------------------ | --------- |
| Today (Preparing mode)    | `/`                      | P1 — core |
| Today (Active mode)       | `/`                      | P1 — core |
| Plans                     | `/plans`                 | P1 — core |
| Target Picker             | `/target-picker`         | P1 — core |
| Profiles / Ideal Profiles | `/profiles`              | P1 — core |
| Gap Assessment            | `/gap-assessment`        | P1 — core |
| Resume Studio             | `/resume-studio`         | P1 — core |
| Pipeline                  | `/pipeline`              | P1 — core |
| Voice Inbox               | `/voice-inbox`           | P1 — core |
| Application Draft         | `/application-draft/:id` | P2        |
| Application Detail        | `/application/:id`       | P2        |
| Prep Pack                 | `/prep-pack/:id`         | P2        |
| Skill Plan                | `/skill-plan`            | P2        |
| Settings                  | `/settings`              | P2        |

### In Scope — Features

| Feature                              | Notes                                                                |
| ------------------------------------ | -------------------------------------------------------------------- |
| **Today dashboard (Preparing mode)** | Vacancy collection, readiness checklist, next best step, voice sync  |
| **Today dashboard (Active mode)**    | Apply queue, follow-ups, calendar strip, market readiness panel      |
| **4-Plan framework**                 | Ideal, Real, Compromise, Anti — display and calibration              |
| **Ideal Profile creation**           | Based on vacancy batch analysis                                      |
| **Gap Assessment**                   | Skill cluster matrix vs Ideal Profile                                |
| **Resume Studio (5 tabs)**           | Summary, Structure, XYZ, STARL, Versions, AI-generated cover letters |
| **XYZ bank**                         | Add, view, track coverage vs must-haves                              |
| **STARL bank**                       | Add, view, map to competency tags                                    |
| **Resume versions**                  | Create, export, track coverage %                                     |
| **Pipeline**                         | List + kanban toggle, all 14 applications, filters                   |
| **Voice Inbox**                      | Auto-populated from mobile sessions, 5 item types                    |
| **Market Readiness score**           | Calculated, shown in TopBar and Today Active                         |
| **Target Picker**                    | Select Real Plan + Ideal Profile combination                         |
| **Application Draft**                | Vacancy details, resume version selector, cover letter editor        |
| **Application Detail**               | Stage timeline, contact log, follow-up scheduler                     |
| **Prep Pack**                        | STARL stories + XYZ mapped to specific interview                     |
| **Skill Plan**                       | 8-week plan, goals, resources                                        |
| **Settings**                         | Stuck threshold, calendar connection, routine toggle                 |
| **LinkedIn authentication**          | Shared auth with mobile                                              |

### Out of Scope (Web MVP)

| Feature                       | Reason                          |
| ----------------------------- | ------------------------------- |
| Team / collaboration features | Single-user product in MVP      |
| Public profile / portfolio    | Post-MVP                        |
| Job board integrations        | Manual vacancy input in MVP     |
| ATS integrations              | Post-MVP                        |
| Mobile-responsive design      | Web-first, desktop focus in MVP |
| Multiple languages            | English only                    |
| Recruiter-facing features     | Post-MVP                        |

***

## Key Design Decisions (Already Made)

| Decision             | Choice                         | Notes                               |
| -------------------- | ------------------------------ | ----------------------------------- |
| Mobile auth method   | LinkedIn mandatory             | No guest mode                       |
| Story format         | STARL                          | Adds Learning component             |
| Achievement format   | XYZ                            | Standard Laszlo Bock format         |
| Design language      | Dark glassmorphism             | Cosmos palette (#0a0612 base)       |
| Voice Inbox behavior | Items appear automatically     | No manual accept step               |
| Demo mode            | Hardcoded Alex Johnson persona | Toggle Preparing/Active in Settings |

***

## Open Questions Affecting Scope

See [Open Questions](../open-questions.md) for full detail.

* Paywall trigger and experience (mobile)
* Document upload UX (mobile)
* Voice Inbox: auto-accept confirmation UX
* Resume export formats (PDF? DOCX?)
* Calendar integration required for MVP?
