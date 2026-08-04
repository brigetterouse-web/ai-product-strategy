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
| **The Contract** | M4 | [ ] | `04-the-contract/` |
| **The Guardrails** | M5 | [ ] | `05-the-guardrails/` |
| **The Pitch** | M6 | [ ] | `06-the-pitch/` |

---

## The Bet (M1)

**What we're building, for whom, why now.**

- **Product:** Mariella — a living marketing PLAN that PRODUCEs every asset against it and attributes the result back to a deal. For lean marketing teams of 1–3 at $200K–$1M+ spend; multi-tenant, T&G-hosted. Displaces a $120–180k/yr content hire.
- **AI Value Archetype:** Orchestrator (Copilot surface, Creator output)
- **Vulnerability Scores:** Moat **4**/5 · Data **4**/5 · Platform **2**/5
- **Top Risk:** Three of four learning loops compound inside a tenant and the fourth barely compounds across them — the product gets better for every client it serves while the asset doing the work is portable text on the runtime of the vendor most likely to replace it.
- **Confidence:** **M**
- **Prototype:** the hosted multi-tenant runtime — per-tenant isolated stores, client credentials vaulted so no staff member can read them, proven end to end on a full setup pass. The open action is a client-facing demo — see `01-the-bet/prototype.md`
- **Kill Criteria:** >30% rework on two consecutive tenants · human oversight >4 hrs/tenant/month · no benchmark plane by 31 Dec 2026 · >1 in 3 onboardings fail the integration gate

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
- **Pricing Model:** decided 22 Jul — subscription (not one-off; a $20–30k one-off was rejected), **13-month contract at the 12-month price** (first month as cooling-off, securing a 12-month commitment), API cost bundled into the base up to a **$120/month credit allowance** (revised up from $25 once real usage was measured), **overage invoiced the following month** with an alert at 90% rather than a hard stop.
- **Cascading Strategy:** **does not apply to this product.** The realistic ratio is ~5% cheap / 95% frontier, not 70/30 — models are session-scoped on Managed Agents, switching them destroys the caching that saves 90%, and by the routing rule almost every session is strategy or client-facing copy. Worth **$1.40/tenant/month (0.06 points)**. The real decision is a whole-product model choice (Opus vs Sonnet 5, **41% measured**, ~$24/tenant/month), and the better levers are **effort tuning** and **session length** — cache reads are 65% of cost and compound within a session.
- **Break-even at:** infrastructure is recovered by **well under one tenant** (the $19/mo box against $2,310/tenant/month of contribution). Payback against the platform build cost is unquantified — build cost is not yet costed.
- **The real risk:** human oversight, not tokens. One hour per tenant per month holds 92%; four hours takes it to **77%**. A $300 self-serve tier lands at **68%**, and **49%** on a heavy tenant — the argument for pricing against a salary, not a seat.

→ Details: [`03-the-margin/`](03-the-margin/)

---

## The Contract (M4)

**Why users will trust a probabilistic system.**

- **Reliability Target:**
- **Golden Dataset:** __ rows, __ adversarial
- **Confidence UX:** [approach]
- **HITL Architecture:**
- **Failure Mode Coverage:**

→ Details: [`04-the-contract/`](04-the-contract/)

---

## The Guardrails (M5)

**What breaks when this scales — and what compounds.**

- **Compounding System:** [describe feedback loops]
- **Governance Posture:** [approach]
- **Shadow AI Status:** __ tools found, __ triaged
- **Agent Boundaries:**
- **Regulatory Exposure:**

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
