# Khawaja Safiullah

**I build systems that run without me — agentic AI loops, scraping pipelines, and the deployment infrastructure that keeps them honest.**

Most AI demos are a prompt and a chat box. The work I care about is what happens on the ninety-ninth run: when the model times out, when a scraper gets blocked, when a deploy ships stale HTML. That is where software either holds up or doesn't.

---

## What I'm working on

**Closed-loop agentic systems.** Give an agent a goal and a rubric, not a script, then build the parts that make that safe: deterministic fallbacks when the model is unavailable, an audit trail for every autonomous decision, and guard rails that stop a bad rubric from producing infinite retries.

**The unglamorous half.** TLS expiry, redirect chains, cache policy, robots parsing to spec. A surprising share of production incidents live in the twenty lines nobody wrote a test for.

---

## Featured work

### [agencyops](https://github.com/aiplusplus360/agencyops)
A closed-loop AI operations engine for agencies. The owner types what they want; it becomes a 90-day roadmap, gets routed to the right specialist, graded against a rubric, and the plan self-heals when something slips.

`Node` · `Express` · `PostgreSQL` · `Prisma` · `Socket.IO` · `React` · `LLM`

*34 models, 30 AI services, 30 REST modules. Every AI path has a deterministic fallback, so the loop closes even with no API key.*

### [devops-site](https://github.com/aiplusplus360/devops-site)
A server-rendered marketing site with 44 routes generated from JSON content, an Express contact API, and a CI/CD pipeline that smoke-tests production after every deploy.

`React 19` · `SSR` · `Vite` · `Express` · `GitHub Actions`

*One route table shared by client and server, so the server can never disagree with the browser about which URLs exist.*

### [prompt-regression](https://github.com/aiplusplus360/prompt-regression)
Catch prompt regressions in CI. A prompt is a dependency — this records expected behaviour and fails the build when output drifts.

`Python` · `Zero dependencies` · `44 tests` · `CI on 3.9 / 3.11 / 3.13`

*The layered comparison is the point: a perfect similarity score can't rescue an output that dropped required content.*

### [deploy-preflight](https://github.com/aiplusplus360/deploy-preflight)
Pre-deploy checks for any URL: TLS expiry, redirect chains, security headers, cache policy, robots and sitemap.

`Python` · `Zero dependencies` · `38 tests`

*Parses `robots.txt` to RFC 9309 — group-scoped and longest-match — because grepping for `Disallow: /` reports a false positive on half the internet.*

---

## How I work

**Fallbacks over assumptions.** If a feature only works when a vendor is up, it's a bug. Every AI path I ship has a deterministic path behind it.

**Test the rules, not the wording.** Model output is prose; asserting on bytes fails on noise until someone deletes the test. Assert on required content, forbidden content, and *then* similarity — in that order.

**Make failure legible.** An unreachable host is a failure, not a skip. A bad certificate says *"certificate verification failed"*, not *"network error"*. A red deploy says which assertion failed.

**Preserve the audit trail.** When software makes a decision on its own, the reasoning, the model, and the cost get recorded. "The AI did it" is not an answer anyone can ship on.

---

## Stack

```text
Languages    TypeScript · Python · JavaScript · SQL · Rust (a little)
Backend      Node, Express, Prisma, PostgreSQL, FastAPI-style pipelines
Frontend     React, Vite, Tailwind, vanilla TS when it's faster
AI           LLM orchestration, RAG, embeddings, prompt evaluation, agents
Infra        Docker, nginx, systemd, GitHub Actions, VPS deploys, TLS
Data         Scraping, enrichment, ETL, Postgres modelling
```

---

## Reach me

Open to **AI engineering, automation, and full-stack roles** where the work is systems, not slideware.

[![Email](https://img.shields.io/badge/Email-khawajasafiullah18%40gmail.com-EA4335?style=flat-square&logo=gmail&logoColor=white)](mailto:khawajasafiullah18@gmail.com)
[![GitHub](https://img.shields.io/badge/GitHub-aiplusplus360-181717?style=flat-square&logo=github&logoColor=white)](https://github.com/aiplusplus360)

<sub>Every repository here is built and maintained by me. If you're evaluating my work, the commit history is the best place to start.</sub>
