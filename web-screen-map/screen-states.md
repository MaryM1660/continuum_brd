# Web Screen States

All meaningful states for web platform screens with visual and behavioral differences.

---

## Global Web States

### Search Status
Controls which Today screen variant is shown and the TopBar Search Status pill color.

| Status | Today Screen | TopBar Pill | Sidebar Badge |
|---|---|---|---|
| Preparing | Preparing mode | Amber border | "Preparing" text |
| Active | Active mode | Green border | "Active" text |
| Paused | Simplified / placeholder | Muted | "Paused" text |

### Authentication State

| State | Behavior |
|---|---|
| Not authenticated | Redirect to LinkedIn OAuth |
| Authenticated, first time | Today screen with onboarding prompt banner |
| Authenticated, returning | Today screen (normal) |
| Session expired | Transparent re-auth; if fails → LinkedIn OAuth redirect |

### Market Readiness Score

| Range | Color | Label |
|---|---|---|
| 0–30% | Danger red | "Just getting started" |
| 31–59% | Warning amber | "Building your profile" |
| 60–74% | Info blue | "Getting close" |
| 75–89% | Success green | "Ready to apply" |
| 90–100% | Bright green | "Highly prepared" |

*Alex Johnson demo state: 62% — "Getting close"*

---

## Today Screen

### Preparing Mode — Module States

**Vacancies Collected:**
| State | Visual |
|---|---|
| Empty | Input bar only + "Add your first vacancy" prompt |
| Has unclassified | Rows with amber [Classify] buttons |
| All classified | Rows with green [Prepare draft] buttons |

**Next Best Step card:**
| State | Visual |
|---|---|
| Has recommendation | Amber accent border + specific task + impact text |
| All items complete | "All done — ready to go Active!" message |

**Ready to Start banner:**
| State | Condition |
|---|---|
| Hidden | Market Readiness < 75% |
| Shown | ≥ 75% AND status = Preparing |
| Hidden again | User switches to Active |

### Active Mode — Module States

**Apply Queue:**
| State | Visual |
|---|---|
| Has items | List with [Send →] buttons |
| Empty | "Queue empty — add applications from Pipeline" |

**Follow-ups Due:**
| State | Visual |
|---|---|
| None due | "All follow-ups done ✓" |
| Due today | Normal highlight |
| Overdue | Danger red highlight |

**Calendar Strip:**
| State | Visual |
|---|---|
| Connected, has events | Events list |
| Connected, no events | "No interviews this week" |
| Not connected | "Connect Google Calendar" CTA |

---

## Plans Screen

| Card | State | Visual |
|---|---|---|
| Any plan | Filled | Normal glass card |
| Any plan | Empty | Warning border + "Add this plan" prompt |
| Real Plan | Horizon > 5 years | Amber warning badge |
| Real Plan | Active target | Subtle amber-glow background |

---

## Resume Studio — Tab States

**XYZ Tab:**
| State | Visual |
|---|---|
| Empty bank | "No achievements yet — talk to your coach" |
| Has items | Achievement cards + coverage indicator bar |
| Full coverage | Success "Full coverage achieved" banner |

**STARL Tab:**
| State | Visual |
|---|---|
| Empty bank | "No stories yet" |
| Has items | Story cards with completeness bars |
| Incomplete story | Completeness bar < 100% highlighted |

**Versions Tab:**
| State | Visual |
|---|---|
| No versions | "Create your first resume version" CTA |
| Has versions | Version cards with coverage % |
| Version outdated (new XYZ added) | "Coverage improved — update version?" prompt |

---

## Pipeline — Application States

| State | Badge | Color | Trigger |
|---|---|---|---|
| Normal | Stage number | Default | Active, progressing |
| Needs attention | ⚠️ | Amber | Overdue follow-up |
| Stuck | ⚠️ Stuck N days | Red | No update > threshold days |
| Interview upcoming | 📅 | Blue | Interview in next 48h |
| Rejected | ✕ | Red | Stage = Rejected |
| Offer received | ★ | Gold | Stage = Offer |

---

## Voice Inbox States

| State | Visual |
|---|---|
| New items | Items list + badge count in sidebar |
| All reviewed | "You're caught up ✓" empty state |
| Sync in progress | Loading indicator in header |
| Sync failed | Error + [Retry] button |

---

## Empty States

Every section with no data has a designed empty state with a clear CTA:

| Screen / Section | Message | CTA |
|---|---|---|
| Voice Inbox | "No items yet — start a coaching session on mobile" | [Open app] |
| XYZ bank | "No achievements yet — talk to your coach" | [Send prompts to mobile] |
| STARL bank | "No stories yet — your coach will help you build them" | [Send prompts to mobile] |
| Pipeline | "No active applications" | [Go to Today] |
| Profiles | "No ideal profiles yet" | [+ Create new batch] |
| Gap Assessment | "Complete your ideal profile first" | [→ Profiles] |
| Skill Plan | "Start from your gap assessment" | [→ Gap Assessment] |
| Apply Queue (Today Active) | "Queue empty" | [Add from Pipeline] |
| Calendar Strip | "Connect Google Calendar" | [Connect] |
