## Hi, I'm Mehmet Cebe

I build products end to end: database, backend, frontend, payments, and the mobile release pipeline. I'm looking for a **software engineering internship or a junior full-stack role**.

Most of the projects below live in private repositories because they're commercial products or apps I'm getting ready to launch. I'm happy to share my screen and walk through any of the code in an interview.

I use AI coding tools like Claude Code every day. I review and test everything they produce, and I can walk you through the reasoning behind each design decision in these projects.

**Contact:** cebemehmet030@gmail.com

---

### GeoVisibilityTool: AI search visibility SaaS · [geovisibilitytool.com](https://www.geovisibilitytool.com)

Tracks how often a brand gets mentioned, ranked and cited when people ask ChatGPT, Perplexity, Gemini and Claude about its market. It then turns every gap it finds into a concrete fix: a content brief, JSON-LD markup, an `llms.txt` file, or a list of sources worth getting cited on.

- **Multi-tenant Postgres with row-level security** on every tenant table. The org-isolation tests were written before any dashboard UI, and the isolation was also checked against the production database.
- **Postgres is the job queue.** Scheduled checks fan out into work items claimed with `FOR UPDATE SKIP LOCKED`. A shared response cache and per-org spend caps keep LLM costs inside a written cost model, and a unit test fails if the plan limits break it.
- **One adapter per AI engine** behind a shared interface, tested against recorded fixtures instead of live APIs.
- **Deterministic analysis first.** Brand mentions are found by alias matching and citations are classified by domain. A model is called once per answer, and only for what needs judgment (position, sentiment, competitors).
- Stripe subscriptions with a signature-verified webhook as the only writer of billing state, plus Clerk auth, Resend email, and a free public audit page protected by rate limits and a daily spend cap.
- **800+ automated tests** (Vitest unit tests and Playwright end-to-end tests).

`Next.js 16` `TypeScript` `Postgres` `Drizzle ORM` `Clerk` `Stripe` `Vercel AI SDK` `Vitest` `Playwright`
*Status: live, private repo. Google AI Overviews tracking is next.*

### CVAnalyze: AI resume analyzer · [cvanalyze.com](https://cvanalyze.com)

Upload a PDF or DOCX resume and get an ATS compatibility score, section-by-section feedback, rewrite suggestions, cover letters, and a match analysis against a job posting.

- Claude does the analysis. Long jobs run in the background on Inngest so the request never hangs.
- Every signup gets a 7-day Pro trial from a Postgres trigger, and the effective plan is resolved on the server.
- Subscriptions run through Creem: hosted checkout, verified webhooks, customer portal.
- Supabase handles auth and storage, with ordered SQL migrations. Transactional email goes through Resend.

`Next.js 16` `React 19` `Supabase` `Claude API` `Inngest` `Creem` `Resend` `Vitest`
*Status: live, private repo.*

### Watt Payı: electricity bill splitter (iOS & Android)

A Turkish-language app. You photograph your electricity bill, pick the appliances you own, and see roughly what each one costs you.

- A Supabase Edge Function sends the bill photo to Claude and extracts the amounts as structured data, with input validation on the image upload.
- The estimates get better over time: a ridge-regularized regression with recency weighting learns a correction factor for each appliance from your bill history.
- One React codebase ships to iOS and Android through Capacitor, with native builds automated on Codemagic.

`React` `TypeScript` `Capacitor` `Supabase Edge Functions` `Claude API` `Codemagic` `Vitest`
*Status: in closed beta, private repo.*

### Before & After Pro · [live](https://before-after-site-ten.vercel.app) · [source](https://github.com/Mehmetpo/before-after-site)

A browser tool for comparing two images with a slider. It can export the comparison as a GIF, generate an embeddable widget, and run image enhancement in a Web Worker so the UI stays responsive.

`React 19` `Vite` `TypeScript` `Web Workers` `Vitest`

### Smaller projects

- **[HealthCalcs](https://healthcalcs.org):** health calculators (BMI, calories, macros, body fat, one-rep max). I spent most of the time on technical SEO: schema.org markup, a real sitemap, and FAQ content built around what people actually search for.
- **[Verdant](https://github.com/Mehmetpo/verdant):** a plant care app that identifies a plant from a photo using Gemini. React and Capacitor. Still in progress.

---

### What I work with

- **Languages:** TypeScript, JavaScript, SQL
- **Frontend:** React, Next.js, Tailwind CSS, shadcn/ui
- **Backend & data:** Postgres, Supabase, Drizzle ORM, Edge Functions, background jobs (Inngest, Postgres queues)
- **Mobile:** Capacitor (iOS & Android), Codemagic
- **AI:** Claude API, Vercel AI SDK, Gemini
- **Payments:** Stripe, Creem
- **Testing:** Vitest, Playwright, Testing Library
