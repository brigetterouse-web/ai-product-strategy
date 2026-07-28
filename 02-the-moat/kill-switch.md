# Kill Switch Audit

**Product:** Mariella (Think & Grow) · **Date:** 2026-07-28
**The test:** could we swap AI providers in under 48 hours?

## Vendor Dependency Assessment

| Dimension | Current State | Risk Level | 48-Hour Action |
|-----------|--------------|------------|---------------|
| **Provider** | Anthropic, single, deep. Managed Agents runs the agent loop and the per-session sandbox; T&G owns only a Node orchestrator + versioned Agent configs. Engine delivery depends on CMA's Files API, and because CMA's file transfer carries a filename but never a folder, T&G encodes `/` as `~` to preserve structure — a workaround that exists solely because of this vendor. Secrets via per-tenant **Vaults: designed, not built** — so on the live client-hosted path, client credentials are today long-lived API keys and private-app tokens held directly by T&G (see the secrets note below). Per-tenant S3 store is T&G-owned and portable. | **H** | Exercise the escape hatch that DECISIONS already names: run one tenant in CMA self-hosted-sandbox / EC2 mode and record what breaks. "EC2 is an escape hatch only" has never been tested, so it is an assumption, not a hatch. |
| **Abstraction** | Split, and the split is instructive. The durable store **is** properly abstracted — `localStore` / `S3Store` behind one async list/read/write interface, selected by `MARIELLA_STORE`. The runtime is **not**: `orchestrator/run-session.mjs` calls the SDK's beta agents + sessions APIs directly, and engine delivery is CMA-shaped end to end. | **H** | Extract the session lifecycle behind `runtime.start() / send() / harvest()`, mirroring the store interface that already works in this codebase. Same pattern, already proven here — a day's work. |
| **Routing** | None. One model for everything — the consultant's deep-research setup pass and the routine weekly refresh alike. **The model choice (Sonnet 5 vs Opus 4.8) was made on feel on 27 Jul with no cost view.** `main`'s agent configs say Opus 4.8; the live agents are at v7 while `main`'s lock is at v2, so the deployed model is not verifiable from the repo. | **H** | Verify which model the v7 agents actually run, then add a per-stage `model` field and route the mechanical stages (search-data refresh, integration maintenance, capture sweep, archive hygiene) to a cheap model. Keep the frontier model for PLAN work, audits and drafting. **This is W45 and it is Module 3's assignment.** |
| **Eval** | None. There is *run-health* signal — per-figure `[DATA:]` / `[INFERRED]` tags, the RESOLVED / FELL_BACK / INFERRED / ERROR connection ledger, flag-and-hold on degraded runs, SOURCED STATS and PILLAR/ICP guardrails — but nothing scores output quality, so no model swap could be justified and the Sonnet-vs-Opus question cannot be answered with evidence. | **H** | Freeze the verified `thinkandgrow` knowledge files as a golden set and write a pass/fail check: required sections present, every figure source-tagged, no `[INFERRED]` in a gated field, every idea maps to a confirmed pillar. Crude, but enough to score a swap — and enough to settle W45 on evidence instead of feel. |

## Portability Score

**Locked** — with a documented but untested exit.

All four dimensions are H. Two things stop that being a crisis: the per-tenant store is genuinely portable and T&G-owned, and an escape hatch (CMA self-hosted-sandbox / EC2) is named in the architecture decision. Neither has been exercised. Order of work to reach **Partial**: verify the live model + add the routing field (hours) → runtime interface (a day) → golden-set check (a day) → self-hosted-sandbox drill (a day).

**Separate but adjacent — availability, not portability:** the orchestrator runs **from a laptop today**. The always-on host is a plan (W70), targeting an AWS box reachable over SSM; because the orchestrator is an *interactive* CLI, a `systemd` service with no TTY hits stdin EOF and truncates the run. Forum: the **10 Aug Server Upgrades** session. A product whose delivery depends on one person's laptop being open has a bus-factor problem that no vendor swap fixes.

**Operational trap worth recording:** two Anthropic orgs share the display name "Think & Grow." A profile bound to the wrong one returns `404 Agent not found` on the agent IDs. The UUID is the only disambiguator. Bind a dedicated profile once.

**Secrets — the gap between the promise and the practice.** The Vault design exists precisely because the product's security story is "the credential never enters the AI, and no T&G human can read it." On the live path today that is not yet true: client integrations run on long-lived read-only API keys and private-app tokens that T&G holds, and at least one client's Klaviyo key and HubSpot token are sitting in plaintext in a shared onboarding spreadsheet — the same document whose client-facing copy promises "revocable integrations rather than holding any of your passwords." Rotate and strip before this becomes an M4 trust question or an M5 governance finding. Tracked internally as SEC-1.

### Three actions

- **This week:** verify the live model on the v7 agents; add the per-stage `model` field; cascade the mechanical stages.
- **This month:** runtime interface behind the store-interface pattern; golden-set eval; put a real cost figure behind the model choice (W45).
- **This quarter:** self-hosted-sandbox drill on one tenant; land the always-on host (10 Aug). Then decide explicitly whether the Vault egress-substitution guarantee is worth the lock-in — it probably *is*, which is a legitimate answer, but it should be a priced decision rather than an accident.

## If Anthropic doubles pricing tomorrow

**48-hour response:**
1. Cascade the mechanical stages to a cheap model (the Routing action above).
2. Cut the per-session input load. Mounting a ~116KB engine into every session pays frontier input rates for a prompt; the planned hardening (a <100k core system prompt + stage playbooks as on-demand skills) is a direct cost lever, not tidiness.
3. Freeze new onboarding until the pricing model has a usage lever.

**The exposure is new, and the commercial model already anticipates it — but the number behind it doesn't exist.** Hosting moves inference from the client's own keys onto T&G's P&L. The pricing model agreed on 22 Jul does contain a usage lever: subscription, 13 months for the price of 12, API cost bundled into the base up to a credit allowance, **overage invoiced the following month rather than hard-stopped, with an alert at 90% of the allowance**. That is the right structure.

What's missing is the allowance itself. **There is no cost view** — the model was chosen on feel on 27 Jul, so the credit threshold, the overage rate and the margin at target usage are all unset, and leadership collateral still describes EC2/Bedrock rather than the actual runtime. So the honest answer to "what if pricing doubles" is *the structure absorbs it; we don't yet know at what price*. **W45 — putting a real cost figure behind the model choice — is the blocker, and it is Module 3's work.**

## If Anthropic ships a competing product

**Defensible:**
- The **PLAN layer** — confirmed strategy, pillars, calendar, budget/ROI — which the client confirms and owns, and which no generic agent arrives holding.
- The **attribution spine**: campaign IDs joining pillar → asset → traffic → enquiry → deal. Decision lineage that neither a model vendor nor a CRM models.
- Per-tenant data in T&G's own versioned S3, with folder structure preserved in both directions (W67).
- A named consultant accountable for the strategy. A services moat — real, and it should be priced as services.

**Not defensible:** the engine prompt. It is markdown, it descends from a public library, and it is the most copyable thing T&G owns. It was made private on 22 Jul to protect it, which was correct — and is also the tell. Stop describing it as the crown jewel.
