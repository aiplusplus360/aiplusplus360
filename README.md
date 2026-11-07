### Hi, I'm Khawaja Safiullah

I build the unglamorous half of AI systems: the part that measures whether it works, stops it when it doesn't, and explains why afterwards.

**50 small, dependency-free tools.** Every repo has typed APIs, unit tests, doctests, CLI tests, a `pyproject.toml`, a CI workflow that runs for real, and a README that admits what it doesn't do.

```console
$ python -c "import sys; print(sys.version)"
3.9+  ·  100% standard library  ·  0 runtime dependencies  ·  50 repositories
```

---

## AI & Automation — 35 tools

Each one covers a failure mode the others don't. They compose: lint a prompt, gate it in CI, route it to the cheapest model that works, budget the agent's tool calls, trace the run, and price the result.

| Repo | The failure it prevents |
|---|---|
| [`llm-router`](https://github.com/aiplusplus360/llm-router) | Overpaying 60× for a task a cheap model handles — or underpaying and silently degrading quality. Every routing decision comes with a stated reason and a fallback chain. |
| [`tool-guard`](https://github.com/aiplusplus360/tool-guard) | An agent looping forever and turning a 2¢ job into a $400 bill. Allowlists, per-call timeouts, call/time/cost budgets, and loop detection enforced at the only entry point. |
| [`context-budget`](https://github.com/aiplusplus360/context-budget) | A long conversation silently truncating the system prompt or the user's actual question. Deterministic packing with pinned, summarised, and dropped tiers. |
| [`structured-output`](https://github.com/aiplusplus360/structured-output) | Paying for a second generation to fix a code fence. Repairs locally, validates against a real schema, and only calls the model again when both fail. |
| [`stream-json`](https://github.com/aiplusplus360/stream-json) | Parsing half-arrived JSON and getting `Expecting ',' delimiter`. Reports exactly which construct is unfinished and where. |
| [`prompt-template`](https://github.com/aiplusplus360/prompt-template) | Shipping a prompt with `{{user_name}}` still in it. Only `{{name}}` is syntax, so JSON braces survive, and every missing variable is reported with a line number. |
| [`prompt-lint`](https://github.com/aiplusplus360/prompt-lint) | Injectable instructions and unfollowable rules — found without calling a model. |
| [`prompt-regression`](https://github.com/aiplusplus360/prompt-regression) | A prompt edit that changes behaviour while the test suite stays green. Layered comparison: rules outrank similarity. |
| [`prompt-dedup`](https://github.com/aiplusplus360/prompt-dedup) | Forty prompts that are almost the same prompt. MinHash for speed, exact Jaccard for the final call, stable output between runs. |
| [`semantic-diff`](https://github.com/aiplusplus360/semantic-diff) | A prompt diff that marks every reflowed sentence as a change instead of saying "the output format changed". |
| [`split-guard`](https://github.com/aiplusplus360/split-guard) | An eval row leaking into the training set. Exact-normalised duplicates, hashed word 5-shingles, Jaccard similarity, and verbatim answer leakage. |
| [`eval-judge`](https://github.com/aiplusplus360/eval-judge) | Gating a deploy on a judge nobody validated. Agreement rates, position bias, and known-answer calibration. |
| [`eval-stats`](https://github.com/aiplusplus360/eval-stats) | Shipping a regression because 82% looked bigger than 79%. Bootstrap intervals, paired permutation tests, exact McNemar, and the sample size you would actually need. |
| [`rag-eval`](https://github.com/aiplusplus360/rag-eval) | An improving average hiding a query that broke. Recall, precision, MRR, nDCG, and per-query regression detection. |
| [`agent-trace`](https://github.com/aiplusplus360/agent-trace) | Not knowing where the 40 seconds and 9 cents went. Span waterfall, token and cost rollup, self-contained HTML — no server, no CDN. |
| [`cost-ledger`](https://github.com/aiplusplus360/cost-ledger) | Spend per tenant in rounded floats, and models that quietly price at zero. Exact decimal cents, explicit unpriced models, and invoice reconciliation. |
| [`mcp-server-kit`](https://github.com/aiplusplus360/mcp-server-kit) | Hand-written JSON Schema drifting from the function it describes. Generated from type hints, with correct JSON-RPC 2.0 lifecycle over stdio. |
| [`mcp-inspector`](https://github.com/aiplusplus360/mcp-inspector) | An agent trusting a tool description that hides instructions, destructive scope, or a schema that accepts anything. |
| [`bpe-tokenizer`](https://github.com/aiplusplus360/bpe-tokenizer) | Token counts and costs you can't compute offline. Train a byte-level BPE vocabulary from your own corpus — no download, no `<unk>`. |
| [`embed-cache`](https://github.com/aiplusplus360/embed-cache) | Paying to embed the same corpus twice. Content-addressed cache with chunk-level reuse. |
| [`doc-to-vectors`](https://github.com/aiplusplus360/doc-to-vectors) | Structure-blind chunking that splits a table in half. Structural Markdown boundaries, traceable heading paths, and BM25 + RRF retrieval to measure before you pay for a vector DB. |
| [`vector-store-lite`](https://github.com/aiplusplus360/vector-store-lite) | An index you can't trust and can't measure. Random-hyperplane LSH in one JSON file, with a built-in `recall(k)` check against brute-force cosine. |
| [`redact-pii`](https://github.com/aiplusplus360/redact-pii) | Regexes that redact an order number as a credit card. Validators that reject lookalikes — Luhn, IBAN mod-97, and a date is not a phone number. |
| [`intake-agent`](https://github.com/aiplusplus360/intake-agent) | Tickets routed by a black box. Deterministic triage: intent, owning queue, urgency with SLA, entities, a PII-safe summary, and a link to earlier duplicates. |
| [`lead-enrich`](https://github.com/aiplusplus360/lead-enrich) | A merge you cannot audit. Blocking plus fuzzy scoring, provenance on every field, and conflicts reported instead of overwritten. |
| [`sheet-sync`](https://github.com/aiplusplus360/sheet-sync) | Last-write-wins sync that silently deletes edits. Three-way merge with recorded conflicts. |
| [`html-to-text`](https://github.com/aiplusplus360/html-to-text) | A scraper that returns a cookie banner, nine menu items, and then the article. Isolates the body by text mass and link density. |
| [`scrape-kit`](https://github.com/aiplusplus360/scrape-kit) | Scraping that gets you blocked. RFC 9309 robots.txt, per-host pacing, and retries that know when to stop. |
| [`change-watch`](https://github.com/aiplusplus360/change-watch) | Alerts on the cookie banner. Learns each page's template from several snapshots, masks it, and diffs what is left at block level. |
| [`queue-lite`](https://github.com/aiplusplus360/queue-lite) | Standing up Redis to run a background job. A durable queue in one SQLite file: leases, jittered backoff, dead letters, dedup. |
| [`rate-limit-lite`](https://github.com/aiplusplus360/rate-limit-lite) | Limits that reset on every deploy and don't hold across workers. Token bucket and sliding window in one SQLite file. |
| [`retry-budget`](https://github.com/aiplusplus360/retry-budget) | The third retry turning a failing dependency into an outage. Jittered backoff, a shared retry budget, and a circuit breaker. |
| [`webhook-relay`](https://github.com/aiplusplus360/webhook-relay) | Dropping a webhook because the receiver was down for 30 seconds. Signature verification, idempotent dedup, retries, and a replayable dead-letter queue. |
| [`secret-sweep`](https://github.com/aiplusplus360/secret-sweep) | A key that was `git rm`'d and is still in history. Entropy plus shape checks, with the commit that introduced it. |

```console
$ llm-router route "hi there"                  → nano-1    $0.00008
$ llm-router route "implement a ring buffer"   → large-1   $0.00483
```

```console
$ rag-eval demo
recall  0.667 → 1.000   +0.333     ← every aggregate improved
1 regression(s): export my data  1.00 → 0.50
VERDICT: mixed (aggregate moved, but some queries regressed)
```

```console
$ split-guard check train.jsonl eval.jsonl
LEAK   train.jsonl:412 ↔ eval.jsonl:9   jaccard=0.86   5-shingles
LEAK   train.jsonl:88  ↔ eval.jsonl:14  verbatim answer
2 leaks in 500 train / 60 eval rows
```

---

## DevOps & Infrastructure — 15 tools

| Repo | What it catches |
|---|---|
| [`k8s-lint`](https://github.com/aiplusplus360/k8s-lint) | `image:latest`, UID 0, privilege escalation, missing limits and probes, host namespaces, no NetworkPolicy or PDB. Ships its own YAML subset parser. |
| [`docker-doctor`](https://github.com/aiplusplus360/docker-doctor) | Running as root, unpinned base images, secrets baked into layers, stale apt caches, `curl \| sh`, and build tools shipped to production. |
| [`gha-audit`](https://github.com/aiplusplus360/gha-audit) | Unpinned actions, ambient permissions, and untrusted event text reaching a shell. |
| [`nginx-doctor`](https://github.com/aiplusplus360/nginx-doctor) | The four `proxy_pass` traps, header inheritance, `if` semantics, and the TLS defaults nobody sets. |
| [`systemd-doctor`](https://github.com/aiplusplus360/systemd-doctor) | A unit that runs as root with no sandbox and restarts forever. 17 rules plus a 20-point hardening score. |
| [`dns-doctor`](https://github.com/aiplusplus360/dns-doctor) | Mail that silently fails authentication. Raw UDP DNS client plus SPF lookup limits, `+all`, DMARC policy and reporting gaps, DKIM key size, CAA. |
| [`cert-watch`](https://github.com/aiplusplus360/cert-watch) | Reading X.509 with no crypto dependency — expiry, names, and whether the chain on the wire is the chain a client can build. |
| [`deploy-preflight`](https://github.com/aiplusplus360/deploy-preflight) | Expired certificates, redirect loops, missing security headers, HTML cached for a year, sitemaps pointing at staging. Fails CI before a customer finds it. |
| [`deploy-verify`](https://github.com/aiplusplus360/deploy-verify) | A green pipeline shipping a broken deploy. Declarative smoke suites that fail with evidence: which URL, status, header, or JSON field. |
| [`infra-inventory`](https://github.com/aiplusplus360/infra-inventory) | Drift between `docker-compose.yml` and `docker ps` — services missing, ports undeclared, digests changed without announcement. |
| [`backup-verify`](https://github.com/aiplusplus360/backup-verify) | A backup that is present and not restorable. Reads every archive member, parses SQL dumps for truncation, and asks SQLite for its own verdict. |
| [`uptime-lite`](https://github.com/aiplusplus360/uptime-lite) | Alerts that cry wolf. Failure thresholds, recovery thresholds, flapping suppression, webhook alerts, one JSON file. |
| [`log-triage`](https://github.com/aiplusplus360/log-triage) | A wall of logs where the new error is invisible. Templates the log, then shows only what was not there before the deploy. |
| [`cron-audit`](https://github.com/aiplusplus360/cron-audit) | Jobs that pile up and jobs that quietly stopped. Parses a crontab the way cron does and compares the schedule with what actually ran. |
| [`csv-doctor`](https://github.com/aiplusplus360/csv-doctor) | Loading a ragged, duplicate-keyed, outlier-riddled CSV into production. Profiles in one pass, then repairs with a plan you read before anything is written. |

```console
$ k8s-lint check deploy/
deploy/api.yaml:14  error    image:latest — tag is mutable, rollback is not reproducible
deploy/api.yaml:22  error    securityContext.runAsUser: 0 — container runs as root
deploy/api.yaml:31  warning  no readinessProbe — traffic arrives before the app is ready
3 findings (2 error, 1 warning)
```

```console
$ dns-doctor audit example.com
SPF    spf1 ip4:… include:_spf.google.com ~all   lookups=4/10  ok
DMARC  p=quarantine pct=100 rua=mailto:…         ok
DKIM   selector=default key=2048 bits           ok
CAA    0 issue "letsencrypt.org"                ok
```

---

## How these are built

Every one of the 50 follows the same rules:

- **No runtime dependencies.** A debugging tool you can't `pip install` on an air-gapped box is a tool you won't use during an incident.
- **Typed APIs, honest CLIs.** Every package has a typed core, an `argparse` CLI with exit codes that mean something, and `python -m` entry points.
- **Tests that assert something.** Metrics are verified against hand-computed values, not against the implementation's own output. Unit tests, doctests, and CLI tests ship in every repo.
- **CI that has failed at least once.** Each workflow runs on 3.9, 3.11 and 3.13. The ones that broke broke for real reasons, and the fix is in the history.
- **READMEs that name the limitation.** Timeouts are cooperative. The YAML parser is a subset. Token counts are estimates. Pretending otherwise is how documentation gets someone paged at 2am.

## Things I care about

**A metric that hides the tail is worse than no metric.** `recall@10 = 0.95` and `p95 recall = 0.0` are both true at the same time. Only one of them is what a user experiences.

**A limit that can be bypassed isn't a limit.** Instructions in a prompt are suggestions. Checks before every call are limits.

**Expected failures are data, not errors.** A tool that says "no" should return something the model can read — not a transport error that triggers a retry storm.

**Explain the decision.** "Why did this go to the cheap model?" is the first question asked when quality drops, and it needs an answer better than "the heuristic said so."

---

<sub>Python · standard library only · TypeScript · Node · Postgres · React · GitHub Actions</sub>
