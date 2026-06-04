# Benjamin S. Petty

> Senior Software Engineer & Founder · Pacific Northwest

Senior software engineer with 24+ years building products end-to-end — currently designing, building, and operating production systems across four independent Pacific Northwest brands; previously senior engineer at Tomorrow (acq. Ethos Life), Crowd Cow, and U.S. LawShield. **Open to senior engineering roles and contract/fractional engagements.**

## Currently building

| Venture | Role | Since | |
|---|---|---|---|
| **Audeos.fm** | Founder & Engineer | 2026 | [audeos.com](https://audeos.com) |
| **Northwest Local Cannabis** | Co-Founder | 2021 | [nw-local.com](https://nw-local.com) |
| **The North West Clothing** | Founder | 2001 | [nwclothing.com](https://nwclothing.com) |
| **Rooted Community** | Engineer | 2024 | [rootedcommunity.org](https://rootedcommunity.org) |

[**ben-petty.com**](https://ben-petty.com/)

---

<details>
<summary>Full resume</summary>

## Current Ventures · 2021–Present

### Audeos.fm · Founder & Engineer · 2026–Present
[audeos.com](https://audeos.com) · [audeos.fm](https://audeos.fm)

Multi-channel live-streaming radio platform. Each channel loops a curated playlist of
pre-transcoded audio, broadcast in sync to every listener.

- Realtime engine on Phoenix LiveView: a GenServer-per-channel state machine with
  PubSub fan-out keeps every listener synced to the same audio segment in real time.
- HLS pipeline with resumable transcode checkpointing: ffmpeg converts uploads into
  rolling segments across four bitrate variants (Cloudflare R2 storage, MediaMTX RTMP
  relay, Oban workers for transcode/cleanup/backups); on interruption, retry probes R2
  segment counts across all variants and resumes from the safe overlap point, keeping
  every ladder in sync through partial failures.
- Custom Oban phantom-slot reconciler (GenServer) that reconciles in-memory producer
  state against the database in both directions — written after a production incident
  where Oban's built-in Lifeline plugin rescued still-running jobs.
- Production operations: AWS SES/SNS email with SSRF-hardened X.509 webhook
  verification; privacy-by-design analytics (MaxMind country resolution at write time,
  raw IP discarded); self-serve GDPR export/delete; and a postmortem-driven invariants
  doc (15+ documented failure modes) backing telemetry-driven incident response on Fly.io.
- Marketing site (audeos.com), Next.js 16 / React 19 on Turbopack: snapshot-gated
  Spotify caching and promise-level Contentful memoization (~200 API calls → 3 per
  build); post-deploy CI runs a sitemap crawl, link-check, Lychee scan, and Lighthouse
  audits (SEO ≥90, a11y ≥90) on every merge; OpenTofu owns the site's DNS and DMARC.
- **Stack:** Elixir · Phoenix · LiveView · Bandit · Postgres · Oban · Cloudflare R2 ·
  MediaMTX · AWS SES/SNS · MaxMind · Sentry · OpenTofu · Fly.io · Next.js · React ·
  Turbopack · Contentful

### Northwest Local Cannabis · Co-Founder · 2021–Present
[nw-local.com](https://nw-local.com)

Co-founder of Northwest Local Cannabis, a WA i502 licensed craft cannabis
producer/processor. Cultivator-operator across grow, tech, brand, and distribution.

- Astro 6 SSG with Sanity CMS as single source of truth for strains, products, blog
  posts, retailer partners, and site settings; deployed to GitHub Pages.
- Typed Schema.org JSON-LD factory emitting Organization / Product / Article /
  BreadcrumbList structured data per page, with a Portable-Text→plaintext extractor.
- Terpene↔strain content graph: a `terpene` document type cross-referenced via a GROQ
  reverse join, surfaced as `/terpenes/[slug]` pages; the content-scaffolding skill
  auto-provisions terpene docs with AI-generated hero imagery.
- Nightly four-job CI audit (build · sitemap validation · Lychee link-health ·
  Lighthouse) wired as a reusable workflow on PRs and a schedule.
- Custom Claude Code skills run content ops conversationally — scaffolding
  strains/products/posts, catalog auditing, multimodal alt-text backfill at the Sanity
  asset level, and a bash image-ingest pipeline (HEIC→JPEG, slug renames, SHA-256 dedup).
- Internal ops platform (ops.nw-local.com): a Django 6 + HTMX CRM that pushes to Sanity
  via `post_save` signals to keep the public wholesale page in sync, with passwordless
  magic-link auth (custom fix for a django-allauth allowlist-bypass), shipped to Fly.io
  via CI/CD.
- **Stack:** Astro · Sanity · astro-portabletext · TypeScript · GitHub Actions ·
  Django 6 · Python 3.14 · Postgres 18 · HTMX · AWS SES · OpenTofu

### The North West Clothing · Founder · 2001–Present
[nwclothing.com](https://nwclothing.com)

Independent Pacific Northwest apparel brand specializing in design, decoration, and
distribution. Founded 2001; relaunched in 2026 on a modern stack with print-on-demand
fulfillment.

- Original era (2001–2015): generated up to $5K/day in online sales through targeted
  campaigns; up to $20K gross revenue per weekend at sponsored events and festivals;
  trained employees across retail, warehouse, and screen-printing operations;
  sustained inventory levels via demand forecasting from sales analytics.
- 2026 relaunch: custom Shopify OS 2.0 theme (Dawn-based) with a Vite + SCSS + Alpine.js
  build pipeline; store run conversationally through a 26-skill Claude Code surface.
- Order-forwarding bridge on a Cloudflare Worker: a 15-minute cron forwards paid Shopify
  orders to a Manual-API Printful store (which Shopify's native integration can't create
  programmatically), with exactly-once delivery via Printful `external_id`, per-order
  error metafields, and Resend failure alerts.
- Declarative product pipeline: Zod-validated YAML specs resolve against the live
  Printful catalog (with margins) to build the full Size × Fabric × Colorway matrix in
  Shopify via the Admin GraphQL `productSet` mutation, then publish, create 301
  redirects, and archive superseded products — dry-run by default.
- SEO intelligence layer joining Google Search Console + GA4 traffic + a structural
  audit into a P0–P3 prioritized opportunity report, with URL Inspection API
  indexability checks.
- **Stack:** Shopify (Admin GraphQL) · Liquid · Vite · TypeScript · Zod · Alpine.js ·
  SCSS · Cloudflare Workers · Printful API · Google APIs (GSC + GA4) · Resend · Vitest

### Rooted Community · Engineer · 2024–Present
[rootedcommunity.org](https://rootedcommunity.org)

Marketing site for a small Washington nonprofit serving system-impacted BIPOC
community members in King, Snohomish, and Pierce counties.

- Zero-touch content deploys: a Sanity→GitHub webhook fires `repository_dispatch` on
  every Studio publish; CI is ordered so type-check and audits gate the deploy,
  preventing a bad push from racing to production.
- Lighthouse-driven accessibility to 100/100/100/100: heading-order fixes via a
  composable typed `headingLevel` prop plus a focus-revealed skip link.
- **Stack:** Astro 6 · Sanity · TypeScript · self-hosted variable fonts · Lighthouse CI
  · Lychee · GitHub Actions

---

## Engineering Experience

### U.S. LawShield · Senior Software Development Engineer (Contract) · Sep 2022 – Aug 2025
[uslawshield.com](https://uslawshield.com)

*PHP · Laravel · Docker · Kubernetes · AWS EKS · Helm · React · Next.js · Tailwind · GitLab*

- Maintained backwards compatibility with the legacy API while building multiple new
  backend services and migrating a poorly-structured monolith into modern, scalable
  service architecture supporting continued product growth.
- Partnered with the DevOps lead to containerize applications and upgrade the CI/CD
  pipelines using Docker, Kubernetes, AWS EKS, Helm charts, and GitLab.
- Added automated unit tests and test coverage to previously untested or
  manually-tested code bases.
- Built a React-based employee dashboard used by customer support agents, admins,
  attorneys, and executives, with role-based access control (RBAC) for permissions.

### Crowd Cow · Software Engineer (FTE) · May 2021 – Dec 2021
[crowdcow.com](https://crowdcow.com)

*Ruby on Rails · Vue.js · Sass · Redis · MySQL · Docker · Heroku · RSpec*

- **Redesigned the legacy credit-card processing module, raising subscription payment
  acceptance from 70% to 90%.** Categorized failed-charge decline codes from the
  payment processor and strategically targeted retry scenarios — for example, timing
  retries on insufficient-funds declines for likely account-replenishment windows.
- On-call rotation for site reliability and production incident response; primary
  point of contact for team support tickets.

### Tomorrow Ideas (acq. Ethos Life) · Mar 2017 – May 2021
[tmro.com](https://tmro.com)

Early-stage fintech startup; acquired by Ethos Life. Joined as contract project lead
for the public launch and grew through promotion to SDE II over 4+ years.

**Software Development Engineer II (FTE) · Aug 2020 – May 2021**

*TypeScript · React · Redux · Node · Express · Tailwind · Redis · Docker · GitHub Actions · AWS · Jest*

- Engineering project lead for a complete UI/UX redesign of the app's web experience,
  pivoting from a native-app-funnel model to a web-centric desktop-friendly product
  built from the ground up.
- Collaborated with external partners and engineers on exclusive integrations
  with Tomorrow's app and APIs.

**Software Engineer (FTE) · Aug 2017 – Jul 2020**

*Python · Django · PHP · Laravel · React · Redux · Sass · Redis · PostgreSQL · Docker · TravisCI · AWS · PHPUnit*

- Led refactoring projects on the monolithic API codebase, converting key modules
  into containerized services; built efficient, reliable CI/CD pipelines for all
  backend services and web projects.
- Built a custom admin dashboard with on-demand features for executive, BI,
  marketing, product, and customer-support teams.
- Identified and repaired bottlenecks in page-load and server response times.
- Mentored junior engineers via regular pair-programming and code review.

**Software Engineer (Contract) · Mar 2017 – Jul 2017**

*Python · Django · Wagtail CMS · React · Redux · PostgreSQL · CircleCI · AWS · Pytest*

- Project lead for the launch of Tomorrow's marketing site and flagship web app.
  Owned all web-development tasks for the company's public product announcement and
  initial release.

### Instrument · Full Stack Engineer (Contract) · Jun 2022 – Sep 2022
[instrument.com](https://instrument.com)

*Docker · Node · WordPress · MySQL · GitHub Actions · WPEngine · Jest*

- Delivered a complete website redesign for the nonprofit
  [BlackSpace](https://blackspace.org/) alongside the agency's design and dev teams.
- Built a containerized dev environment to streamline frontend onboarding; wrote
  scripts to sync content between remote and local databases.
- Set up custom CI/CD pipelines with GitHub Actions and WPEngine.

---

## Selected Projects

*Self-directed works in progress — problem domains outside the ventures.*

- **crate-agent** — native macOS companion app for Serato DJ (Swift/SwiftUI + Rust via
  UniFFI) that keeps the Serato library in sync when tracks are renamed or moved in
  Finder: watches the filesystem and rewrites Serato's binary library files so their
  absolute-path track links never silently break.
- **kraang** — self-hosted personal knowledge graph (FastAPI · GraphQL · Postgres): a
  five-worker IMAP ingestion pipeline with an auditable state machine and Postgres-role
  service isolation, plus Claude Code skills wired to the live API for AI-assisted
  document review.

---

## Technical

**Languages** TypeScript · JavaScript · Elixir · Python · Ruby · PHP · Bash

**Frontend** Astro · Next.js · React · Phoenix LiveView · Alpine.js · Tailwind · SCSS

**Backend** Phoenix · Django · Express · Rails · Laravel

**Data** PostgreSQL · MySQL · Redis · MongoDB · Cloudflare R2

**Infrastructure** AWS · Cloudflare · Cloudflare Workers · Fly.io · Docker · GitHub Actions · OpenTofu

**Content & commerce** Sanity · Contentful · WordPress · Shopify (Admin GraphQL)

**Practices** SOLID · Service-Oriented Architecture · Test-Driven Development · RBAC · CI/CD · IaC · Postmortem-driven invariants

---

## Education

**International Business & Trade, AAS** · Highline College, Des Moines WA · 2018

President's List · Vice President's Honor Roll · Phi Theta Kappa Honor Society

</details>
