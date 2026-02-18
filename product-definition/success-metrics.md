# Success Metrics — MVP

## Purpose

Defines what "success" means for the Continuum MVP. These metrics guide product decisions during and after launch — what to optimize for, what signals tell us the product is working, and what would tell us it's not.

---

## North Star Metric

> **Weekly Active Sessions per Paying User**

A user who talks to the coach regularly is building career capital. Everything else (resumes, pipeline, readiness) follows from that. If this number is healthy, the product is doing its job.

**Target (at 30 days post-launch):** ≥ 2 sessions/week per paying user

---

## Tier 1 — Core Health Metrics

These are the primary signals. Tracked weekly.

### 1. Free → Paid Conversion Rate
**Definition:** % of users who hit the paywall and subscribe
**Why it matters:** Validates that the free experience creates enough value to justify payment
**Target:** ≥ 20% of users who reach the paywall
**Red flag:** < 10%

### 2. Weekly Active Sessions (paying users)
**Definition:** Average coaching sessions per paying user per week
**Why it matters:** Sessions = career capital being built. No sessions = churn risk.
**Target:** ≥ 2 sessions/week
**Red flag:** < 1 session/week at 30 days

### 3. D30 Retention (mobile)
**Definition:** % of new users who open the mobile app on day 30
**Why it matters:** Career prep is a long game. Retention = product is creating a habit.
**Target:** ≥ 30%
**Red flag:** < 15%

### 4. Time to First XYZ/STARL (mobile)
**Definition:** Time from first session start to first extracted item (XYZ or STARL) in Career Profile
**Why it matters:** "First value moment" — user feels something was accomplished
**Target:** Within first session (< 30 minutes from session start)
**Red flag:** < 50% of users get first item in first session

### 5. Web Activation Rate
**Definition:** % of mobile users who also open the web platform within 7 days
**Why it matters:** The web is where career capital becomes job search assets. Low web activation = broken flywheel.
**Target:** ≥ 60% of paying mobile users
**Red flag:** < 30%

---

## Tier 2 — Engagement Quality Metrics

These go deeper into whether users are getting real value. Tracked monthly.

### 6. Career Profile Richness (at 30 days)
**Definition:** Average XYZ count + STARL count per paying user at day 30
**Why it matters:** Profile richness = accumulated value = retention moat
**Target:** ≥ 5 XYZ + ≥ 3 STARL per user at day 30
**Red flag:** < 2 XYZ per user at day 30

### 7. Market Readiness Progression
**Definition:** Average Market Readiness score at day 30 vs. day 1
**Why it matters:** Visible progress = motivation to continue
**Target:** +15–20% improvement in 30 days for active users
**Calculation:** Available only once we have real user data (not demo)

### 8. Resume Version Created Rate
**Definition:** % of paying users who create at least 1 resume version within 30 days
**Why it matters:** Resume creation is the primary tangible output. If users aren't making resumes, they're not getting the core value.
**Target:** ≥ 50% of paying users within 30 days
**Red flag:** < 20%

### 9. Voice Inbox → Career Profile Flow Rate
**Definition:** % of Voice Inbox items that end up in XYZ or STARL bank (not archived/ignored)
**Why it matters:** If extracted items are being dismissed, the AI extraction quality is poor
**Target:** ≥ 70% of extracted items retained
**Red flag:** < 40%

### 10. Session Length (average)
**Definition:** Average duration of a completed coaching session
**Why it matters:** Too short = coach not engaging; too long = friction. Optimal = 15–25 min.
**Target:** 15–25 minutes average
**Signals:** < 5 min = abandonment, > 40 min = possible UX issue

---

## Tier 3 — Business Metrics

Tracked monthly, primary focus post-PMF.

### 11. MRR (Monthly Recurring Revenue)
**Definition:** Total active subscriptions × price
**Target:** Set once pricing is defined
**Early signal:** Trending direction matters more than absolute number in MVP

### 12. Churn Rate (monthly)
**Definition:** % of paying subscribers who cancel per month
**Target:** < 5% monthly churn
**Red flag:** > 10% monthly churn (means product isn't sticky)

### 13. Payback Period
**Definition:** Months to recover CAC from subscription revenue
**Target:** < 6 months
**Requires:** Knowing CAC, which requires marketing spend data

---

## Leading Indicators of Churn

These are early warning signs that a user is about to churn. Track these for intervention triggers.

| Signal | Threshold | Response |
|---|---|---|
| No session in 7 days (paying user) | 7 days | Push notification: "Your coach misses you" |
| No session in 14 days | 14 days | Email re-engagement |
| Market Readiness stagnant for 2 weeks | 14 days | "Next Best Step" push |
| No web open in 30 days | 30 days | Email: "You have N items waiting in your workspace" |
| 0 XYZ in bank at day 7 | day 7 | In-app prompt to send voice prompts to mobile |

---

## What Invalidates MVP

The MVP fails (requires fundamental pivot) if:

1. **Free → Paid conversion < 5%** — product isn't demonstrating value in free session
2. **D30 retention < 10%** — no habit formation, likely UX or value proposition issue
3. **< 30% of users get first XYZ in first session** — core extraction mechanism broken
4. **Average session length < 5 min** — users are not engaging with the coach

---

## Measurement Notes

### What we can measure immediately (MVP)
- Session count, length (mobile)
- Items extracted per session (backend)
- Career Profile richness (backend)
- Web open rate (analytics)
- Paywall hit / conversion (backend + payments)

### What requires more instrumentation
- Market Readiness progression (requires baseline at signup)
- Voice Inbox retention rate (requires item status tracking)
- Resume version creation rate (backend event)

### What we cannot easily measure in MVP
- Actual job outcomes (did user get an offer?)
- Resume quality (subjective)
- Interview performance improvement

> **Note:** Job outcomes (time to offer, offer quality) are the ultimate North Star, but they're lagging indicators with 3–12 month timelines. For MVP, we proxy with engagement and output metrics.

---

## Reporting Cadence

| Metric | Frequency | Owner |
|---|---|---|
| Weekly active sessions | Weekly | Product |
| Free → paid conversion | Weekly | Product + Business |
| D7 / D30 retention | Monthly | Product |
| Career Profile richness | Monthly | Product |
| MRR / Churn | Monthly | Business |
| Churn leading indicators | Daily (automated alerts) | Product |
