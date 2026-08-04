# Mariella — AI Product Strategy

> A living strategy built across 6 sessions. Each module adds one component. By Module 6, this repo IS your strategy — version-controlled, board-ready, portable.

**Product:** Mariella — a multi-tenant AI marketing engine for B2B professional-services firms (Think & Grow).
**Owner:** Brigette Rouse · **Path:** B — AI-native.

---

## Strategy at a Glance

| Component | Module | Status | Key Artifact |
|-----------|--------|--------|-------------|
| **The Bet** | M1 | [x] | `01-the-bet/` |
| **The Moat** | M2 | [x] | `02-the-moat/` |
| **The Margin** | M3 | [x] | `03-the-margin/` |
| **The Contract** | M4 | [x] | `04-the-contract/` |
| **The Guardrails** | M5 | [x] | `05-the-guardrails/` |
| **The Pitch** | M6 | [ ] | `06-the-pitch/` |

---

## The Bet (M1)

**What we're building, for whom, why now.**

- **Product:** Mariella — a living marketing PLAN that PRODUCEs every asset against it and attributes the result back to a deal. For lean marketing teams of 1–3 at $200K–$1M+ spend; multi-tenant, T&G-hosted. Priced against a $120–180k/yr content hire.
- **AI Value Archetype:** Orchestrator (Copilot surface, Creator output)
- **Demand type:** **non-consumption win** — the ICP mostly can't fund that hire, so the behaviour being sold didn't previously exist at a price they could pay. Competing against nothing happening, not against an incumbent.
- **Vulnerability Scores:** Moat **4**/5 · Data **4**/5 · Platform **2**/5
- **Top Risk:** Three of four learning loops compound inside a tenant and the fourth barely compounds across them — the product gets better for every client it serves while the asset doing the work is portable text on the runtime of the vendor most likely to replace it.
- **Confidence:** **M** — ~**85%** on the service bet (sells and delivers at this price) · ~**60%** on the product bet (compounds rather than staying delivery tooling)
- **Prototype:** the hosted multi-tenant runtime — per-tenant isolated stores, client credentials vaulted so no staff member can read them, proven end to end on a full setup pass. The open action is a client-facing demo — see `01-the-bet/prototype.md`
- **Kill Criteria:** >30% rework on two consecutive tenants · human oversight >4 hrs/tenant/month · no benchmark plane within six months of hosted launch · >1 in 3 onboardings fail the integration gate

→ Details: [`01-the-bet/`](01-the-bet/)

---

## The Moat (M2)

**Why this won't get copied in 6 months.**

- **Data Flywheel Score:** **14**/20 — Correction 4 · Preference 4 · Domain Context 4 · Network 2
- **Weakest Loop:** Network (**2/5**) — the cross-tenant benchmark is a genuine network effect and the only loop that makes Mariella compound as a company rather than per client. The strong version isn't the benchmark clients *read* (that saturates) — it's cross-tenant priors feeding the PLAN layer.
- **Competitive Position:** genuine workflow layer. PLAN/PRODUCE gives real cross-domain transfer inside an account, and the living-strategy amend loop lets corrections change the plan rather than just the next output. Almost all of it compounds per tenant; barely any across them.
- **Encroachment Defense:** ship the benchmark loop before the category is defined; own cross-platform where HubSpot can only attribute what passes through HubSpot; own PLAN and concede the CRM; compete on cohort relevance rather than sample size; price the consultant as services; stop calling the engine the IP.
- **Vendor Portability:** **Locked** (documented but untested exit)

**The one-sentence moat summary:** Mariella's moat is not the engine — it is the PLAN layer plus the campaign-ID attribution spine, and it only becomes a *product* moat when learnings start compounding across tenants.

→ Details: [`02-the-moat/`](02-the-moat/)

---

## The Margin (M3)

**Will this make money or bleed it?**

- **Gross Margin (current):** services delivery — not separately quantified; growth is headcount-bound, so revenue and cost scale together.
- **Gross Margin (AI-adjusted):** **92.2%** at expected volume ($2,500 revenue vs $194 COGS). Range **89.9–93.6%** across light and heavy tenants. Of that COGS, **$59 is AI and $130 is one hour of human oversight**.
- **Cost per turn:** **$0.21 measured** from real production sessions (`sessions.retrieve().usage`), not estimated. Prompt caching verified working — saving ~90% on the largest line.
- **Feature split:** Leader (PLAN + cadence) $35/mo · Filler (reports, visibility check) $3.50/mo · Killer recurring (campaign production) $18/mo · Killer one-off (consultant setup) $3.46 measured, charged as an onboarding fee.
- **Pricing Model:** subscription (not one-off; a $20–30k one-off was rejected), **13-month contract at the 12-month price** (first month as cooling-off, securing a 12-month commitment), API cost bundled into the base up to a **$120/month credit allowance** (sized against measured usage), **overage invoiced the following month** with an alert at 90% rather than a hard stop.
- **Cascading Strategy:** **does not apply to this product.** The realistic ratio is ~5% cheap / 95% frontier, not 70/30 — models are session-scoped on Managed Agents, switching them destroys the caching that saves 90%, and by the routing rule almost every session is strategy or client-facing copy. Worth **$1.40/tenant/month (0.06 points)**. The real decision is a whole-product model choice (Opus vs Sonnet 5, **41% measured**, ~$24/tenant/month), and the better levers are **effort tuning** and **session length** — cache reads are 65% of cost and compound within a session.
- **Break-even at:** infrastructure is recovered by **well under one tenant** (the $19/mo box against $2,310/tenant/month of contribution). Payback against the platform build cost is unquantified — build cost is not yet costed.
- **The real risk:** human oversight, not tokens. One hour per tenant per month holds 92%; four hours takes it to **77%**. A $300 self-serve tier lands at **68%**, and **49%** on a heavy tenant — the argument for pricing against a salary, not a seat.

→ Details: [`03-the-margin/`](03-the-margin/)

---

## The Contract (M4)

**Why users will trust a probabilistic system.**

- **The stake:** the client publishes Mariella's output under their own brand, so a confident error is not a bad answer — it is **a false claim in market**. Air Canada's tribunal held that a chatbot speaks for the brand; the equivalent here is a fabricated statistic in a published asset. Mariella therefore **competes on receipts, not fluency** — fluency is what model vendors ship for free.
- **Golden Dataset:** **12 rows** at v1, **5 adversarial** (prompt injection via ingested competitor content, pressure to fabricate a market-leader stat, cross-tenant data extraction, tampered tenant knowledge file, instruction to waive the approval gate). Frozen from one verified tenant, versioned like code, path to ~150 via promoted corrections.
- **Confidence UX:** **tier on provenance, not self-reported confidence** — a model asserts 95% about an invented figure as readily as a sourced one, so a confidence bar built on it manufactures trust instead of earning it. Three tiers computed at assembly: **Derived** (fully sourced, mapped to a pillar, campaign ID assigned) · **Flagged** (inference marked inline, source ledger shown) · **Held** (missing plan input, dead connection, or a figure that would have to be invented — no asset produced, reason stated).
- **Reliability Contract:** **0%** unsourced figures in client-facing output (deterministic check, so zero is enforceable) · **100%** plan adherence · **≥70%** first-pass acceptance · **≤1 hr/tenant/month** oversight · **≥98%** cadence reliability · **<0.5%/wk** drift. Latency p95 deliberately dropped — a scheduled cadence with approval gates has no meaningful p95; cadence reliability is the equivalent promise.
- **HITL Architecture:** **two loops moving in opposite directions.** The client approval gate covers every asset and **never shrinks** — it is the trust product and the reason "the client owns the strategy" is true. The consultant exception queue **must shrink**, capped by the ≤1 hr/tenant/month margin budget. Both are HITL; only one is a cost.
- **Closes M2's open gap:** Eval scored **H / "None"** in the kill-switch audit. This artifact is the specification that closes it, and the precondition for portability moving from **Locked** toward **Partial**.

→ Details: [`04-the-contract/`](04-the-contract/)

---

## The Guardrails (M5)

**What breaks when this scales — and what compounds.**

- **Compounding System:** **five loops — 2 active, 1 broken, 2 missing.** Recursive learning and cross-domain transfer are genuinely active *within* a tenant. **Attribution learning is broken**: campaign IDs are minted at publish but the deal outcome never returns where CRM connectivity is partial, so the engine recommends on engagement proxies while the ROI signal sits unjoined. Network intelligence and the eval loop are **missing** — and they are the only two that compound at company level, one shared pipe away from both.
- **Freeze Test:** frozen three months, Mariella **still improves for an existing tenant** (signals and PLAN keep accumulating, independent of any model upgrade) and **learns nothing transferable as a company** — tenant three would onboard at exactly tenant one's quality. **Verdict: compounds per client, scales as a company.** Reproduces the M2 flywheel finding by an independent route.
- **Governance Posture:** **Level 2 → Level 3.** Governance is GTM for this product specifically, because the client publishes the output under their own brand — "show me how you test this" is the purchase decision, not a procurement formality. Two artifacts already sell: the Held-tier distribution showing the engine declining when it should, and the credential vault making "no staff member can read your tokens" structural rather than promised.
- **Agent Boundaries:** read and draft auto · **publish, send and PLAN amendment never auto** · **no write-back tool exists in the allow-list at all**, removing a whole class of irreversible action rather than governing it · shared cross-tenant memory permitted **only in aggregate**, which is what makes the network loop legal to build · PLAN-FIRST gate doubles as the stop-the-chain trigger.
- **Shadow AI Status:** **5 workarounds — 1 build · 2 partner · 1 re-opens M4 · 1 ignore.** Adjacent spend **~$90–160/tenant/month (modelled)**, which at 4–6% of the subscription is not a pricing threat — the finding is *shape*: three of five are Mariella's output being carried somewhere else, so the product boundary is drawn one step short of where the work finishes. The **trust-gap** row (users re-verifying an already-sourced figure) is the one that matters, because it reports a weakness in something already shipped.
- **Regulatory Exposure:** EU AI Act **limited risk** (transparency satisfied structurally by the approval gate) · **Australian Privacy Act / APPs** as the primary regime · GDPR where a tenant holds EU contacts · **email drafted never sent, so the client stays sender of record** — a deliberate allocation of liability, not an accident of design.

→ Details: [`05-the-guardrails/`](05-the-guardrails/)

---

## The Pitch (M6)

**How you get this funded, shipped, and adopted.**

- **Horizon 1 (Now):**
- **Horizon 2 (Next):**
- **Horizon 3 (Bet):**
- **Board Narrative:** [1-sentence thesis]
- **Key Metric:**

→ Details: [`06-the-pitch/`](06-the-pitch/)
