# Three-Axis Diagnostic

**Product:** Mariella — a multi-tenant AI marketing engine for lean B2B marketing teams (Think & Grow)
**Engine versions:** consultant v7.5 / client v8.0 · **Operating model:** PLAN & PRODUCE (2 modes)
**Path:** B — AI-native. The intelligence is the product, not a sidebar.
**Dominant archetype:** Orchestrator (Copilot surface, Creator output)
**Date:** 2026-07-28

**ICP:** Australian-focused. Lean marketing teams of 1–3, $200K–$1M+ annual marketing spend, AI-literate and actively avoiding "AI slop." Two-buyer GTM: the founder buys *desire + speed*, the marketer buys *the data story*. The alternative it displaces is a **$120–180k/yr content hire**.

> Scored 1 = pain, 5 = strong. Calibration: Figma = deep moat, thin ChatGPT wrapper = shallow.

| Axis | Score |
|------|-------|
| Contextual Moat | **4**/5 |
| Data Advantage | **4**/5 |
| Platform Exposure | **2**/5 |

---

## 1. Contextual Moat — 4/5

**Workflow depth × switching cost.**

**Rationale:** Mariella is not a content generator with a knowledge base. It runs a **two-mode operating model**: PLAN owns the living decision layer — confirmed strategy, content pillars, the content + event calendar, budget and per-event ROI, campaign and lead-magnet plans — and PRODUCE derives every asset (post, ad, lead magnet, email, website copy, testimonial) *from* that plan, through a PLAN-FIRST gate that refuses to fabricate a pillar to proceed. Every PLAN item that will publish gets a **stable campaign ID** that threads content → traffic → enquiry → deal across the attribution spine.

That is a workflow layer, not an embedded feature. Switching means abandoning the confirmed strategy, the pillar set, the calendar, the campaign-ID history and the attribution lineage — i.e. rebuilding how the marketing function makes decisions, not just changing which tool writes the posts.

**Workflow depth on the spectrum:** genuine **workflow layer**, trending toward operating system for a lean marketing function.

**Named attacker:** **HubSpot Breeze** (hubspot.com → Breeze AI). Clients already pay for HubSpot; Breeze agents sit where the CRM and campaign data already live. It attacks the one place Mariella's attribution spine has to reach — the CRM contact/company join key — from the inside.

**Why not 5:** the depth is real but thinly deployed. Integrations (GA4 / Search Console / LinkedIn via Vaults) are **designed, not built**, so audits currently run on public-web inference only. The consultant→client handoff is unproven — transport works, but no run has produced `marketing-strategy-confirmed.md`, which is the very file the PLAN layer is anchored on. The moat is architected; it is not yet installed in a client.

---

## 2. Data Advantage — 4/5

**Proprietary signal that compounds.**

**Rationale:** There are three compounding mechanisms, not a stockpile:

1. **The attribution spine.** Campaign IDs born in PLAN join published asset → traffic → enquiry → deal. That lineage — *which marketing decision produced which revenue* — is signal no platform holds: HubSpot has the deal but not the plan-to-asset provenance; Semrush has the search data but no deal outcome.
2. **The living-strategy amend loop.** When a strategic signal appears — a pillar repeatedly rejected, a stated change in ICP or positioning — the engine *asks* whether to amend the confirmed strategy and logs what drove the change. The plan itself learns, not just next week's ideas.
3. **Per-turn capture.** Every PRODUCE turn lands in `signals.csv`; real-time signals accumulate in `client-learnings.md` with 60-day archive hygiene.

**Why not 5:** all of it compounds **within** a tenant and none of it across tenants. Client #10's engine is no smarter than client #1's was on day one. A per-tenant loop is a switching cost; it is not a data moat.

**Named attacker:** **Semrush** (semrush.com). Holds cross-account search and content performance data across millions of domains. Any market-level claim T&G eventually makes from aggregated client data, Semrush can already make from a far bigger sample — see the Network loop in `../02-the-moat/data-flywheel.md`.

---

## 3. Platform Exposure — 2/5

**If a platform ships your wedge natively tomorrow, then what?**

**Rationale:** The engine is ~116KB (client) / ~189KB (consultant) of markdown executing on a frontier Claude model inside Anthropic's Managed Agents. It exceeds CMA's 100k system-prompt cap, so it is mounted as a file per session — which is an honest description of the asset: **the product is portable text on someone else's runtime.** Anthropic ships Agent Skills and a skills marketplace; the open-source marketing-skills library the engine descends from is public and free, which is direct evidence the category commoditises. T&G made its own fork **private on 22 Jul specifically to protect the engine IP** — a correct move, and also an admission of how copyable the asset is.

The scarce ingredient is the marketing judgment written into the engine. Written judgment is forkable judgment.

**Named attacker:** **Anthropic** (anthropic.com — Claude Agent Skills / skills marketplace). Uncomfortable, and that is the point: **the same vendor holds both the runtime and the substitute.** Second-order: **OpenAI AgentKit** (openai.com).

---

## Top Vulnerability

**Three of Mariella's four learning loops are strong inside a tenant and the fourth is zero across them — so the product gets better for every client it serves and never better as a company, while the asset doing the work is portable text on the runtime of the vendor most likely to replace it.**

## Confidence: **M**

The bet is validated where most aren't: real clients, a proven end-to-end consultant run, a live delivery cadence, and a displaced cost (a content hire) that anchors willingness to pay. But the platform is half-installed — Vaults, integrations, the client interface and the always-on host are all unbuilt, the orchestrator runs from a laptop, and the cross-tenant loop that would turn this into a product doesn't exist. M, not H, until integrations and the aggregation plane ship. M, not L, because demand is proven and the architecture is right.

---

## Partner stress-test

**Not yet done with a partner.** Scores are self-assessed and the module is explicit that self-assessment is generous. The score most likely to be too kind is **Contextual Moat (4)** — it credits an architecture that is not yet live in a paying client. A fair attacker would argue that until the integration gate and the confirmed-strategy handoff actually work, the deployed reality is closer to a 3. Redo with a real partner and let them argue it down.
