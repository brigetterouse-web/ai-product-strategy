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
| **The Margin** | M3 | [ ] | `03-the-margin/` |
| **The Contract** | M4 | [ ] | `04-the-contract/` |
| **The Guardrails** | M5 | [ ] | `05-the-guardrails/` |
| **The Pitch** | M6 | [ ] | `06-the-pitch/` |

---

## The Bet (M1)

**What we're building, for whom, why now.**

- **Product:** Mariella — a living marketing PLAN that PRODUCEs every asset against it and attributes the result back to a deal. For lean marketing teams of 1–3 at $200K–$1M+ spend; multi-tenant, T&G-hosted. Displaces a $120–180k/yr content hire.
- **AI Value Archetype:** Orchestrator (Copilot surface, Creator output)
- **Vulnerability Scores:** Moat **4**/5 · Data **4**/5 · Platform **2**/5
- **Top Risk:** Three of four learning loops are strong inside a tenant and the fourth is zero across them — the product gets better for every client it serves and never better as a company, while the asset doing the work is portable text on the runtime of the vendor most likely to replace it.
- **Confidence:** **M**
- **Live today:** T&G-operated on the client-hosted path — **Wink Models** (audit delivered 26 Jun off real data; Klaviyo + GA4 connected) and **Think & Grow** (CJ Robinson, daily power user: 90-day strategy, event ROI, content plans, scheduled tasks). The T&G-hosted platform is the migration target and is half-built.
- **Prototype:** a product in use, not a mock. Recorded walk-through exists; the open action is a client-facing demo — see `01-the-bet/prototype.md`
- **Kill Criteria:** >30% rework on two consecutive tenants · AI COGS >25% of retainer at target usage · no aggregation plane by 31 Dec 2026 · integrations not live by 30 Sep 2026

→ Details: [`01-the-bet/`](01-the-bet/)

---

## The Moat (M2)

**Why this won't get copied in 6 months.**

- **Data Flywheel Score:** **13**/20 — Correction 4 · Preference 4 · Domain Context 4 · Network 1
- **Weakest Loop:** Network (**1/5 today, designed for 4**) — nothing crosses a tenant boundary yet, but the cross-client benchmark is a genuine network effect and the only loop that would make Mariella compound as a company. The strong version isn't the benchmark clients *read* (that saturates) — it's cross-tenant priors feeding the PLAN layer.
- **Competitive Position:** genuine workflow layer. PLAN/PRODUCE gives real cross-domain transfer inside an account, and the living-strategy amend loop lets corrections change the plan rather than just the next output. All of it compounds per tenant; none across them.
- **Encroachment Defense:** ship the integrations (the data story is inference-only until then); own cross-platform where HubSpot can only attribute what passes through HubSpot; own PLAN and concede the CRM; ship the benchmark loop before the category is defined; price the consultant as services; stop calling the engine prompt the IP.
- **Vendor Portability:** **Locked** (documented but untested exit)

**The one-sentence moat summary:** Mariella's moat is not the engine — it is the PLAN layer plus the campaign-ID attribution spine, and it only becomes a *product* moat when learnings start compounding across tenants.

→ Details: [`02-the-moat/`](02-the-moat/)

---

## The Margin (M3)

**Will this make money or bleed it?**

- **Gross Margin (current):**
- **Gross Margin (AI-adjusted):**
- **Pricing Model:** decided 22 Jul — subscription (not one-off; a $20–30k one-off was rejected), **13-month contract at the 12-month price** (first month as cooling-off, securing a 12-month commitment), API cost bundled into the base up to a credit allowance, **overage invoiced the following month** with an alert at 90% rather than a hard stop.
- **Cascading Strategy:** none today — one frontier model for every stage. See the Routing row in `02-the-moat/kill-switch.md`.
- **Break-even at:** unknown — **no cost view exists** (model chosen on feel, 27 Jul). This is W45 and it is this module's work.

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
