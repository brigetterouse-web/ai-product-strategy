# Mariella — hosted, multi-tenant AI marketing engine for lean B2B teams.

> A living strategy built across 6 sessions. By Module 6, this repo IS the strategy — version-controlled, board-ready, portable.

---

## Strategy at a Glance

| Component | Module | Status | Key Artifact |
|-----------|--------|--------|-------------|
| **The Bet** | M1 | Done | `01-the-bet/` |
| **The Moat** | M2 | Done | `02-the-moat/` |
| **The Margin** | M3 | Done | `03-the-margin/` |
| **The Contract** | M4 | Done | `04-the-contract/` |
| **The Guardrails** | M5 | Done | `05-the-guardrails/` |
| **The Pitch** | M6 | Done | `06-the-pitch/` |

---

## The Bet (M1)

- **Product:** Mariella — hosted, multi-tenant AI marketing engine for lean B2B teams.
- **Archetype:** Orchestrator.
- **Vulnerability:** Moat 2/5 · Data 2/5 · Platform 2/5.
- **Top Risk:** differentiation — a client buys the outcome without needing it to be us.
- **Confidence:** M — ~85% ships · ~50% pay $2,500/mo · ~45% compounds.
- **Prototype:** engine proven end-to-end; multi-tenant runtime in build.
- **Kill Criteria:** rework >30% on two clients → consultant tool · oversight >4 hrs at month 3 → service · no benchmark in 6 mo → delivery tooling · >1 in 3 onboardings fail the gate → re-scope.

→ [`01-the-bet/`](01-the-bet/)

---

## The Moat (M2)

- **Flywheel Score:** 10/20 (Correction 3 · Preference 3 · Domain 3 · Network 1).
- **Weakest Loop:** Network — the loop HubSpot Breeze attacks.
- **Top Threat:** HubSpot Breeze — owns the CRM join key, already paid for.
- **Defense:** ship the server, onboard client #2, stand up the aggregation pipe.
- **Portability:** Partial — store is ours and portable; the server that compounds learnings and gates access is still in build.

→ [`02-the-moat/`](02-the-moat/)

---

## The Margin (M3)

- **Gross Margin:** ~75–80% ($2,500/mo vs $455–730 COGS, caching on).
- **AI-adjusted:** ~65–70% without caching. Oversight, not tokens, is the swing.
- **Pricing:** flat $2,500/mo + one-off onboarding (~$1,800). Untested.
- **Today → Tomorrow:** one flat seat ($180.89/mo) → $2,500/mo per tenant, metered + cached.
- **AI COGS / unit:** $75–200/mo with caching (3–5× without).
- **Cascading:** minimal (~95% frontier); real levers are oversight and caching.
- **Net Shift:** ~75–80% → ~90% as oversight falls to ~1 hr. Caching is load-bearing.
- **Break-even:** positive from client #1; none paying yet. Self-serve is negative.

→ [`03-the-margin/`](03-the-margin/)

---

## The Contract (M4)

- **Reliability Target:** 0% unsourced · 100% plan adherence · ≥70% first-pass · ≥98% cadence · <0.5%/wk drift. Targets — no harness runs them yet (MAR-56).
- **Golden Dataset:** 7 rows, 4 adversarial.
- **Confidence UX:** tier on provenance, not the model's stated confidence.
- **HITL:** approval gate on every asset, never smaller; exception queue must shrink and seeds golden rows.
- **Failure Coverage:** no-plan refusal, unsourced omission, injection, fabrication, cross-client leakage, gate-skip. In design; unproven until the harness runs.

→ [`04-the-contract/`](04-the-contract/)

---

## The Guardrails (M5)

- **Compounding:** 5 loops — Recursive + Cross-Domain active; Attribution broken (deal-join not closed); Network + eval missing. Fix: gate the deal-join at onboarding.
- **Governance:** all client-facing output; excludes internal staff use.
- **Autonomy:** read/draft auto; publish, send, PLAN-amend never auto; no write-back.
- **Escalation:** held tier · unsourced numeral · injection · PLAN change · first run · gate-waiver · regulated claims.
- **Audit:** assembly rule checks (Brigette) · weekly judge (Alex) · monthly tier review (Brigette) · quarterly privacy (Alex).
- **Shadow AI:** 5 workarounds — build 1, partner 2, ignore 1, re-open M4 1. Adjacent spend ~$90–160/client/mo.
- **Agents:** Orchestrator, Consultant, Client — each scoped; Brigette approves.
- **Regulatory:** AU Privacy Act primary; GDPR if EU contacts; EU AI Act limited-risk. Email drafted, client is sender of record.

→ [`05-the-guardrails/`](05-the-guardrails/)

---

## The Pitch (M6)

- **H1 (Now):** handover · always-on host · orchestrator hardening · join-first audit · no-CRM refusal path · isolation + secret containment · cost view + metering · pricing + collateral · demand tests.
- **H2 (Next):** first paying client at $2,500 *(Margin)* · migrate pilot + onboard #2 *(Moat)* · wire GA4/GSC/LinkedIn *(Bet)* · credential model + Vaults *(Guardrails)* · onboarding + integration gate *(Contract)* · client web UI *(Bet)* · close the deal-join *(Bet)* · oversight ≤2 hrs *(Contract)* · eval harness *(Contract)* · caching + effort tuning *(Margin)* · benchmark warehouse *(Moat)* · portability drill *(Moat)* · pre-pilot security + DPA *(Guardrails)*.
- **H3 (Bet):** publishing autonomy *(Guardrails)* · outcome-based pricing pilot *(Margin)*.
- **Narrative:** a 1–3 person marketing team spending $200K–$1M a year can't fund the hire that makes that spend work, so we sell them that person's job, running.
- **Ask:** capacity to ship the server, run demand tests, and land first clients over ~3 months, hard review at month 3 against the H2 kill lines.
- **Key Change:** margin 95% → ~80% (caching load-bearing) · top vulnerability moved to differentiation · confidence split by claim · "paying engagements" dropped · four demand initiatives added.

→ [`06-the-pitch/`](06-the-pitch/)
