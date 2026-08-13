# Mariella — hosted, multi-tenant AI marketing engine for lean B2B teams.

> A living strategy built across 6 sessions. Each module adds one component. By Module 6, this repo IS the strategy, version-controlled, board-ready, portable.

---

## Strategy at a Glance

| Component | Module | Status | Key Artifact |
|-----------|--------|--------|-------------|
| **The Bet** | M1 | [x] | `01-the-bet/` |
| **The Moat** | M2 | [x] | `02-the-moat/` |
| **The Margin** | M3 | [ ] | `03-the-margin/` |
| **The Contract** | M4 | [x] | `04-the-contract/` |
| **The Guardrails** | M5 | [x] | `05-the-guardrails/` |
| **The Pitch** | M6 | [x] | `06-the-pitch/` |

---

## The Bet (M1)

**What we're building, for whom, why now.**

- **Product:** Mariella — hosted, multi-tenant AI marketing engine for lean B2B teams.
- **AI Value Archetype:** _(add: Automator / Copilot / Oracle / Creator / Orchestrator)_
- **Vulnerability Scores:** _(add: Moat _/5 · Data _/5 · Platform _/5)_
- **Top Risk:**
- **Confidence:** _(add: H / M / L)_
- **Prototype:**
- **Kill Criteria:**

→ Details: [`01-the-bet/`](01-the-bet/)

---

## The Moat (M2)

**Why this won't get copied in 6 months.**

- **Data Flywheel Score:**
- **Weakest Loop:**
- **Top Encroachment Threat:**
- **Encroachment Defense:** ship the server, onboard client #2, stand up the aggregation pipe.
- **Vendor Portability:** Partial — in build, not tested. Store is portable and ours; runtime sits behind an interface. The multi-tenant server — what lets learnings compound and lets us turn a client's access on or off — is still being built.

→ Details: [`02-the-moat/`](02-the-moat/)

---

## The Margin (M3)

**Will this make money or bleed it?**

- **Gross Margin (current):**
- **Gross Margin (AI-adjusted):**
- **Pricing Model:**
- **Pricing Today → Tomorrow:**
- **Total AI COGS / unit:**
- **Cascading Strategy:**
- **Net Margin Shift:**
- **Break-even at:**

→ Details: [`03-the-margin/`](03-the-margin/)

---

## The Contract (M4)

**Why users will trust a probabilistic system.**

- **Reliability Target:**
- **Golden Dataset:** 7 rows, __ adversarial
- **Confidence UX:** Tier on provenance (checkable at assembly), not the model's stated confidence.
- **HITL Architecture:** **Client approval gate** — covers every asset and never gets smaller. **Exception queue** — held runs, unsourced holds, injection flags, PLAN changes, first run for a client; must shrink, capped by the oversight budget, and recurring except…
- **Failure Mode Coverage:**

→ Details: [`04-the-contract/`](04-the-contract/)

---

## The Guardrails (M5)

**What breaks when this scales, and what compounds.**

- **Compounding System:** | Loop | Input | Output | Compounds? | Status | |------|-------|--------|-----------|--------| | Recursive Learning | approval edits, rejections | next run drops rejected hooks, resurfaces deferred ideas | Y | active | |…
- **Governance Posture:** all client-facing output; excludes internal staff AI use.
- **Autonomy Boundaries:** read and draft, auto. Publish, send and PLAN-amend, never auto. No write-back tool. Cross-client aggregation company-level only, and human approval required.
- **Escalation Triggers:** (1) held tier · (2) unsourced numeral · (3) injection flag · (4) PLAN change · (5) first run for a client · (6) gate-waiver request · (7) regulated claims.
- **Audit Cadence:** | When | Check | Owner |
- **Shadow AI Audit (user-side):**
- **Agent Boundaries:** | Agent | Can | Can't | Approval owner | |-------|-----|-------|----------------| | Orchestrator | run sessions, mount files, harvest output | read credentials, publish, cross a client | Brigette | | Consultant (setup) | research, write the…
- **Regulatory Exposure:** AU Privacy Act / APPs primary; GDPR if EU contacts; EU AI Act limited-risk. **Risk tier: limited.** Controls: email is drafted by the agent and the client remains sender of record; a golden-set regression gate on the qua…

→ Details: [`05-the-guardrails/`](05-the-guardrails/)

---

## The Pitch (M6)

**How you get this funded, shipped, and adopted.**

- **Horizon 1 (Now):** Close the consultant-to-client handover · Always-on host for the orchestrator · Orchestrator hardening and unattended cadence · Engine v7.6 join-first audit · Refusal path when no CRM is connected · Prove isolation and secret containment · Cost view and per-run metering · Finalise pricing and fix the collateral · Demand tests
- **Horizon 2 (Next):** Land the first paying client at $2,500 *(Margin)* · Migrate pilot client and onboard client #2 *(Moat)* · Wire GA4, Search Console and LinkedIn *(Bet)* · Credential model and per-tenant Vaults *(Guardrails)* · Onboarding and integration gate *(Contract)* · Client web interface *(Bet)* · Close the deal-outcome join *(Bet)* · Cut oversight to two hours per client *(Contract)* · Eval harness and acceptance metric *(Contract)* · COGS levers: caching and effort tuning *(Margin)* · Benchmark warehouse and priors *(Moat)* · Portability seam and escape-hatch drill *(Moat)* · Pre-pilot security, DPA and monitoring *(Guardrails)*
- **Horizon 3 (Bet):** Publishing autonomy *(Guardrails)* · Outcome-based pricing pilot *(Margin)*
- **Board Narrative:** A 1-3 person marketing team spending $200K-$1M a year can't fund the hire that would make that spend work, so we sell them that person's job, running.
- **Ask:** Capacity to ship the server, run the demand tests, and land the first clients over ~3 months, with a hard review at month 3 against the H2 kill lines.
- **Key Strategic Change:** margin 95% → ~80% with caching named as load-bearing, top vulnerability moved to differentiation, confidence split by claim, the "paying engagements" claim dropped, and four demand initiatives added b…

→ Details: [`06-the-pitch/`](06-the-pitch/)
