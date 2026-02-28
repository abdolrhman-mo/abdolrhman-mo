# Y Combinator Website — Detailed User Flows Research

> Research date: February 28, 2026

---

## Table of Contents

1. [Login / Authentication Flow](#1-login--authentication-flow)
2. [Profile Update Flow](#2-profile-update-flow)
3. [Application Flow](#3-application-flow)
4. [Key UX Patterns & Takeaways](#4-key-ux-patterns--takeaways)

---

## 1. Login / Authentication Flow

### Entry Points

YC has **three separate login surfaces**, each for a different audience:

| Portal | URL | Audience |
|---|---|---|
| **YC Account** | `account.ycombinator.com` | Applicants & founders |
| **Hacker News** | `news.ycombinator.com/login` | Community members |
| **Bookface** | `bookface.ycombinator.com` | Accepted YC founders only |

### Unified Account System

YC uses a **unified account system** shared between Hacker News (`news.ycombinator.com`) and the YC application portal (`apply.ycombinator.com`). Your Hacker News credentials serve as your login across the entire YC ecosystem — there is **no separate signup** for the application.

### Step-by-Step: New User (No Account)

1. Go to `news.ycombinator.com/login`.
2. Under the **"Create Account"** section (on the same page as login), enter a **username** and **password**.
3. Account is created immediately — no email verification step.
4. Navigate to `apply.ycombinator.com`.
5. Log in with the newly created HN credentials.
6. You're redirected to the application dashboard.

### Step-by-Step: Existing HN User

1. Navigate to `apply.ycombinator.com` (or click "Apply" on ycombinator.com).
2. Enter your existing HN **username** and **password**.
3. Click **Login**.
4. You're redirected to the application dashboard.

### Step-by-Step: Via account.ycombinator.com

1. Navigate to `account.ycombinator.com`.
2. Log in with HN credentials (or create a new account).
3. Access your current and past applications, manage account settings.

### Login Page UI (Hacker News)

The login page is **famously minimalist**:
- **Orange header bar** (#ff6600) with the "Y" logo
- Plain HTML with virtually no CSS styling
- Simple text fields for **username** and **password**
- A **Login** button
- A **"Forgot your password?"** text link
- A **"Create Account"** section with its own username/password fields on the same page
- No images, no branding beyond the header, no social login buttons
- One of the most minimal login interfaces on the modern web

### Authentication Details

- **Method:** Username + password only (no OAuth, no magic links, no social login, no email-based auth)
- **Two-factor authentication (2FA):** Not publicly documented for the applicant portal
- **Session management:** Standard session cookies; no public documentation on session duration
- **Co-founder access:** Co-founders are invited via email and must create their own accounts using the email address entered in the application. Credential conflicts can occur if multiple founders use the same device (YC recommends using incognito/private browser windows).
- **No email verification:** Account creation requires only a username and password — no email confirmation step.

---

## 2. Profile Update Flow

### Context

YC has two profile contexts:

1. **Application-time founder profile** — filled out during the application process
2. **Post-acceptance founder profile** — managed via Bookface (internal YC platform)

### A. Application-Time Founder Profile

Each founder fills out a **Founder Profile Form** that is linked to the company application.

#### Step-by-step:

1. **Primary applicant** creates the application and enters co-founder emails.
2. **Co-founders receive an email** with a link to fill out their own founder profile.
3. The **Founder Profile Form** collects:
   - Full name
   - Email address
   - Phone number
   - Date of birth
   - Education history (schools, degrees, years)
   - Work experience (companies, roles, years)
   - Online profiles (LinkedIn, GitHub, Twitter/X, personal website)
   - Bio / personal statement
4. Founders can **edit their profile** at any time before the application is submitted.
5. After submission, the application enters review and **continuous editing is no longer allowed**.

#### UX Notes:
- The form is straightforward — a **single-page form** with standard input fields.
- Profile data is part of the broader application — there is no standalone "profile settings" page.
- If a co-founder hasn't received the email, the primary applicant can remove and re-add them to trigger a new invitation.

### B. Post-Acceptance Founder Profile (Bookface)

For accepted YC founders, profile management moves to **Bookface** (`bookface.ycombinator.com`):

1. Log in to Bookface.
2. Navigate to profile/settings.
3. Editable fields include:
   - Personal information (name, bio, photo)
   - Company information
   - Founder verification link (can be created at `bookface.ycombinator.com/verify`)
   - Co-founder matching profile visibility settings
4. Founders can **create a verification link** that publicly proves their YC participation.
5. Profile info can be **updated or disabled at any time**.

### C. YC Co-Founder Matching Profile

YC operates the **world's largest co-founder matching platform** (100,000+ matches made):

1. Accessible at `ycombinator.com/cofounder-matching`.
2. Users create a **matching profile** visible only to other approved participants (not public).
3. **Profile fields:**
   - Photo (strongly recommended — profiles with photos get more matches)
   - Video (optional short intro)
   - About yourself / background
   - Your startup idea (YC recommends being open)
   - Skills (product, design, engineering, sales/marketing, operations)
   - Location
   - Co-founder preferences (interests, skills, location — editable on the third page of profile creation)
4. Profile can be **updated at any time** through profile settings.

### D. Key Profile Constraints

- **Only the primary applicant** can edit the Company Application — co-founders can only fill out their own Founder Profiles.
- Founder Profiles are **freely editable before submission**, but **locked after submission**.
- Material changes post-submission (e.g., co-founder changes) can be sent via a special update link provided by YC.

---

## 3. Application Flow

### Overview

The YC application is a **single online form** (not a multi-page wizard). It is one long questionnaire called the "Company Application," plus individual Founder Profile forms for each co-founder.

The form is **dynamic** — certain questions appear or hide based on previous answers (e.g., revenue questions only appear if you indicate you have revenue).

### Step-by-Step Process

#### Step 1: Account Creation / Login
- Go to `ycombinator.com/apply` → redirected to log in.
- Log in with your **Hacker News account** (or create one at `news.ycombinator.com/login` — just username + password, no email verification).
- YC uses a **unified account system** — HN credentials work across all YC properties.

#### Step 2: Start Application
- After logging in, begin a new application.
- Select which **batch** to apply for (e.g., Spring 2026, Summer 2026, or "A batch after [current]" for early decision).

#### Step 3: Fill Out Company Application

The Company Application form contains the following sections and fields:

---

### Section 1: Company Information

| Field | Details |
|---|---|
| **Company name** | Current name of your company/project |
| **Describe what your company does (50 chars)** | Ultra-concise one-liner |
| **Company URL** | Website (if any) |
| **Demo URL** | Link to product/prototype with login credentials if needed |
| **Company category** | Dropdown selection |
| **Where are founders based?** | Location of the team |
| **Where would the company be based after YC?** | Post-batch location |

### Section 2: Legal Entity & Financials

| Field | Details |
|---|---|
| **Have you formed any legal entity yet?** | List all entities, states/countries of formation (e.g., Delaware C Corp, Singapore Pvt Ltd) |
| **Equity ownership breakdown** | Percentages for each founder + title (e.g., CEO), employees, and other stockholders |
| **Have you taken any investment yet?** | Yes/No + details |
| **How much money do you spend per month?** | Monthly burn rate |
| **How much money does your company have in the bank?** | Cash balance |
| **How long is your runway?** | Calculated from cash / burn rate (in months) |
| **Are you currently fundraising?** | Yes/No (are you pitching, taking calls, or accepting investments?) |

### Section 3: Progress & Traction (Conditional Fields)

> This section uses **dynamic/conditional logic**. Questions appear or hide based on your answers.

| Field | Details |
|---|---|
| **What progress have you made?** | Traction data — launch dates, ARR, WAU, MAU, revenue, etc. Stick to facts, not projections. |
| **How long have each of you been working on this?** | Time since first code/conversation/incorporation. How much has been full-time? |
| **How far along are you?** | Stage: idea, prototype, launched, revenue |
| **Are people using your product?** | Yes/No (conditional — if No, asks for a specific launch date instead) |
| **Do you have revenue?** | Yes/No (triggers follow-up) |
| **Revenue for each of the last 6 months** | (Conditional) 6 numeric inputs for calendar months |
| **How many active users/customers? How many paying?** | (Conditional) Who pays you the most and how much? |
| **Anything else regarding revenue or growth rate?** | (Conditional) Free text |

### Section 4: Product & Vision

| Field | Details |
|---|---|
| **What is your company going to make?** | Describe your product and what it does or will do |
| **Why did you pick this idea to work on?** | Domain expertise? How do you know people need this? |
| **Who desperately needs this?** | Target customer / user (replaced the older "How will you make money?" question) |
| **What's new about what you're making?** | What substitutes do people use because it doesn't exist yet? |
| **How do or will you make money? How much could you make?** | Revenue model + potential |
| **How big is the potential market? (TAM)** | Provide a specific number |
| **What do you understand about your business that others don't get?** | Unique insight / competitive advantage backed by data |
| **Who are your competitors? Who might become competitors?** | Name specific companies. Who do you fear most? |

### Section 5: Founder / Team Questions

| Field | Details |
|---|---|
| **Who writes code or does technical work?** | Was any done by a non-founder? |
| **How long have the founders known one another?** | How did you meet? Have any not met in person? |
| **Interesting project created together** | Preferably outside of class or work |
| **Something impressive each founder has built or achieved** | 1-2 sentences per founder. **YC says this is the most important question on the application.** |

### Section 6: Wildcard / Culture Fit

| Field | Details |
|---|---|
| **Time you most successfully hacked a (non-computer) system** | Open-ended. YC looks for unconventional thinkers who "beat the system." Strong answers here can rescue otherwise weak applications. |
| **Tell us something surprising or amusing you discovered** | Shows curiosity and insight |

### Section 7: Other Ideas

| Field | Details |
|---|---|
| **Other ideas you considered applying with** | List format: idea in 50 chars + 1 sentence of context. YC sometimes funds teams to work on an alternate idea. |

### Section 8: Additional Info

| Field | Details |
|---|---|
| **If applying with the same idea as a previous batch, did anything change?** | (Conditional) Only shown if reapplying |
| **If you participated in an incubator/accelerator, tell us about it** | (Conditional) Prior program experience |
| **Is there anything else we should know?** | Catch-all for anything not covered |
| **How did you hear about YC? What convinced you to apply?** | 2-6 sentences. Name anyone who encouraged you; mention YC events attended. |
| **Referral code** | If referred by a YC alum |

### Section 9: Video

| Field | Details |
|---|---|
| **1-minute unlisted YouTube video URL** | Introducing the founders. Optional but **highly recommended** — statistically much more likely to get an interview if you submit one. |

### Section 10: New Fields (2025+)

| Field | Details |
|---|---|
| **AI Safety Disclosure** | 150 characters. E.g., "We fine-tune Llama-3 on proprietary data; no user PII leaves VPC." |
| **Climate Impact Tag** | Optional. Quantify energy savings if applicable. |

---

#### Step 4: Fill Out Founder Profiles

Each co-founder fills out their individual Founder Profile (see Section 2 above).

#### Step 5: Review & Edit

- Applicants can go back and edit any answer before submission.
- The form auto-saves progress.

#### Step 6: Submit

- Click submit. The application enters YC's review pipeline.
- **No further edits** are allowed after submission.

#### Step 7: Wait for Decision

- YC reviews applications and releases interview invitations **in weekly waves** (changed in 2025 — used to be one big batch).
- Applying early is encouraged — you can get a response in ~10 days vs. ~10 weeks.
- If submitted before the on-time deadline, decision arrives by a specific date (e.g., March 13 for Spring 2026).
- Late applications are still accepted but with no guaranteed response timeline.

#### Step 8: Interview (If Selected)

- **10-minute video interview** with YC partners.
- Short and direct — covers your idea, traction, team, and market.
- Funding decisions are made **immediately after** interviews.

#### Step 9: Join the Batch

- 3-month program in San Francisco.
- Group office hours every 2 weeks.
- 1-on-1 partner office hours as needed.
- Weekly expert talks (founders, VCs, tech executives).
- Culminates in **Demo Day** (~10 weeks in).

### What You Receive

- **$500K in funding** via two SAFEs:
  - $125K on standard post-money SAFE
  - $375K on uncapped SAFE with MFN (Most Favored Nation) provision
- Mentorship from YC partners
- Demo Day investor access
- Lifetime alumni network with perks, credits, and ongoing support

---

## 4. Key UX Patterns & Takeaways

### Authentication
- **Minimal friction:** Username + password only via Hacker News accounts. No OAuth, no email verification, no social login.
- **Unified account system:** One account works across HN, application portal, and account settings.
- **Separate portals** for different user types (applicants vs. community vs. accepted founders).
- **No 2FA** for applicants (reduces friction for a one-time application).
- **Famously minimalist UI** — plain HTML, no styling, no images.

### Application Form
- **Single long form** — not a multi-step wizard. All questions on one page.
- **Dynamic/conditional fields** — questions show/hide based on answers (e.g., revenue details only if you have revenue).
- **Auto-save** — progress is saved automatically.
- **Character limits enforced** — forces conciseness (50 chars, 150 chars, 200 chars for different fields).
- **Co-founder collaboration** — primary applicant starts, co-founders are invited by email to fill their own profiles independently.
- **No continuous editing** after submission — creates urgency to get it right before submitting.

### Profile Management
- **Application-time:** Profile is part of the application flow, not a separate settings page.
- **Post-acceptance:** Full profile management moves to Bookface (internal platform).
- **Verification system:** Founders can generate public verification links.

### Design Philosophy
- **Simplicity over polish** — YC values substance. The application UI is clean and functional, not flashy.
- **Conciseness is enforced** — character limits on nearly every field.
- **Low barrier to entry** — anyone can create an account and apply. No gatekeeping before the application.
- **Batch model** — applications are tied to specific batches, creating natural deadlines and cohort structure.

---

## Sources

- [Y Combinator — Apply](https://www.ycombinator.com/apply)
- [Y Combinator — How to Apply](https://www.ycombinator.com/howtoapply)
- [Y Combinator — FAQ](https://www.ycombinator.com/faq)
- [Y Combinator — Interview Guide](https://www.ycombinator.com/interviews)
- [YC Application Guide (Leland)](https://www.joinleland.com/library/a/yc-application)
- [YC Application Questions Template (Peak Digital Studio)](https://www.peakdigitalstudio.com/articles/yc-application-questions-template)
- [YC Application Breakdown (Nick Raushenbush)](https://www.nickraushenbush.com/y-combinator-application-breakdown-and-guide/)
- [YC Application Tips 2025 (Flowjam)](https://www.flowjam.com/blog/yc-application-tips-2025)
- [How to Apply to YC (Walturn)](https://www.walturn.com/insights/how-to-apply-for-y-combinator-a-comprehensive-guide)
- [How to Apply to YC — 2026 Guide (WeAreFounders)](https://www.wearefounders.uk/how-to-apply-to-y-combinator-your-complete-guide-to-the-fall-2025-batch/)
- [Apply to YC Accelerator (XRaise)](https://xraise.ai/blog/apply-to-y-combinator-accelerator-2025-2026/)
- [YC Application Deadline Dates (Zyner.io)](https://zyner.io/blog/yc-application-deadline)
- [32 Successful YC Application Examples (Shizune)](https://shizune.co/yc-application-examples)
- [How to Get Into YC: Full F25 Application Pack](https://www.productmarketfit.tech/p/how-to-get-into-yc-the-full-f25-application)
- [YC Application Guide: Tips to Stand Out (Inkle)](https://www.inkle.ai/blog/how-to-get-into-y-combinator)
- [The YC Application Procedure (Medium — Shivalik Sen)](https://medium.com/@shvlksen/the-ycombinator-application-procedure-or-how-we-almost-made-it-part-1-of-2-5bb2b84d7144)
- [Our YC F24 Application (Medium — Rohan Balkondekar)](https://medium.com/@rohanbalkondekar/our-yc-f24-application-6798b41a2fde)
- [Y-Combinator Application Guide (GitHub)](https://github.com/rohitdotmittal/Y-Combinator-application-and-interviews-guide)
- [YC Co-Founder Matching](https://www.ycombinator.com/cofounder-matching)
- [How to Make Your Co-Founder Profile Stand Out (YC Library)](https://www.ycombinator.com/library/Dw-how-to-make-your-co-founder-matching-profile-stand-out)
- [YC Founder Verification](https://www.ycombinator.com/verify)
- [Hacker News Login](https://news.ycombinator.com/login)
- [YC Account Portal](https://account.ycombinator.com/)
