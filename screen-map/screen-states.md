# Screen States

All meaningful states that screens can be in, with visual/behavioral differences documented.

---

## Global States

### Search Status
Affects Today screen layout, Sidebar user section badge, and TopBar Search Status pill.

| Status | Today Screen | Sidebar | TopBar Pill |
|---|---|---|---|
| Preparing | Preparing mode | "Preparing" label | Amber border pill |
| Active | Active mode | "Active" label | Green border pill |
| Paused | Simplified view | "Paused" label | Muted pill |

### Authentication State
| State | Mobile | Web |
|---|---|---|
| Not authenticated | Welcome screen | LinkedIn OAuth redirect |
| Authenticated (first time) | Context Setup | Today (with onboarding prompts) |
| Authenticated (returning) | Welcome Back | Today (normal) |
| Session expired | Silent re-auth attempt → LinkedIn OAuth if failed | LinkedIn OAuth redirect |

---

## Mobile Screens

### Talk Screen States
| State | Visual | Behavior |
|---|---|---|
| Idle (before start) | Static mic button | "Tap to start" label |
| Recording (user speaking) | Pulsing mic animation + waveform | STT active, coach listening |
| Coach responding | Different animation (listening state) | TTS playing coach response |
| Processing | Loading indicator on mic | AI processing input |
| Paused | Paused indicator | Session paused, mic inactive |
| Paywall limit approaching | Warning banner: "X minutes remaining" | Session continues |
| Paywall limit reached | Session end + paywall screen | See paywall states |
| Network lost | Banner: "Connection lost" | Local buffering |

### Welcome Back Screen States
| State | Triggers | Content |
|---|---|---|
| Standard returning | Normal re-entry | Last session info + CTA |
| Long absence (>2 weeks) | No session in 14+ days | Adjusted messaging, gentle re-engagement |
| Interview upcoming | Interview in calendar within 24h | Interview highlighted, Prep Pack CTA |
| New Voice Inbox items | Items from last session pending web review | "N items in your workspace" |

---

## Web Screens

### Today Screen States

#### Preparing Mode — Module States

**Vacancies Collected module:**
| State | Content |
|---|---|
| Empty (no vacancies) | Input bar + "Add your first vacancy" prompt |
| Has unclassified vacancies | Rows with [Classify] buttons highlighted |
| All classified | Rows with [Prepare draft] buttons |

**Next Best Step card:**
| State | Content |
|---|---|
| Has recommendation | Specific task + impact + [Start] button |
| All done | "All items complete — ready to go Active!" |

**Ready to Start banner:**
| State | Condition |
|---|---|
| Hidden | Market Readiness < 75% |
| Shown | Market Readiness ≥ 75% (or specific gates met) |
| Already Active | Banner replaced by "You're in Active mode" |

#### Active Mode — Module States

**Apply Queue:**
| State | Content |
|---|---|
| Has items | Queue of applications ready to send |
| Empty | "No applications queued — add from Pipeline" |

**Follow-ups Due:**
| State | Content |
|---|---|
| None due | Empty state or "All follow-ups done ✓" |
| Due today | Highlighted items |
| Overdue | Red highlighting on overdue items |

**Calendar Strip:**
| State | Content |
|---|---|
| Calendar connected | Events shown |
| Calendar not connected | "Connect Google Calendar" CTA |
| No upcoming events | "No interviews scheduled this week" |

---

### Plans Screen — Card States

| Card | State | Visual |
|---|---|---|
| Any plan | Complete | Normal glass card |
| Any plan | Empty/Not filled | Warning border + "Add this plan" prompt |
| Real Plan | Horizon > 5 years | Amber warning badge on card |
| Real Plan | Currently active target | Amber-glow subtle glow |

---

### Resume Studio — Tab States

**XYZ Tab:**
| State | Content |
|---|---|
| Empty bank | "No achievements yet — talk to your coach" |
| Has items | Achievement cards + coverage indicator |
| All must-haves covered | Success banner "Full coverage achieved" |

**STARL Tab:**
| State | Content |
|---|---|
| Empty bank | "No stories yet" |
| Has items | Story cards |
| Incomplete story | Completeness bar shows < 100% |

**Versions Tab:**
| State | Content |
|---|---|
| No versions | "Create your first resume version" CTA |
| Has version(s) | Version cards with coverage % |
| Version needs update (new XYZ added) | "Coverage improved — update this version?" |

---

### Pipeline — Application States

| State | Badge | Color | Trigger |
|---|---|---|---|
| Normal | Stage number | Default | Active, moving forward |
| Needs attention | ⚠️ | Amber | Overdue follow-up |
| Stuck | ⚠️ Stuck N days | Amber/red | No update for > threshold |
| Interview upcoming | 📅 | Blue | Interview in next 48h |
| Rejected | ✕ | Red | Stage updated to Rejected |
| Offer | ★ | Gold | Stage = Offer |

---

### Voice Inbox — States

| State | Content |
|---|---|
| New items (unread) | Items displayed, badge count shown |
| All reviewed | "You're caught up" empty state |
| Sync in progress | Loading indicator in header |
| Sync failed | Error state + [Retry] button |

---

### Market Readiness Score — States

| Range | Color | Label |
|---|---|---|
| 0–30% | Danger red | "Just getting started" |
| 31–59% | Warning amber | "Building your profile" |
| 60–74% | Info blue | "Getting close" |
| 75–89% | Success green | "Ready to apply" |
| 90–100% | Success green (bright) | "Highly prepared" |

Alex Johnson's current state: 62% — "Getting close"

---

## Empty States Strategy

Every screen that can be empty has a designed empty state:

| Screen | Empty State Message | CTA |
|---|---|---|
| Voice Inbox | "No items yet — start a coaching session on mobile" | [Open app] |
| XYZ bank | "No achievements yet — talk to your coach" | [Send prompts to mobile] |
| STARL bank | "No stories yet — your coach will help you build them" | [Send prompts to mobile] |
| Pipeline | "No active applications — start applying when ready" | [Go to Today] |
| Profiles | "No ideal profiles yet — create your first" | [+ Create new batch] |
| Gap Assessment | "Complete your ideal profile first" | [→ Profiles] |
| Skill Plan | "No skill plan yet — start from gap assessment" | [→ Gap Assessment] |
