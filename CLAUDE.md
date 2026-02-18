# CLAUDE.md

## Project Overview

This repository is the **Business Requirements Document (BRD)** for **Continuum**, an AI-powered career development product consisting of two platforms:

- **Mobile App** — Voice-first AI coaching that extracts structured career data (XYZ achievements, STARL stories) from natural conversation
- **Web Platform** — Career management workspace that converts extracted data into resumes, job strategies, gap assessments, and interview preparation

This is a **documentation-only repository** (Markdown files). There is no application source code, build system, or test suite here.

## Repository Structure

```
├── README.md                  # Executive summary
├── SUMMARY.md                 # Table of contents / navigation index
├── glossary.md                # 21 key terms and definitions
├── open-questions.md          # Unresolved design/business decisions
│
├── product-definition/        # Product strategy, scope, and metrics
│   ├── purpose.md
│   ├── target-users.md
│   ├── core-concept.md
│   ├── mvp-scope.md
│   ├── success-metrics.md
│   ├── paywall.md
│   └── notifications.md
│
├── architecture/              # System design and data flow
│   ├── platform-overview.md
│   └── voice-to-web-bridge.md
│
├── mobile/                    # Mobile app specs (onboarding, voice sessions)
├── mobile-app/                # Mobile screen hierarchy
│
├── web/                       # Web platform overview and design system
├── web-platform/              # Web navigation, screen hierarchy, states
├── web-screens-details/       # Detailed specs for all 13 web screens
│
└── user-flows/                # End-to-end user journey documentation
```

## Key Terminology

Use terms consistently as defined in `glossary.md`. Critical terms:

- **XYZ Achievement** — "Accomplished X as measured by Y by doing Z" format
- **STARL Story** — Situation → Task → Action → Result → Learning (with competency tags)
- **Plans** — Four-plan framework: Ideal, Real, Compromise, Anti
- **Voice Inbox** — Queue of items auto-extracted during mobile coaching, routed to web sections
- **Market Readiness** — North star metric calculated from plans, profiles, XYZ/STARL coverage, and gap assessment
- **Target** — An Ideal Profile that drives all calculations on the web platform

## Architecture

```
Mobile App (Voice Input) → Backend (Extraction & Storage) → Web Platform (Strategy Output)
```

The **Voice Inbox** bridges mobile and web: items extracted during coaching sessions are auto-routed to the appropriate web sections (XYZ bank, STARL bank, Gap Assessment, Plans).

## MVP Priorities

**P1 (Core Loop):** Today, Plans, Target Picker, Profiles, Gap Assessment, Resume Studio, Pipeline, Voice Inbox

**P2 (Nice-to-have):** Application Draft/Detail, Prep Pack, Skill Plan, Settings

## Design System

The web platform uses a **dark glassmorphism** theme:

- Base color: `#0a0612` (cosmos-900)
- Accent: `#e8933a` (amber-glow)
- Typography: Inter font family
- CSS framework: Tailwind CSS v4 with custom `@theme` tokens
- Animations: Framer Motion for page transitions
- See `web/design-system.md` for full specification

## Conventions

- All documentation is in Markdown with consistent heading hierarchy (H1 → H2 → H3)
- Screen specs follow a pattern: purpose, layout, components, states, interactions
- Open decisions are tracked in `open-questions.md` — check there before making assumptions
- The demo persona is **Alex Johnson** (Senior PM, 62% Market Readiness, Preparing mode)
