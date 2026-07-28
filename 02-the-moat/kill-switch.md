# Kill Switch Audit

**Product:** Mariella (Think & Grow) · **Date:** 2026-07-28
**The test:** could we swap AI providers in under 48 hours?

## Vendor Dependency Assessment

| Dimension | Current State | Risk Level | 48-Hour Action |
|-----------|--------------|------------|---------------|
| **Provider** | Anthropic, single, deep. Managed Agents runs the agent loop and the per-session sandbox; T&G owns only a Node orchestrator + versioned Agent configs. Engine delivery depends on CMA's Files API, and because CMA's file transfer carries a filename but never a folder, T&G encodes `/` as `~` to preserve structure — a workaround that exists solely because of this vendor. Secrets via per-tenant **Vaults: designed, not built.** Per-tenant S3 store is T&G-owned and portable. | **H** | Exercise the escape hatch that DECISIONS already names: run one tenant in CMA self-hosted-sandbox / EC2 mode and record what breaks. "EC2 is an escape hatch only" has never been tested, so it is an assumption, not a hatch. |
| **Abstraction** | Split, and the split is instructive. The durable store **is** properly abstracted — `localStore` / `S3Store` behind one async list/read/write interface, selected by `MARIELLA_STORE`. The runtime is **not**: `orchestrator/run-session.mjs` calls the SDK's beta agents + sessions APIs directly, and engine delivery is CMA-shaped end to end. | **H** | Extract the session lifecycle behind `runtime.start() / send() / harvest()`, mirroring the store interface that already works in this codebase. Same pattern, already proven here — a day's work. |
| **Routing** | None. One model for everything — the consultant's deep-research setup pass and the routine weekly refresh alike. **The model choice (Sonnet 5 vs Opus 4.8) was made on feel on 27 Jul with no cost view.** `main`'s agent configs say Opus 4.8; the live agents are at v7 while `main`'s lock is at v2, so the deployed model is not verifiable from the repo. | **H** | Verify which model the v7 agents actually run, then add a per-stage `model` field and route the mechanical stages (search-data refresh, integration maintenance, capture sweep, archive hygiene) to a cheap model. Keep the frontier model for PLAN work, audits and drafting. **This is W45 and it is Module 3's assignment.** |
| **Eval** | None. There is *run-health* signal — per-figure `[DATA:]` / `[INFERRED]` tags, the RESOLVED / FELL_BACK / INFERRED / ERROR connection ledger, flag-and-hold on degraded runs, SOURCED STATS and PILLAR/ICP guardrails — but nothing scores output quality, so no model swap could be justified and the Sonnet-vs-Opus question cannot be answered with evidence. | **H** | Freeze the verified `thinkandgrow` knowledge files as a golden set and write a pass/fail check: required sections present, every figure source-tagged, no `[INFERRED]` in a gated field, every idea maps to a confirmed pillar. Crude, but enough to score a swap — and enough to settle W45 on evidence instead of feel. |

## Portability Score

**Locked** — with a documented but untested exit.

All four dimensions are H. Two things stop that being a crisis: the per-tenant store is genuinely portable and T&G-owned, and an escape hatch (CMA self-hosted-sandbox / EC2) is named in the architecture decision. Neither has been exercised. Order of work to reach **Partial**: verify the live model + add the routing field (hours) → runtime interface (a day) → golden-set check (a day) → self-hosted-sandbox drill (a day).

**Separate but adjacent — availability, not portability:** the orchestrator runs **from a laptop today**. The always-on host is a plan (W70), targeting an AWS box reachable over SSM; because the orchestrator is an *interactive* CLI, a `systemd` service with no TTY hits stdin EOF and truncates the run. Forum: the **10 Aug Server Upgrades** session. A product whose delivery depends on one person's laptop being open has a bus-factor problem that no vendor swap fixes.

**Operational trap worth recording:** two Anthropic orgs share the display name "Think & Grow." A profile bound to the wrong one returns `404 Agent not found` on the agent IDs. The UUID is the only disambiguator. Bind a dedicated profile once.

### Three actions

- **This week:** verify the live model on the v7 agents; add the per-stage `model` field; cascade the mechanical stages.
- **This month:** runtime interface behind the store-interface pattern; golden-set eval; put a real cost figure behind the model choice (W45).
- **This quarter:** self-hosted-sandbox drill on one tenant; land the always-on host (10 Aug). Then decide explicitly whether the Vault egress-substitution guarantee is worth the lock-in — it probably *is*, which is a legitimate answer, but it should be a priced decision rather than an accident.

## If Anthropic doubles pricing tomorrow

**48-hour response:**
1. Cascade the mechanical stages to a cheap model (the Routing action above).
2. Cut the per-session input load. Mounting a ~116KB engine into every session pays frontier input rates for a prompt; the planned hardening (a <100k core system prompt + stage playbooks as on-demand skills) is a direct cost lever, not tidiness.
3. Freeze new onboarding until the pricing model has a usage lever.

**The uncomfortable part, twice over.** First, the exposure is new and self-inflicted: client-hosted, the client's own keys paid for inference and token price was someone else's problem; T&G-hosted, every token becomes T&G COGS against a fixed retainer. Second, **there is currently no cost view at all** — the model was chosen on feel, and leadership pricing collateral still describes EC2/Bedrock rather than CMA. So today the honest answer to "what happens if pricing doubles" is *we don't know*. **The pivot must not ship before the pricing model changes.**

## If Anthropic ships a competing product

**Defensible:**
- The **PLAN layer** — confirmed strategy, pillars, calendar, budget/ROI — which the client confirms and owns, and which no generic agent arrives holding.
- The **attribution spine**: campaign IDs joining pillar → asset → traffic → enquiry → deal. Decision lineage that neither a model vendor nor a CRM models.
- Per-tenant data in T&G's own versioned S3, with folder structure preserved in both directions (W67).
- A named consultant accountable for the strategy. A services moat — real, and it should be priced as services.

**Not defensible:** the engine prompt. It is markdown, it descends from a public library, and it is the most copyable thing T&G owns. It was made private on 22 Jul to protect it, which was correct — and is also the tell. Stop describing it as the crown jewel.
