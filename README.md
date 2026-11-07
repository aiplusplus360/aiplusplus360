### Hi, I'm Khawaja Safiullah

I build the unglamorous half of AI systems: the part that measures whether it works, stops it when it doesn't, and explains why afterwards.

Ten small, dependency-free tools and two applications. Every repo has tests, CI that passes for real reasons, and a README that admits what it doesn't do.

---

## The AI reliability stack

These fit together. Each one covers a failure mode the others don't.

| Repo | The failure it prevents | Why it's hard |
|---|---|---|
| [`llm-router`](https://github.com/aiplusplus360/llm-router) | Overpaying 60× for a task a cheap model handles, or underpaying and silently degrading quality | Explaining the decision, not just making it |
| [`tool-guard`](https://github.com/aiplusplus360/tool-guard) | An agent looping forever and turning a 2¢ job into a $400 bill | Enforcing limits at the only entry point, so they can't be bypassed |
| [`structured-output`](https://github.com/aiplusplus360/structured-output) | Paying for a second generation to fix a code fence | Repairing locally first, without corrupting valid data |
| [`rag-eval`](https://github.com/aiplusplus360/rag-eval) | An improving average hiding a query that broke | Per-query regressions, because means lie |
| [`prompt-regression`](https://github.com/aiplusplus360/prompt-regression) | A prompt edit that changes behaviour while tests stay green | Layered comparison: rules outrank similarity |
| [`agent-trace`](https://github.com/aiplusplus360/agent-trace) | Not knowing where the 40 seconds and 9 cents went | Tolerating broken traces, because crashes are what you investigate |
| [`mcp-server-kit`](https://github.com/aiplusplus360/mcp-server-kit) | Hand-written JSON Schema drifting from the function it describes | Generating it from type hints, and getting JSON-RPC lifecycle right |

```console
$ llm-router route "hi there"          → nano-1     $0.00008
$ llm-router route "implement a ring buffer" → large-1  $0.00483
```

```console
$ rag-eval demo
recall  0.667 → 1.000   +0.333     ← every aggregate improved
1 regression(s): export my data  1.00 → 0.50
VERDICT: mixed (aggregate moved, but some queries regressed)
```

## DevOps and deployment

| Repo | What it does |
|---|---|
| [`deploy-preflight`](https://github.com/aiplusplus360/deploy-preflight) | TLS expiry, redirect chains, security headers, caching, robots and sitemap — before you ship |
| [`devops-site`](https://github.com/aiplusplus360/devops-site) | React 19 SSR marketing site, 40 JSON-driven service pages, CI/CD with production smoke tests |

## Applications

| Repo | What it is |
|---|---|
| [`agencyops`](https://github.com/aiplusplus360/agencyops) | An AI ops engine that plans, routes, grades and self-heals agency work — with a deterministic fallback for every AI decision and an audit log that proves it |

---

## How these are built

Every one of the eleven repos follows the same rules:

- **No runtime dependencies.** A debugging tool you can't `pip install` on an air-gapped box is a tool you won't use during an incident.
- **Tests that assert something.** Metrics are verified against hand-computed values, not against the implementation's own output.
- **CI that has failed at least once.** Each workflow was run locally first; the ones that broke broke for real reasons (a missing `pyproject.toml`, a cost rollup that reported `$0.00`), and the fix is in the history.
- **READMEs that name the limitation.** Timeouts are cooperative. The validator doesn't support `$ref`. Token counts are `len(text) // 4`. Pretending otherwise is how documentation gets someone paged at 2am.

## Things I care about

**A metric that hides the tail is worse than no metric.** `recall@10 = 0.95` and `p95 recall = 0.0` are both true at the same time. Only one of them is what a user experiences.

**A limit that can be bypassed isn't a limit.** Instructions in a prompt are suggestions. Checks before every call are limits.

**Expected failures are data, not errors.** A tool that says "no" should return something the model can read — not a transport error that triggers a retry storm.

**Explain the decision.** "Why did this go to the cheap model?" is the first question asked when quality drops, and it needs an answer better than "the heuristic said so."

---

<sub>Python · TypeScript · Node · Postgres · React · GitHub Actions</sub>
