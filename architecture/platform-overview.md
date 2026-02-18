# Platform Overview

## System Architecture (Conceptual)

Continuum is a two-platform product with a shared backend:

```
┌─────────────────────────────────────────────────────────────┐
│                        USER                                  │
│                                                              │
│    ┌──────────────────┐          ┌───────────────────────┐  │
│    │   MOBILE APP     │          │     WEB PLATFORM      │  │
│    │  (iOS / Android) │          │  (browser, desktop)   │  │
│    │                  │          │                        │  │
│    │  • Voice coach   │          │  • Career strategy    │  │
│    │  • STARL/XYZ     │◄────────►│  • Resume Studio      │  │
│    │    extraction    │  sync    │  • Pipeline            │  │
│    │  • Teleprompter  │          │  • Voice Inbox         │  │
│    │  • Summaries     │          │  • Gap Assessment      │  │
│    └────────┬─────────┘          └───────────┬───────────┘  │
│             │                                │              │
└─────────────┼────────────────────────────────┼──────────────┘
              │                                │
              ▼                                ▼
┌─────────────────────────────────────────────────────────────┐
│                      BACKEND                                 │
│                                                              │
│  ┌─────────────┐  ┌──────────────┐  ┌──────────────────┐   │
│  │   Auth      │  │   Career     │  │   AI Pipeline    │   │
│  │  (LinkedIn  │  │   Profile    │  │                  │   │
│  │   OAuth)    │  │   Storage    │  │  • LLM (coach)   │   │
│  └─────────────┘  └──────────────┘  │  • Extraction    │   │
│                                      │  • Matching      │   │
│  ┌─────────────┐  ┌──────────────┐  └──────────────────┘   │
│  │  Voice      │  │  Sync /      │                          │
│  │  Processing │  │  Voice Inbox │                          │
│  │  (STT/TTS)  │  │  Queue       │                          │
│  └─────────────┘  └──────────────┘                          │
└─────────────────────────────────────────────────────────────┘
              │
              ▼
┌─────────────────────────────────────────────────────────────┐
│                    LINKEDIN                                   │
│              (OAuth identity provider)                       │
└─────────────────────────────────────────────────────────────┘
```

***

## Platform Roles

### Mobile App — "The Coach"

The mobile app is where career capital is **built**. It is conversational, voice-first, low-friction.

**Key characteristics:**

* User opens it during commute, lunch break, before sleep
* Sessions are 5–30 minutes
* The AI coach leads the conversation — the user doesn't need to know what to say
* Extraction happens in the background — user just talks naturally
* Post-session: brief summary of what was captured

**What flows OUT of mobile:** Structured career data — XYZ statements, STARL stories, plan insights, skill evidence — automatically synced to the backend after each session.

### Web Platform — "The Workspace"

The web is where career capital is **deployed**. It is structured, information-dense, strategic.

**Key characteristics:**

* Used at a desk, during dedicated work time
* User reviews extracted data, builds strategies, creates artifacts
* Resumes, plans, gap assessments, applications are managed here
* The data in the web is entirely driven by what the mobile coach extracted

**What flows INTO web:** Everything from mobile sessions, via the Voice Inbox system.

### LinkedIn — Identity Provider

LinkedIn serves as the authentication mechanism for both platforms. The same LinkedIn account links mobile and web together.

**What we use from LinkedIn:**

* Identity (name, email) for account creation
* Profile data (current role, company) for pre-populating initial career context

> **Open question:** Exact scope of LinkedIn data pulled at auth time. See [Open Questions](../open-questions.md).

***

## Key Data Entities

| Entity            | Lives In | Created By            | Used By                                      |
| ----------------- | -------- | --------------------- | -------------------------------------------- |
| Career Profile    | Backend  | Mobile coaching       | Web (Resume Studio, Gap Assessment)          |
| XYZ Achievements  | Backend  | Mobile coaching       | Web (Resume Studio, Resume versions)         |
| STARL Stories     | Backend  | Mobile coaching       | Web (Resume Studio, Prep Packs)              |
| Real Plans        | Backend  | Web (Plans screen)    | Web (Target Picker, Market Readiness)        |
| Ideal Plan        | Backend  | Web (Plans screen)    | Web (Target Picker)                          |
| Compromise Plan   | Backend  | Web (Plans screen)    | Web (Plans screen)                           |
| Anti-Plan         | Backend  | Web (Plans screen)    | Web (Plans screen)                           |
| Ideal Profile     | Backend  | Web (Profiles screen) | Web (Gap Assessment, Resume Studio)          |
| Target            | Backend  | Web (Target Picker)   | Web (all screens — drives context)           |
| Vacancies         | Backend  | Web (Today screen)    | Web (Profiles, Pipeline)                     |
| Applications      | Backend  | Web (Pipeline)        | Web (Pipeline, Application Detail)           |
| Voice Inbox Items | Backend  | Mobile coaching       | Web (Voice Inbox → routed to other entities) |
| Resume Versions   | Backend  | Web (Resume Studio)   | Web (Applications, export)                   |

***

## Authentication Flow

```
Mobile launch                     Web launch
      │                                 │
      ▼                                 ▼
LinkedIn OAuth                    LinkedIn OAuth
      │                                 │
      ▼                                 ▼
Backend creates / retrieves user   Backend verifies user
      │                                 │
      ▼                                 ▼
Mobile session starts             Web workspace loads with
                                  user's Career Profile data
```

Same LinkedIn account = same backend user = data visible on both platforms.

***

## Sync Architecture — Voice Inbox

The Voice Inbox is the critical bridge between mobile and web. See detailed doc: [Voice to Web Bridge](voice-to-web-bridge.md).

**High level:**

1. Mobile coaching session runs
2. LLM extracts structured items during conversation (real-time or post-session)
3. Extracted items queued in backend Voice Inbox store
4. Web platform polls / receives push update → Voice Inbox badge count increments
5. Items automatically routed to appropriate sections (XYZ bank, STARL bank, etc.)
6. User sees new items in Voice Inbox screen on web with full context
