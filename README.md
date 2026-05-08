# Benjamin S. Petty

> Founder · Engineer · Pacific Northwest

Founder and senior engineer with 24+ years building products end-to-end. Currently running four consumer-facing PNW brands; previously senior engineer at Tomorrow (acq. Ethos Life), Crowd Cow, and U.S. LawShield.

## Currently building

| Venture | Role | Since | |
|---|---|---|---|
| **Audeos.fm** | Founder & Engineer | 2023 | [audeos.com](https://audeos.com) |
| **Northwest Local Cannabis** | Co-Founder | 2021 | [nw-local.com](https://nw-local.com) |
| **The North West Clothing** | Founder | 2001 | [nwclothing.com](https://nwclothing.com) |
| **Rooted Community** | Engineer | 2024 | [rootedcommunity.org](https://rootedcommunity.org) |

[**ben-petty.com**](https://ben-petty.com/) · [Resume PDF ↓](resume.pdf)

---

<details>
<summary>Full resume</summary>

## Current Ventures · 2021–Present

### Audeos.fm · Founder & Engineer · 2023–Present
[audeos.com](https://audeos.com) · [audeos.fm](https://audeos.fm)

Multi-channel live-streaming radio platform. Each channel loops a curated playlist of
pre-transcoded audio, broadcast in sync to every listener.

- Realtime engine on Phoenix LiveView: a GenServer-per-channel state machine with
  PubSub fan-out keeps every listener synced to the same audio segment in real time.
- HLS pipeline: ffmpeg transcoder converts uploaded audio into rolling segments;
  Cloudflare R2 for object storage; MediaMTX RTMP relay; Oban background workers
  handle transcode, cleanup, and database backups.
- Solo deploy on Fly.io with telemetry-driven incident response, Sentry integration
  with PII scrubbing, and a documented postmortem-driven invariants culture.
- Marketing site (audeos.com): Next.js 16 + Contentful with build-time Spotify
  playlist integration and client-side Fuse.js search, deployed to GitHub Pages.
- **Stack:** Elixir · Phoenix · LiveView · Postgres · Oban · Cloudflare R2 · MediaMTX
  · Sentry · Fly.io · Next.js · Contentful

### Northwest Local Cannabis · Co-Founder · 2021–Present
[nw-local.com](https://nw-local.com)

Co-founder of Northwest Local Cannabis, a WA i502 licensed craft cannabis
producer/processor. Cultivator-operator across grow, tech, brand, and distribution.

- Astro 6 SSG with Sanity CMS as single source of truth for strains, products, blog
  posts, retailer partners, and site settings; deployed to GitHub Pages.
- Custom Claude Code skills automate content workflows — scaffolding new entries
  (strains, products, posts) and auditing the catalog.
- **Stack:** Astro · Sanity · TypeScript · GitHub Actions

### The North West Clothing · Founder · 2001–Present
[nwclothing.com](https://nwclothing.com)

Independent Pacific Northwest apparel brand specializing in design, decoration, and
distribution. Founded 2001; relaunched in 2026 on a modern stack with print-on-demand
fulfillment.

- Original era (2001–2015): generated up to $5K/day in online sales through targeted
  campaigns; up to $20K gross revenue per weekend at sponsored events and festivals;
  trained employees across retail, warehouse, and screen-printing operations;
  sustained inventory levels via demand forecasting from sales analytics.
- 2026 relaunch: custom Shopify OS 2.0 theme (Dawn-based) with Vite + SCSS + Alpine.js
  build pipeline; TypeScript CLI built on Shopify Admin GraphQL and Printful REST for
  POD fulfillment; conversational content management via custom Claude Code skills.
- **Stack:** Shopify · Liquid · Vite · TypeScript · Alpine.js · SCSS · Printful API

### Rooted Community · Engineer · 2024–Present
[rootedcommunity.org](https://rootedcommunity.org)

Marketing site for a small Washington nonprofit serving system-impacted BIPOC
community members in King, Snohomish, and Pierce counties.

- **Stack:** Astro · Sanity · TypeScript · GitHub Actions

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

## Technical

**Languages** TypeScript · JavaScript · Elixir · Python · Ruby · PHP · Bash

**Frontend** Astro · Next.js · React · Phoenix LiveView · Alpine.js · Tailwind · SCSS

**Backend** Phoenix · Django · Express · Rails · Laravel

**Data** PostgreSQL · MySQL · Redis · MongoDB · Cloudflare R2

**Infrastructure** AWS · Cloudflare · Fly.io · Docker · GitHub Actions

**Content & commerce** Sanity · Contentful · WordPress · Shopify (Admin GraphQL)

**Practices** SOLID · Service-Oriented Architecture · Test-Driven Development · RBAC · CI/CD · IaC · Postmortem-driven invariants

---

## Education

**International Business & Trade, AAS** · Highline College, Des Moines WA · 2018

President's List · Vice President's Honor Roll · Phi Theta Kappa Honor Society

</details>
