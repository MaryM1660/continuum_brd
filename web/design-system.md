# Design System — Dark Glassmorphism

## Overview

The Continuum web design system uses a **dark glassmorphism** aesthetic that mirrors the mobile app. The visual language communicates: focused, modern, intentional — a tool for serious career work, not a cheerful HR platform.

Source of truth: `src/index.css` in the web PoC repository.

---

## Color Palette

### Cosmos (Base)

| Token | Hex | Usage |
|---|---|---|
| `cosmos-950` | `#050309` | Deepest background, overlay |
| `cosmos-900` | `#0a0612` | Primary body background |
| `cosmos-800` | `#120a24` | Elevated surfaces |
| `cosmos-700` | `#1a1035` | Card backgrounds (alternative) |

### Amber Glow (Accent)

| Token | Hex | Usage |
|---|---|---|
| `amber-glow` | `#e8933a` | Primary CTA, active nav, key metrics |
| `amber-glow-dim` | `#e8933a4d` | Amber backgrounds, badges, hover states |

The amber accent is the single warm color in an otherwise cool/dark palette. Used sparingly for maximum impact. Every amber element signals: "this is important" or "this requires action."

### Glass System

| Token | Value | Usage |
|---|---|---|
| `glass` | `#ffffff0f` (white 6%) | Default card background |
| `glass-border` | `#ffffff1f` (white 12%) | Card borders |
| `glass-hover` | `#ffffff1a` (white 10%) | Hover state fill |
| `glass-strong` | `#ffffff26` (white 15%) | Elevated cards, selected states |

### Semantic Colors

| Token | Hex | Usage |
|---|---|---|
| `success` | `#00c758` | Complete status, active pipeline stage, green metrics |
| `warning` | `#f99c00` | Warning status, amber pipeline flags |
| `danger` | `#fb2c36` | Error, Anti-Plan badge, stuck/failed states |
| `info` | `#60a5fa` | Informational, Real Plan badge |

### Text Hierarchy

| Token | Value | Usage |
|---|---|---|
| `text-primary` | `#ffffffee` (white 93%) | Primary text, headings |
| `text-secondary` | `#ffffff99` (white 60%) | Secondary text, labels |
| `text-muted` | `#ffffff55` (white 33%) | Placeholder, disabled, timestamps |

---

## CSS Tokens (Tailwind v4 @theme)

```css
@theme {
  /* Cosmos palette */
  --color-cosmos-950: #050309;
  --color-cosmos-900: #0a0612;
  --color-cosmos-800: #120a24;
  --color-cosmos-700: #1a1035;

  /* Amber accent */
  --color-amber-glow: #e8933a;
  --color-amber-glow-dim: #e8933a4d;

  /* Glass system */
  --color-glass: #ffffff0f;
  --color-glass-border: #ffffff1f;
  --color-glass-hover: #ffffff1a;
  --color-glass-strong: #ffffff26;

  /* Semantic */
  --color-success: #00c758;
  --color-warning: #f99c00;
  --color-danger: #fb2c36;
  --color-info: #60a5fa;

  /* Text */
  --color-text-primary: #ffffffee;
  --color-text-secondary: #ffffff99;
  --color-text-muted: #ffffff55;
}
```

**Body:**
```css
body {
  background-color: var(--color-cosmos-900);
  color: var(--color-text-primary);
  -webkit-font-smoothing: antialiased;
}
```

---

## Glass Component Classes

```css
@layer components {
  .glass {
    background: var(--color-glass);
    border: 1px solid var(--color-glass-border);
    backdrop-filter: blur(20px);
    -webkit-backdrop-filter: blur(20px);
  }

  .glass-strong {
    background: var(--color-glass-strong);
    border: 1px solid var(--color-glass-border);
    backdrop-filter: blur(24px);
    -webkit-backdrop-filter: blur(24px);
  }
}
```

---

## Typography

**Font:** Inter (already loaded via `@fontsource/inter` or Google Fonts)
**Font smoothing:** `antialiased` on body

| Usage | Size | Weight | Token |
|---|---|---|---|
| Page title | 24px / 1.5rem | 600 | — |
| Section heading | 18px / 1.125rem | 600 | — |
| Card title | 16px / 1rem | 500 | — |
| Body text | 14px / 0.875rem | 400 | text-primary |
| Secondary text | 14px / 0.875rem | 400 | text-secondary |
| Label / caption | 12px / 0.75rem | 400 | text-muted |
| Badge / pill | 11px / 0.6875rem | 500 | — |

---

## UI Components

### GlassCard
Base container. Variants:
- `default` — standard glass background + border
- `strong` — glass-strong background (for elevated/selected content)
- `accent` — glass background + amber-glow border (for highlighted cards, Next Best Step)
- `danger` — glass background + danger-colored border

Usage: nearly every content container on the platform.

### Button
Variants:
- `primary` — amber-glow fill, cosmos-900 text, full width or auto
- `secondary` — glass border + fill, white text
- `ghost` — transparent, white text, no border
- `danger` — danger fill, white text

### Badge / StatusPill
Pill-shaped label with background fill:
- **Preparing:** amber border + amber dim bg
- **Active:** success green
- **Paused:** glass (muted)
- **Match score:** green (>75%), amber (50–75%), danger (<50%)
- **Unclassified:** amber border (for vacancies)
- **Stage labels:** numbered + color (stage 1-2: muted, 3-5: info, 6-7: success, 8: danger for rejected)

### Avatar
Circular container with user/company initials. Color determined deterministically from first letter:
- A, B, C → amber
- D, E, F → blue
- G, H, I → green
- etc. (full mapping TBD — consistent hash function)

### ProgressBar
Thin horizontal bar (4px or 8px height):
- Market Readiness: amber fill
- Coverage complete: success fill
- Coverage partial: warning fill

### Tabs
Glass tab bar with animated active indicator (sliding underline or fill). Used in Resume Studio.

### Modal
Glass overlay with cosmos-950 backdrop (blur). Sizes: sm (400px), md (560px), lg (720px).

### Toast
Top-right notification. Auto-dismiss after 4 seconds. Types: success, warning, info, error.

---

## Layout Patterns

### App Shell

```
┌──────────────────────────────────────────────────────────────┐
│ SIDEBAR 240px                │ CONTENT AREA                   │
│ bg-cosmos-950/80             │                                │
│ backdrop-blur-xl             │  TOP BAR (sticky, full width) │
│ border-r border-glass-border │  ──────────────────────────── │
│                              │                                │
│ [nav items]                  │  PAGE CONTENT (scrollable)    │
│                              │                                │
│ [user section]               │                                │
└──────────────────────────────────────────────────────────────┘
```

### Content Area
- Default padding: `p-6` (24px)
- Max width: unconstrained (fills available space)
- Typical inner layout: 2-column grid (main ~60%, sidebar ~40%) for Today and detail screens

### Active Nav State
Sidebar active item:
- Left border accent: `border-l-2 border-amber-glow`
- Background: `bg-glass-strong`
- Text: `text-primary` (full opacity)
- Inactive items: `text-secondary`

---

## Page Transitions

Using Framer Motion:
```tsx
// Standard page transition
<motion.div
  initial={{ opacity: 0, y: 8 }}
  animate={{ opacity: 1, y: 0 }}
  exit={{ opacity: 0, y: -8 }}
  transition={{ duration: 0.2 }}
>
  {/* page content */}
</motion.div>
```

---

## Hover States

- Cards: `hover:bg-glass-hover` (slight brightening)
- Buttons: slight opacity increase
- Nav items: `hover:bg-glass`
- Table rows: `hover:bg-glass-hover`

All hover transitions: `transition-colors duration-150`
