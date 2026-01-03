# 🧭 SubSentry — OpenCode Issues Master (25 Issues, Fully Expanded)

This document defines **all OpenCode issues for SubSentry** in a **highly descriptive, mentor-style format**, structured **week-wise** to respect **weekly point limits** and ensure smooth progress till the end of OpenCode (31st).

## 🗓️ WEEK 1 — Onboarding & Foundations (75 points)

### 🎯 Week Goal (Very Important)

Week 1 is about **setting the base correctly**. The intention is _not_ speed, but **clarity and correctness**. By the end of this week:

- Every contributor should be comfortable with the repo structure
- The project should run locally without hacks
- Authentication and database connectivity should be correctly wired

A strong Week 1 ensures the rest of OpenCode runs smoothly.

---

### Issue 0: Contributor Onboarding

**Points:** 5
**Labels:** `good first issue`, `documentation`, `OpenCode`

**Expanded Description:**
This issue exists to onboard contributors into the SubSentry codebase and the OpenCode workflow. It deliberately avoids technical complexity and focuses instead on understanding how collaboration works in a real open-source project.

Contributors will add their name, GitHub profile, and a short professional bio to `CONTRIBUTORS.md`. This also acts as a public acknowledgment of their participation.

**Why this issue exists:**

- Reduces anxiety for first-time contributors
- Ensures everyone understands PR workflow early
- Builds a sense of ownership and community

**What NOT to do:**

- Do not edit other contributors’ entries
- Do not change formatting
- Do not include unnecessary personal information

**Acceptance Expectations:**

- Only `CONTRIBUTORS.md` is modified
- Entry follows the exact format
- One PR per contributor

---

### Issue 1: Setup Next.js with Clerk Authentication

**Points:** 30
**Labels:** `frontend`, `auth`

**Expanded Description:**
This issue sets up the **frontend foundation** of SubSentry. Contributors will initialize a Next.js application using the App Router and integrate Clerk for authentication.

The goal is to ensure that:

- Users can sign up and sign in
- Authentication state is handled cleanly
- Protected routes (like the dashboard) are inaccessible without login

**Why this issue exists:**
Authentication is non-negotiable in real-world products. This issue introduces contributors to industry-grade auth flows instead of mock or local-only solutions.

**Key Expectations:**

- Proper ClerkProvider setup
- Middleware-based route protection
- No auth logic inside UI components

**Common mistakes to avoid:**

- Hardcoding auth checks
- Skipping middleware
- Leaving dashboard publicly accessible

---

### Issue 2: Setup Express Server with MongoDB

**Points:** 30
**Labels:** `backend`

**Expanded Description:**
This issue establishes the **backend backbone** of SubSentry. Contributors will initialize an Express server, configure environment variables, and connect the application to MongoDB using Mongoose.

The focus here is **stability and clarity**, not feature development.

**Why this issue exists:**

- Every feature depends on a reliable backend
- Prevents rushed, messy backend setup later

**Key Expectations:**

- Clean server entry point
- Proper error handling for DB connection
- No credentials hardcoded in code

**What NOT to do:**

- Commit `.env` files
- Ignore connection errors

---

### Issue 3: Subscription Database Schema

**Points:** 10
**Labels:** `backend`, `database`

**Expanded Description:**
This issue focuses on designing the **core data model** for SubSentry. Contributors will define a subscription schema that supports real-world use cases like recurring billing, trials, renewals, and multiple data sources.

**Why this issue exists:**

- Poor schema design causes long-term problems
- A clean schema enables all future features

**Key Expectations:**

- Fields for billing cycle, renewal date, trial status, source, and user ownership
- Use of timestamps
- Extensible design (easy to add fields later)

**What NOT to do:**

- Overengineering
- Adding unrelated fields

---

**🟢 Week 1 Total: 75 points**

---

## 🗓️ WEEK 2 — Core CRUD & Layout (75 points)

### 🎯 Week Goal (Very Important)

Week 2 is about **making the application useful**. By the end of this week, users should be able to **create and view real subscription data** through a basic but functional dashboard.

This week connects the foundations built in Week 1 to actual user-facing functionality.

---

### Issue 4: Constants & Enums Setup

**Points:** 10
**Labels:** `refactor`
**Date:** 2025-12-27

**Expanded Description:**
This issue focuses on improving code quality early by removing hardcoded strings and values related to subscription categories and billing cycles.

Contributors will centralize these values into constants or enums so they can be reused consistently across frontend and backend.

**Why this issue exists:**

- Prevents bugs caused by mismatched strings
- Makes future features easier to add
- Encourages clean architecture practices

**Key Expectations:**

- Single source of truth for constants
- Used wherever applicable
    
**What NOT to do:**

- Duplicate constants across files
- Keep magic strings in components or controllers

---

### Issue 5: Create Subscription API (POST)

**Points:** 25
**Labels:** `backend`, `api`
**Date:** 2025-12-29

**Expanded Description:**
This issue implements the first core backend feature: allowing users to add subscriptions to the system.

The API should accept subscription details, validate them, and store them in the database while ensuring the data belongs only to the authenticated user.

**Why this issue exists:**

- Enables all future subscription-based features
- Introduces secure, user-scoped APIs

**Key Expectations:**

- Proper request validation
- User-based data isolation
- Meaningful error responses

**What NOT to do:**

- Allow unauthenticated access
- Trust client-provided user IDs

---

### Issue 6: Fetch Subscriptions API (GET)

**Points:** 20
**Labels:** `backend`, `api`
**Date:** 2026-01-01

**Expanded Description:**
This issue allows users to retrieve all of their subscriptions from the backend.

The API should return only the subscriptions belonging to the currently authenticated user and support clean, predictable response structures.

**Why this issue exists:**

- Forms the backbone of the dashboard
- Teaches safe data retrieval practices

**Key Expectations:**

- Secure user-based filtering
- Stable response format

**What NOT to do:**

- Return data for other users
- Over-fetch unnecessary fields

---

### Issue 7: Basic Dashboard Layout

**Points:** 20
**Labels:** `frontend`, `ui`
**Date:** 2026-01-03

**Expanded Description:**
This issue focuses on building the structural UI of the application.

Contributors will create a basic dashboard layout with navigation and a content area that will later host subscription listings, analytics, and ingestion features.

**Why this issue exists:**

- Provides a consistent user experience
- Prevents layout rewrites later

**Key Expectations:**   

- Responsive layout
- Clean separation of layout and content

**What NOT to do:**

- Hardcode feature-specific UI
- Over-style at this stage

---

**🟢 Week 2 Total: 75 points**

---

## 🗓️ WEEK 3 — UI Integration & Insights (75 points)

### 🎯 Week Goal (Very Important)

Week 3 is about **making SubSentry feel like a real product**, not just an API playground.

By the end of this week:

- Frontend and backend should be fully connected
- Users should be able to manage subscriptions end‑to‑end
- The dashboard should clearly communicate information, not just display data

This week focuses on **usability, correctness, and confidence**.

---

### Issue 8: Subscription Listing UI

**Points:** 25
**Labels:** `frontend`, `ui`
**Date:** 2026-01-06

**Expanded Description:**
This issue builds the primary screen users will interact with: the subscription list. Contributors will fetch subscription data from the backend and present it in a clean, readable, and responsive UI.

The goal is clarity — users should instantly understand what subscriptions they have, how much they cost, and when they renew.

**Why this issue exists:**

- This is the core dashboard experience
- Poor listing UX makes the app unusable

**Key Expectations:**

- Fetch data using the GET subscriptions API
- Display name, amount, billing cycle, category, renewal date
- Clearly indicate trials vs paid subscriptions
- Responsive layout for smaller screens

**What NOT to do:**

- Dump raw JSON on screen
- Hide important information behind clicks
- Hardcode dummy data

---

### Issue 9: Add Subscription Form UI

**Points:** 20
**Labels:** `frontend`, `forms`
**Date:** 2026-01-08

**Expanded Description:**
This issue allows users to manually add subscriptions through a structured form.

The form should guide users toward correct input and prevent common mistakes such as missing required fields or invalid amounts.

**Why this issue exists:**

- Manual entry is the primary way users add subscriptions initially
- Good forms reduce backend errors

**Key Expectations:**

- Controlled inputs with basic validation
- Clear labels and placeholders
- Form submission connected to POST API

**What NOT to do:**

- Allow submission with empty required fields
- Reload the entire page on submit

---

### Issue 10: Edit Subscription UI

**Points:** 15
**Labels:** `frontend`
**Date:** 2026-01-11

**Expanded Description:**
This issue enables users to update existing subscriptions when details change, such as price increases or plan upgrades.

Editing should feel safe and predictable, with existing data prefilled for clarity.

**Why this issue exists:**

- Subscriptions change over time
- Users need control over their data

**Key Expectations:**

- Prefill existing subscription data
- Update using PUT API
- UI reflects changes immediately

**What NOT to do:**

- Force users to re-enter all fields
- Create duplicate subscriptions

---

### Issue 11: Delete Subscription UI

**Points:** 15
**Labels:** `frontend`
**Date:** 2026-01-13

**Expanded Description:**
This issue focuses on safe deletion of subscriptions.

Accidental deletions can seriously harm user trust, so confirmation is required.

**Why this issue exists:**

- Prevents irreversible mistakes
- Aligns with real-world UX patterns

**Key Expectations:**

- Confirmation dialog before deletion
- Call DELETE API only after confirmation
- Update UI immediately after deletion

**What NOT to do:**

- Delete without warning
- Leave stale UI state

---

**🟢 Week 3 Total: 75 points**

---

## 🗓️ WEEK 4 — Analytics & Experience (75 points)

### 🎯 Week Goal (Very Important)

Week 4 is about **turning raw data into meaningful insight**.

By the end of this week:

- Users should understand _where their money is going_
- The dashboard should answer questions, not just show numbers
- SubSentry should clearly differentiate itself from a basic CRUD app

This week is especially important from a **judge and user-value perspective**.

---

### Issue 12: Monthly Spend Calculation

**Points:** 20
**Labels:** `backend`, `logic`
**Date:** 2026-01-16

**Expanded Description:**
This issue focuses on calculating the **effective monthly spend** across all subscriptions, even when billing cycles differ (monthly vs yearly).

Contributors will normalize all subscriptions to a monthly value so users can understand their recurring financial commitment at a glance.

**Why this issue exists:**

- Users think in monthly budgets
- Raw subscription data is not meaningful without aggregation

**Key Expectations:**

- Convert yearly plans into monthly equivalents
- Ignore inactive or invalid subscriptions
- Handle edge cases gracefully (empty list, zero values)

**What NOT to do:**

- Hardcode assumptions
- Mix calculation logic into controllers unnecessarily

---

### Issue 13: Yearly Spend Calculation

**Points:** 15
**Labels:** `backend`, `logic`
**Date:** 2026-01-18

**Expanded Description:**
This issue complements monthly spend by calculating the **total yearly cost** of all subscriptions.

The yearly view helps users understand long-term financial impact rather than short-term cash flow.

**Why this issue exists:**

- Long-term planning matters
- Encourages conscious subscription management

**Key Expectations:**

- Accurate yearly aggregation
- Clear separation from monthly logic

**What NOT to do:**

- Duplicate monthly logic blindly
- Ignore billing cycle differences

---

### Issue 14: Dashboard Summary Widgets

**Points:** 20
**Labels:** `dashboard`
**Date:** 2026-01-21

**Expanded Description:**
This issue introduces high-level summary widgets at the top of the dashboard.

These widgets should provide **instant insight** without requiring users to scroll or analyze tables.

**Why this issue exists:**

- Users want quick answers
- Dashboards should surface key metrics immediately

**Key Expectations:**

- Total monthly spend
- Total active subscriptions
- Number of free trials
- Clean, minimal visual design

**What NOT to do:**

- Overcrowd the dashboard
- Use placeholder or hardcoded values

---

### Issue 15: Upcoming Renewals Section

**Points:** 20
**Labels:** `frontend`
**Date:** 2026-01-23

**Expanded Description:**
This issue highlights subscriptions that are renewing soon, helping users avoid surprise charges.

Subscriptions renewing in the near future (e.g., next 7–30 days) should be visually distinguished.

**Why this issue exists:**

- Surprise charges damage trust
- Proactive alerts increase product value

**Key Expectations:**

- Sort subscriptions by renewal date
- Highlight imminent renewals
- Clear date formatting

**What NOT to do:**

- Hardcode date ranges
- Ignore timezone considerations

---

**🟢 Week 4 Total: 75 points**

---

## 🗓️ WEEK 5 — Email Ingestion & Final Polish (75 points)

### 🎯 Week Goal (Very Important)

Week 5 is the **most sensitive and high-impact week** of the project.

The goal here is **automation + trust**:

- Automate subscription detection via Gmail **without violating user privacy**
- Ensure the application feels complete, stable, and demo-ready
- Avoid risky shortcuts that could compromise security or user confidence

This week is where SubSentry clearly stands out as more than a manual tracker.

---

### Issue 16: Gmail OAuth (Read-only)

**Points:** 30
**Labels:** `backend`, `oauth`
**Date:** 2026-01-26

**Expanded Description:**
This issue introduces Gmail integration by implementing OAuth authentication using the **strictly read-only** Gmail scope (`gmail.readonly`).

Contributors must ensure users can safely connect their Gmail account to SubSentry without granting write, delete, or send permissions.

**Why this issue exists:**

- Email-based automation is a core differentiator
- User trust depends on strict permission control

**Key Expectations:**

- OAuth flow using Google APIs
- Read-only scope enforced
- Tokens stored securely
- Clear error handling for auth failures

**What NOT to do:**

- Request broader Gmail scopes
- Log access tokens or email content
- Hardcode OAuth credentials

---

### Issue 17: Fetch Transactional Emails

**Points:** 20
**Labels:** `backend`
**Date:** 2026-01-28

**Expanded Description:**
This issue focuses on fetching emails that are likely related to subscriptions, invoices, payments, or renewals.

Rather than processing the entire inbox, contributors should intelligently filter relevant emails using search queries and metadata.

**Why this issue exists:**

- Reduces unnecessary processing
- Improves performance and accuracy

**Key Expectations:**

- Use Gmail search queries (keywords like invoice, subscription, renewal)
- Fetch minimal required metadata
- Handle empty or limited inbox cases gracefully

**What NOT to do:**

- Fetch entire inbox blindly
- Store raw email bodies unnecessarily

---

### Issue 18: Parse Emails for Subscription Data

**Points:** 15
**Labels:** `backend`, `parsing`
**Date:** 2026-01-31

**Expanded Description:**
This issue extracts meaningful subscription information from fetched emails using **simple, rule-based parsing**.

The goal is not perfect accuracy, but **reasonable detection** that can later be corrected by users.

**Why this issue exists:**

- Automation reduces manual effort
- Rule-based parsing keeps complexity manageable

**Key Expectations:**

- Extract service/merchant name
- Detect amount and billing hints
- Gracefully handle parsing failures

**What NOT to do:**

- Overfit logic to specific vendors
- Use fragile regex-heavy solutions

---

### Issue 19: Save Email-based Subscriptions

**Points:** 10
**Labels:** `backend`
**Date:** 2026-02-02

**Expanded Description:**
This issue converts parsed email data into valid subscription records stored in the database.

Contributors must ensure duplicates are avoided and email-sourced subscriptions are clearly marked.

**Why this issue exists:**

- Bridges automation with existing subscription system
- Prevents duplicate or confusing data

**Key Expectations:**

- Map parsed data to schema
- Set source = `email`
- Deduplicate intelligently

**What NOT to do:**

- Overwrite user-created subscriptions
- Create duplicates blindly

---

### Issue 20: Email Ingestion UI Feedback

**Points:** 10
**Labels:** `frontend`
**Date:** 2026-02-05

**Expanded Description:**
This issue ensures users clearly understand what happens during email ingestion.

The UI should communicate progress, success, and failures transparently.

**Why this issue exists:**

- Email ingestion can feel scary
- Transparency builds trust

**Key Expectations:**

- Loading indicators during ingestion
- Clear success/error messages
- No silent failures

**What NOT to do:**

- Freeze the UI
- Hide errors from users

---

### Issue 21: Free Trial Highlighting

**Points:** 10
**Labels:** `frontend`
**Date:** 2026-02-07

**Expanded Description:**
This issue visually distinguishes free trials from paid subscriptions and highlights trial end dates.

**Why this issue exists:**

- Free trials are easy to forget
- Users want to avoid unintended charges

**Key Expectations:**

- Clear visual indicators
- Accurate trial end display

---

### Issue 22: Filters & Sorting

**Points:** 10
**Labels:** `frontend`
**Date:** 2026-02-10

**Expanded Description:**
This issue improves usability by allowing users to filter subscriptions by category and sort them by renewal date or price.

**Why this issue exists:**

- Improves navigation for users with many subscriptions

**Key Expectations:**

- Client-side filtering and sorting
- No additional backend load

---

### Issue 23: Final UI Polish

**Points:** 10
**Labels:** `ui`
**Date:** 2026-02-12

**Expanded Description:**
This issue focuses on visual and interaction polish across the application.

Contributors should fix spacing, alignment, responsiveness, and minor UX inconsistencies.

**Why this issue exists:**

- Polish impacts first impressions
- Judges notice UI consistency

---

### Issue 24: Documentation Improvements

**Points:** 10
**Labels:** `documentation`
**Date:** 2026-02-15

**Expanded Description:**
This issue improves the clarity and completeness of project documentation.

Contributors should enhance setup instructions, add screenshots, and clarify usage where needed.

**Why this issue exists:**

- Good docs reduce confusion
- Improves onboarding for future contributors

---

### Issue 25: Final Bug Fixes & Cleanup

**Points:** 10
**Labels:** `maintenance`
**Date:** 2026-02-17

**Expanded Description:**
This issue is reserved for stabilizing the project before submission.

Contributors will fix minor bugs, remove debug logs, and ensure the app is production-ready.

**Why this issue exists:**

- Prevents last-minute surprises
- Ensures smooth demo experience

---

**🟢 Week 5 Total: 75 points**

---

## ✅ Final Outcome

If all issues are completed:

- SubSentry will be **feature-complete**
- Weekly and per-issue point rules respected
- Contributors gain real-world experience
- Project ready for demo, judging, and future expansion

---

🛡️ **Maintainer Tip:** Release issues strictly week-wise to prevent point overflow and confusion.
