# Settings Modification Flow

## Overview

How users find, change, and apply settings on both platforms.

---

## Web Settings

### Accessing Settings
- Via gear icon in TopBar (right side)
- Via gear icon at bottom of Sidebar
- Route: `/settings`

### Common Settings Changes

#### Change stuck threshold
```
Settings → "Job Search Behavior" section
Select: 7 / 10 / 14 days
Applied immediately — Pipeline updates stuck flags on next load
```

#### Change search status (demo toggle / real transition)
```
Settings → "Search Status" section
Select: Preparing / Active / Paused
If switching to Active: confirmation modal
  "This will change your Today dashboard to Active mode."
  [Confirm] [Cancel]
Applied immediately — Today screen reloads in new mode
```

#### Connect Google Calendar
```
Settings → "Integrations" section
[Connect Google Calendar] →
OAuth flow (Google auth) →
"Google Calendar connected" badge appears
Today Active screen now shows Calendar Strip with real events
```

#### Disconnect LinkedIn
```
Settings → "Integrations" section
[Disconnect LinkedIn] →
Warning modal: "This will log you out of Continuum on all devices."
[Confirm disconnect] → logged out, redirected to login screen
```

#### Export data
```
Settings → "Data" section
[Export my data] →
Download starts (Career Profile as ZIP: JSON + resume versions)
```

---

## Mobile Settings

Settings on mobile are accessible via:
- Side Drawer → Account Screen

### Account Screen Settings

#### Manage subscription
```
Account Screen → [Manage subscription]
Opens: Subscription management (in-app purchase or web)
Options: Monthly / Annual plan
Cancel subscription option
```

#### Disconnect LinkedIn (mobile)
```
Account Screen → [Disconnect LinkedIn]
Warning: "This will log you out"
[Confirm] → logged out, Welcome Screen appears
```

---

## Key Principle

Settings changes should be **immediately visible** — no need to save/reload. The only exception is destructive changes (disconnect, delete account) which require confirmation dialogs.
