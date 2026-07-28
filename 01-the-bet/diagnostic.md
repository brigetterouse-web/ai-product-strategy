# Three-Axis Diagnostic

**Product:** Mariella — a multi-tenant AI marketing engine for lean B2B marketing teams (Think & Grow)
**Engine versions:** consultant v7.5 / client v8.0 · **Operating model:** PLAN & PRODUCE (2 modes)
**Path:** B — AI-native. The intelligence is the product, not a sidebar.
**Dominant archetype:** Orchestrator (Copilot surface, Creator output)
**Date:** 2026-07-28

**ICP:** Australian-focused. Lean marketing teams of 1–3, $200K–$1M+ annual marketing spend, AI-literate and actively avoiding "AI slop" (set 14 Jul; C-suite roles deliberately excluded from targeting). Two-buyer GTM: the founder buys *desire + speed*, the marketer buys *the data story*. The alternative it displaces is a **$120–180k/yr content hire**.

## Deployment state — read this before the scores

Two delivery paths exist, and conflating them produces a much gloomier diagnosis than the truth.

- **Live today — T&G-operated, client-hosted / Drive-folder.** Mariella is in production against real systems. **Wink Models**: marketing audit delivered 26 Jun off real client data (revenue mix, revenue by state, 97.3% repeat-business split, top clients by deal count), with Klaviyo and GA4 connected, HubSpot and LinkedIn partial. **Think & Grow itself**: CJ Robinson is a daily power user — 90-day marketing strategy and budget, event ROI modelling (targeting a $50k deal per 10 attendees), monthly content plans, newsletter click-rate analysis, LinkedIn ads benchmarking, and recurring scheduled tasks that keep SEO/AEO/GEO guidance current. A weekly "Maria Upgrades" working session has run since 16 Jun.
- **In build — the T&G-hosted CMA platform.** Vaults, per-tenant S3, the orchestrator, the client-facing interface. This is the *migration target*. Its gaps (Vaults unbuilt, integrations not yet wired through Vaults, orchestrator on a laptop) are gaps in the platform, **not** in the product as delivered.

> Scored 1 = pain, 5 = strong. Calibration: Figma = deep moat, thin ChatGPT wrapper = shallow.

| Axis | Score |
|------|-------|
| Contextual Moat | **4**/5 |
| Data Advantage | **4**/5 |
| Platform Exposure | **2**/5 |

---

## 1. Contextual Moat — 4/5

**Workflow depth × switching cost.**

**Rationale:** Mariella runs a **two-mode operating model**. PLAN owns the living decision layer — confirmed strategy, content pillars, the content and event calendar, budget and per-event ROI, campaign and lead-magnet plans — and PRODUCE derives every asset (post, ad, lead magnet, email, website copy, testimonial) *from* that plan, through a PLAN-FIRST gate that refuses to fabricate a pillar to proceed. Every PLAN item that will publish carries a **stable campaign ID** threading content → traffic → enquiry → deal.

**The depth is observed, not theorised.** CJ's usage is the evidence: she doesn't ask it to write posts, she asks it to build the 90-day strategy, model event ROI against a revenue target, and maintain its own standing instructions on a schedule. That is a tool sitting inside how the marketing function *decides*, and scheduled tasks mean it runs whether or not anyone opens it. Switching means abandoning the confirmed strategy, the pillars, the calendar, the campaign-ID history and the attribution lineage — rebuilding how the function operates, not changing who drafts the copy.

**Workflow depth on the spectrum:** genuine **workflow layer**; for a single-operator marketing function like CJ's it is approaching an operating system.

**Named attacker:** **HubSpot Breeze** (hubspot.com → Breeze AI). Wink's HubSpot is already in the stack and the attribution spine's join key is the CRM contact/company — so Breeze attacks the exact seam Mariella has to reach across, from the inside, with no integration to negotiate.

**Why not 5:** two tenants, one of them itself. Switching cost is demonstrated for a handful of operators, not a book of clients. Delivery is still manual last-mile — updating a live engine means a human re-pasting or a script touching one Drive file, with no auto-deploy — so version control across clients is a promise the hosted platform makes, not a property the product has. And the hosted path that would make the moat durable is half-built.

---

## 2. Data Advantage — 4/5

**Proprietary signal that compounds.**

**Rationale:** Three compounding mechanisms, all now running against real data:

1. **The attribution spine.** Campaign IDs born in PLAN join published asset → traffic → enquiry → deal. That lineage — *which marketing decision produced which revenue* — is signal no platform holds: HubSpot has the deal but not the plan-to-asset provenance; Semrush has search performance but no deal outcome.
2. **The living-strategy amend loop.** A pattern — a pillar repeatedly rejected, a stated change in ICP or positioning — prompts the engine to ask whether to amend the confirmed strategy, logging what drove the change. The plan learns, not just the next draft.
3. **Per-turn capture.** Every PRODUCE turn lands in `signals.csv`; real-time signals accumulate in `client-learnings.md` with 60-day archive hygiene. CJ is separately tracking task-level time savings to build the internal business case — a usage dataset most vendors would have to run a research project to get.

**Why not 5:** all of it compounds **within** a tenant and none of it across tenants. Wink's engine learns nothing from T&G's and vice versa. A per-tenant loop is a switching cost, not a data moat.

**Named attacker:** **Semrush** (semrush.com). Cross-account search and content performance across millions of domains. Any market-level claim T&G eventually makes from aggregated client data, Semrush can already make from a far bigger sample — see the Network loop in `../02-the-moat/data-flywheel.md`.

---

## 3. Platform Exposure — 2/5

**If a platform ships your wedge natively tomorrow, then what?**

**Rationale:** The engine is ~116KB (client) / ~189KB (consultant) of markdown executing on a frontier Claude model. It exceeds the hosted runtime's 100k system-prompt cap, so it is mounted as a file per session — an honest description of the asset: **the product is portable text on someone else's runtime.** Anthropic ships Agent Skills and a skills marketplace; the open-source marketing-skills library the engine descends from is public and free. T&G made its own fork **private on 22 Jul specifically to protect the engine IP** — correct, and also an admission of how copyable the asset is.

The scarce ingredient is the marketing judgment written into the engine. Written judgment is forkable judgment.

**Named attacker:** **Anthropic** (anthropic.com — Claude Agent Skills / skills marketplace). Uncomfortable, and that is the point: **the same vendor holds both the runtime and the substitute.** Second-order: **OpenAI AgentKit** (openai.com).

---

## Top Vulnerability

**Three of Mariella's four learning loops are strong inside a tenant and the fourth is zero across them — so the product gets better for every client it serves and never better as a company, while the asset doing the work is portable text on the runtime of the vendor most likely to replace it.**

## Confidence: **M**

Higher than the architecture alone would justify, because the demand side is answered: a paying client engagement running on live data, an internal power user who reaches for it daily rather than dutifully, a pricing model agreed at leadership level (subscription, 13 months for the price of 12, overage rolled to the next invoice), and a displaced cost — a content hire — that anchors willingness to pay.

Still M rather than H because the thing in production is **T&G-operated with a manual last mile**, and the platform that makes it a scalable product — Vaults, integrations through Vaults, client login, always-on host, aggregation plane — is unfinished. The bet is proven as a service; it is not yet proven as a product.

---

## Partner stress-test

**Not yet done with a partner.** The score most likely to be too kind is **Contextual Moat (4)**, and the sharpest attack is that n=2 with one of them being yourself is a pilot, not a moat — real switching cost has never been tested by a client who wanted to leave. Redo with a partner and let them argue it down.
