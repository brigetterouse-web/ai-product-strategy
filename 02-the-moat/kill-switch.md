# Kill Switch Audit

**Product:** Mariella — hosted multi-tenant AI marketing engine (Think & Grow)
**The test:** could we swap AI providers in under 48 hours?

## Vendor Dependency Assessment

| Dimension | Current State | Risk Level | 48-Hour Action |
|-----------|--------------|------------|---------------|
| **Provider** | One vendor, deeply. The hosted runtime isn't "we call an API" — it's the vendor's agent control plane: versioned agent configs, per-session sandboxes, the credential vault that keeps client secrets out of the running agent, file mounting for engine delivery, and scheduled runs for the weekly cadence. Every one of those is a product capability we'd otherwise have to build. | **H** | Prove the exit the architecture already names: run one tenant in self-hosted-sandbox mode on T&G infrastructure and record what breaks. "No rewrite" is currently an assumption, not a tested hatch. |
| **Abstraction** | Split, and the split is instructive. The durable tenant store **is** abstracted — local and object-storage backends behind one interface, selected by config. The runtime is **not**: the orchestrator calls the vendor's agent and session APIs directly, and engine delivery depends on their file mounting. | **H** | Extract the session lifecycle behind a `runtime.start() / send() / harvest()` interface, mirroring the store interface that already works. Same pattern, already proven in this codebase. |
| **Routing** | Single-model **by design**. 95% of turns are strategic reasoning against a confirmed plan, so only 6% of traffic is cheap-eligible at all, and switching models mid-conversation invalidates the prompt cache that saves 90% of input cost. Cascading is worth 0.06 margin points here — a non-lever (see `../03-the-margin/cost-curve.md`). | **H** | The exposure is portability, not cost. Add a per-stage model field so a provider swap has somewhere to land — justified as an exit seam, never as a saving. |
| **Eval** | None. There's *run-health* signal — per-figure source tags, a connection ledger, flag-and-hold on degraded runs, sourced-stats and pillar/ICP guardrails — but nothing scores output quality, so no model swap could be justified on evidence. | **H** | Freeze one verified tenant's knowledge base as a golden set and write a pass/fail check: required sections present, every figure source-tagged, nothing inferred in a gated field, every idea mapping to a confirmed pillar. Deliberately narrow — deterministic checks are what make an enforceable target, and they are enough to score a swap. **Specified in full in [`../04-the-contract/golden-dataset.md`](../04-the-contract/golden-dataset.md).** |

## Portability Score

**Locked** — with a documented but untested exit.

All four dimensions are H. Two things stop that being a crisis: the tenant store is genuinely portable and T&G-owned, and a specific escape hatch (self-hosted sandbox on T&G infrastructure) is named in the architecture. Neither has been exercised. Order of work to reach **Partial**: routing field (hours) → runtime interface (a day) → golden-set check (a day) → self-hosted-sandbox drill (a day).

### Three actions

- **This week:** per-stage model field — as a provider-swap seam, not to cascade.
- **This month:** runtime interface behind the store-interface pattern; golden-set eval.
- **This quarter:** self-hosted-sandbox drill on one tenant, then decide the lock-in question explicitly rather than by default.

## The lock-in is probably worth it — say so deliberately

Two capabilities are doing real product work, and both would have to be rebuilt on a self-hosted runtime:

1. **The credential vault.** Client secrets are substituted into outbound calls at egress and never enter the running agent, which is what makes "no T&G staff member can read your tokens" a true claim rather than a policy promise. A DIY secrets manager gives a weaker guarantee, because the agent would hold plaintext.
2. **Automatic prompt caching and context compaction.** The engine is a large, byte-identical prefix on every turn; the managed runtime serves it from cache at a tenth of base input cost and compacts long sessions without us building either. That's a margin feature, not a convenience.

So the honest position isn't "escape the vendor." It's **"stay, knowingly, and keep the exit tested"** — which requires the four actions above regardless.

## If the provider doubles pricing tomorrow

**48-hour response:**
1. Cut per-session input load — the engine is delivered as a large mounted file read into context; a leaner core with stage playbooks loaded on demand reduces what's paid for per turn. Cache reads are 65% of cost, so this is the only lever with real magnitude.
2. Drop effort from `xhigh` on the mechanical sessions. Unlike a model switch, effort is a generation-time parameter and does not invalidate the cache.
3. Nothing else — and specifically **not** cascading, which is worth 0.06 margin points here. Inference is under 1% of revenue at $2,500/tenant/month, so a 2× shock moves gross margin from ~93.6% to ~93.4%.

**The honest version:** this scenario doesn't threaten the business. The commercial model already carries the lever anyway — API cost bundled to a credit allowance, overage invoiced the following month with a 90% alert, no hard stop — so a genuine cost shock passes through without renegotiation. **Provider pricing is the wrong thing to worry about here; human oversight per tenant is the number that decides the margin.**

## If the provider ships a competing product

**Defensible:**
- The **PLAN layer** — confirmed strategy, pillars, calendar, budget and ROI — which the client confirms and owns, and which no generic agent arrives holding.
- The **attribution spine**: campaign IDs joining pillar → asset → traffic → enquiry → deal. Decision lineage that neither a model vendor nor a CRM models.
- **Per-tenant data** in T&G's own versioned store, with the integration gate across GA4 + Search Console + LinkedIn that no single platform owns end to end.
- The **cross-tenant benchmark plane** once it turns — the one asset that gets stronger as the client base grows.
- A named consultant accountable for the strategy. A services moat: real, and priced as services.

**Not defensible:** the engine itself. It's markdown, it descends from a public library, and it's the most copyable thing the business owns. It was made private to protect it, which was correct — and is also the tell. Stop describing it as the crown jewel.
