# Mariella — hosted, multi-tenant AI marketing engine for lean B2B teams.

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

*What we're building, for whom, why now.*

- **Product:** Mariella — hosted, multi-tenant AI marketing engine for lean B2B teams.
- **AI Value Archetype:** Orchestrator.
- **Vulnerability Scores:** Moat 2/5 · Data 2/5 · Platform 2/5.
- **Top Risk:** differentiation — a client buys the outcome without needing it to be us.
- **Confidence:** M — ~65% if we ship the server, ~25% if it stays as is.
- **Prototype:** [link pending — 60-second capture of a live tenant run]; engine proven end-to-end, multi-tenant runtime in build.
- **Kill Criteria:** rework >30% on two clients → consultant tool · oversight >4 hrs at month 3 → service · no benchmark in 6 mo → delivery tooling · >1 in 3 onboardings fail the gate → re-scope.

→ [`01-the-bet/`](01-the-bet/)

---

## The Moat (M2)

*Why this won't get copied in 6 months.*

- **Data Flywheel Score:** 10/20 (Correction 3 · Preference 3 · Domain 3 · Network 1).
- **Weakest Loop:** Network — the loop HubSpot Breeze attacks.
- **Competitive Position:** weak across all three axes (Moat 2 · Data 2 · Platform 2); we place on cohort relevance and a client-owned PLAN, not on data volume (Semrush) or platform control (Anthropic). Top adjacent threat: HubSpot Breeze, which owns the CRM join key and is already paid for.
- **Encroachment Defense:** ship the server, onboard client #2, stand up the aggregation pipe.
- **Vendor Portability:** Partial — store is ours and portable; the server that compounds learnings and gates access is still in build.

→ [`02-the-moat/`](02-the-moat/)

---

## The Margin (M3)

*Will this make money or bleed it?*

- **Gross Margin (current):** ~75–80% ($2,500/mo vs $455–730 COGS, caching on), rising to ~90% as oversight falls to ~1 hr.
- **Gross Margin (AI-adjusted):** ~65–70% without caching — oversight, not tokens, is the swing.
- **Pricing Model:** flat $2,500/mo + one-off onboarding (~$1,800); hybrid base + metered overage; untested.
- **Cascading Strategy:** minimal (~95% frontier); the real levers are oversight hours and caching.
- **Break-even at:** positive per client from client #1 ($2,500 vs $455–730 COGS); none paying yet, so unrealised. Self-serve is negative.

→ [`03-the-margin/`](03-the-margin/)

---

## The Contract (M4)

*Why users will trust a probabilistic system.*

- **Reliability Target:** 0% unsourced · 100% plan adherence · ≥70% first-pass · ≥98% cadence · <0.5%/wk drift. Targets — no harness runs them yet (MAR-56).
- **Golden Dataset:** 7 rows, 4 adversarial.
- **Confidence UX:** tier on provenance, not the model's stated confidence.
- **HITL Architecture:** approval gate on every asset, never smaller; exception queue must shrink and seeds golden rows.
- **Failure Mode Coverage:** no-plan refusal, unsourced omission, injection, fabrication, cross-client leakage, gate-skip. In design; unproven until the harness runs.

→ [`04-the-contract/`](04-the-contract/)

---

## The Guardrails (M5)

*What breaks when this scales, and what compounds.*

- **Compounding System:** 5 loops — Recursive + Cross-Domain active; Attribution broken (deal-join not closed); Network + eval missing. Fix: gate the deal-join at onboarding.
- **Governance Posture:** covers all client-facing output (excludes internal staff use); read and draft are automatic, publish/send/PLAN-amend never are, no write-back tool; escalates on held tier, unsourced numeral, injection, PLAN change, first run, gate-waiver or regulated claims; audited at assembly, weekly, monthly and quarterly.
- **Shadow AI Audit (user-side):** 5 workarounds — 1 build, 2 partner, 1 ignore, 1 TBD. Estimated hidden spend ~$90–160/client/mo (est., not surveyed).
- **Agent Boundaries:** Orchestrator, Consultant and Client agents, each scoped to what it can and can't do; Brigette and Alex approve.
- **Regulatory Exposure:** AU Privacy Act primary; GDPR if EU contacts; EU AI Act limited-risk. Email is drafted and the client stays sender of record.

→ [`05-the-guardrails/`](05-the-guardrails/)

---

## The Pitch (M6)

*How you get this funded, shipped, and adopted.*

- **Horizon 1 (Now):** handover · always-on host · orchestrator hardening · join-first audit · no-CRM refusal path · isolation + secret containment · cost view + metering · pricing + collateral · demand tests.
- **Horizon 2 (Next):** first paying client at $2,500 *(Margin)* · migrate pilot + onboard #2 *(Moat)* · wire GA4/GSC/LinkedIn *(Bet)* · credential model + Vaults *(Guardrails)* · onboarding + integration gate *(Contract)* · client web UI *(Bet)* · close the deal-join *(Bet)* · oversight ≤2 hrs *(Contract)* · eval harness *(Contract)* · caching + effort tuning *(Margin)* · benchmark warehouse *(Moat)* · portability drill *(Moat)* · pre-pilot security + DPA *(Guardrails)*.
- **Horizon 3 (Bet):** publishing autonomy *(Guardrails)* · outcome-based pricing pilot *(Margin)*.
- **Board Narrative:** a 1–3 person marketing team spending $200K–$1M a year can't fund the hire that makes that spend work, so we sell them that person's job, running.
- **Key Metric:** first paying client signed at $2,500 within 3 months — the one number that proves demand, which doesn't exist yet.

→ [`06-the-pitch/`](06-the-pitch/)
