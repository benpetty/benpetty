# Benjamin S. Petty

> Senior Software Engineer & Founder · Pacific Northwest

Senior software engineer and founder. Eight years on SaaS engineering teams at Tomorrow Ideas (acq. Ethos Life), Crowd Cow, and U.S. LawShield. Since 2001 I've built and run the software behind four independent Pacific Northwest businesses. **Open to senior engineering roles and contract/fractional engagements.**

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

Live-streaming radio. Each channel plays a curated loop of audio, in sync for
every listener.

*Elixir · Phoenix · LiveView · Postgres · Oban · Cloudflare R2 · AWS SES · Fly.io · Next.js · React*

- Built the live-audio engine in Elixir. One process per channel keeps every
  listener on the same segment.
- Built the transcode pipeline. ffmpeg cuts uploads into HLS segments at four
  bitrates on Cloudflare R2, with background workers handling transcode,
  cleanup, and backups. An interrupted job resumes from the last complete
  segment rather than starting over.
- Run it in production: transactional email, analytics that resolve country at
  write time and discard the IP, self-serve GDPR export and delete, and a
  written record of every failure mode I've hit so far.
- Built the marketing site on Next.js. Caching and memoization took it from
  roughly 200 API calls per build down to 3.

### Northwest Local Cannabis · Co-Founder · 2021–Present
[nw-local.com](https://nw-local.com)

Licensed craft cannabis producer and processor in Washington. I cover the grow,
the tech, the brand, and distribution.

*Astro · Sanity · TypeScript · Django · Python · Postgres · HTMX · Fly.io*

- Built the brand site on Astro and Sanity, with the CMS as the single source of
  truth for strains, products, posts, and retail partners.
- Built the internal ops platform: a Django and HTMX CRM for retailers,
  contacts, and deals, with magic-link sign-in. Changes push to Sanity, so the
  public wholesale page stays current.
- Wrote the content tooling: structured-data generation, a nightly CI audit of
  the build, sitemap, links, and Lighthouse scores, and an image pipeline that
  converts HEIC to JPEG, renames by slug, and drops duplicates by hash.

### The North West Clothing · Founder · 2001–Present
[nwclothing.com](https://nwclothing.com)

Pacific Northwest apparel brand. Founded in 2001, relaunched in 2026 with
print-on-demand fulfillment.

*Shopify (Admin GraphQL) · Liquid · Vite · TypeScript · Alpine.js · Cloudflare Workers · Printful API*

- 2001–2015: up to $5K/day in online sales, and up to $20K in a weekend at
  events and festivals. Forecast demand from sales data and trained staff across
  retail, warehouse, and screen printing.
- Relaunched the store in 2026 on a custom Shopify theme. Catalog and deploy
  work runs through 26 custom Claude Code skills I wrote for it.
- Built the order bridge on a Cloudflare Worker. A cron job forwards paid
  Shopify orders to Printful, delivers each one exactly once, and alerts on
  failures.
- Built the product pipeline. YAML specs resolve against the live Printful
  catalog and generate the full size, fabric, and color matrix through Shopify's
  Admin GraphQL API, then publish and redirect. Dry-run by default.

### Rooted Community · Engineer · 2024–Present
[rootedcommunity.org](https://rootedcommunity.org)

Website for a Washington nonprofit serving system-impacted BIPOC community
members. Pro bono.

*Astro · Sanity · TypeScript · GitHub Actions*

- Publishing in the CMS triggers a deploy. Type-checks and audits run before it,
  not after.
- Took the site to 100 in all four Lighthouse categories.

---

## Engineering Experience

### Independent Software Consultant · 2026–Present

Records and document systems for a community association management firm.

*Python · pypdfium2 · Apple Vision · tesseract · pytest*

- Built an audit pipeline for a records request. It hashes every file in a
  document archive, including files nested inside zip archives, to separate what
  was produced from what was withheld, then compares withheld PDFs page by page.
- Every output package is byte-reproducible and ships with a SHA-256 manifest
  and its own hash for the transmittal record.
- Built a full-text index over the same archive. It reads each document's text
  layer and OCRs the pages that lack one through two engines, then reports
  coverage per document, so an unreadable file is never mistaken for an empty
  one.
- Rendered an email archive to a bookmarked PDF for legal review. Remote images
  are blocked, so opening it does not notify the senders.

### U.S. LawShield · Senior Software Development Engineer (Contract) · Sep 2022 – Aug 2025
[uslawshield.com](https://uslawshield.com)

*PHP · Laravel · React · Next.js · Docker · Kubernetes · AWS EKS · Helm · GitLab*

- Migrated a monolith into separate services while keeping the legacy API
  working for the clients already on it.
- Built product and coverage logic for a legal-services platform whose offerings
  are regulated separately in all 50 states.
- Built the internal dashboard used by support agents, admins, attorneys, and
  executives, with per-role permissions.
- Containerized the applications on Docker, Kubernetes, and AWS EKS with the
  DevOps lead, and added test coverage to code that had none.

### Crowd Cow · Software Engineer (FTE) · May 2021 – Dec 2021
[crowdcow.com](https://crowdcow.com)

*Ruby on Rails · Vue.js · Redis · MySQL · Docker · Heroku · RSpec*

- Redesigned the credit-card processing module and raised subscription payment
  acceptance from 70% to 90%. Sorted decline codes by reason and retried each
  one when it was most likely to clear, such as retrying insufficient funds on
  payday.
- On call for site reliability and production incidents, and the first point of
  contact for team support tickets.

### Tomorrow Ideas (acq. Ethos Life) · Software Engineer → SDE II · Mar 2017 – May 2021
[tmro.com](https://tmro.com)

Estate-planning app, acquired by Ethos Life. Joined as a contractor to lead the
launch and was promoted to SDE II over four years. The product was the legal
documents themselves, which had to meet the requirements of all 50 states.

*Python · Django · TypeScript · React · Redux · Node · PostgreSQL · Docker · AWS*

- Led the web build for the public launch: the marketing site and the first
  release of the app.
- Built document generation for wills and related instruments against each
  state's execution requirements.
- Led the redesign that moved the product from a native-app funnel to a
  desktop-friendly web app.
- Converted modules of the monolithic API into containerized services and built
  the CI/CD pipelines for them.
- Built the internal dashboard used by the executive, BI, marketing, product,
  and support teams.
- Mentored junior engineers through pairing and code review.

### Instrument · Full Stack Engineer (Contract) · Jun 2022 – Sep 2022
[instrument.com](https://instrument.com)

*Docker · Node · WordPress · MySQL · GitHub Actions · WPEngine*

- Rebuilt the website for the nonprofit [BlackSpace](https://blackspace.org/)
  with the agency's design and engineering teams, and set up the deploy
  pipeline.

---

## Selected Projects

*Self-directed, outside the ventures.*

- **crate-agent** — macOS companion app for Serato DJ, in Swift and Rust. It
  watches the filesystem and rewrites Serato's library files when tracks are
  renamed or moved, so the links to them don't break.
- **kraang** — self-hosted knowledge graph on FastAPI, GraphQL, and Postgres. A
  five-worker email ingestion pipeline with an auditable state machine and a
  separate Postgres role per service.

---

## Technical

**Languages** TypeScript · JavaScript · Python · Elixir · Ruby · PHP · SQL

**Frontend** React · Next.js · Astro · Phoenix LiveView · Alpine.js · Tailwind · SCSS

**Backend & data** Django · Phoenix · Rails · Laravel · Express · PostgreSQL · MySQL · Redis

**Infrastructure** AWS · Cloudflare · Fly.io · Docker · Kubernetes · GitHub Actions · OpenTofu

**Content & commerce** Sanity · Contentful · Shopify (Admin GraphQL) · WordPress

---

## Education

**International Business & Trade, AAS** · Highline College, Des Moines WA · 2018

President's List · Vice President's Honor Roll · Phi Theta Kappa Honor Society

</details>
