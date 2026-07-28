# Data Flywheel Map

> Score each loop 1-5. Your weakest loop is where competitors attack first.

**Product:** Mariella (Think & Grow) · consultant v7.5 / client v8.0 · **Date:** 2026-07-28

## Flywheel Loops

| Loop | What It Measures | Score 1 | Score 5 | Score |
|------|------------------|---------|---------|-------|
| **Correction** | Do users fix AI outputs? Is that signal captured and reused? | No capture | Automated retraining | **4**/5 |
| **Preference** | Does the product learn individual / team preferences over time? | Stateless | Deep personalization | **4**/5 |
| **Domain Context** | Does usage in one area improve quality in adjacent areas? | Siloed | Cross-domain transfer | **4**/5 |
| **Network** | Does each new user / team make the product better for everyone? | Isolated | Strong network effects | **1**/5 |

### Correction Loop — 4/5

**What you capture today:** every PRODUCE turn is captured to `signals.csv`. Real-time signals accumulate in `client-learnings.md` with timestamps and 60-day archive hygiene. `product-feedback.md` separates engine complaints from client-content signals.

**How it compounds:** two levels, and the second is the unusual one. Tactically, signals apply as overrides on the next run — rejected hook types stop being suggested, deferred ideas re-surface as "previously deferred." **Strategically, the LIVING STRATEGY amend-prompt watches for *patterns* — a pillar repeatedly rejected, a stated change in ICP or positioning — and asks the client whether to amend `marketing-strategy-confirmed.md`, logging what drove the change.** Most products' correction loops improve the next output. This one can change the plan that all future outputs derive from.

**Why not 5:** the client must say yes (ask-first, never silent — correct for trust, slower for compounding), and nothing retrains. It is a prompt reading markdown.

### Preference Loop — 4/5

**What you capture today:** durable per-tenant `brand-voice.md`, `style-guide.md`, `audience.md`, plus the PLAN layer the client confirms and owns — pillars, calendar, budget/ROI. Guardrails enforce it on every asset: the PILLAR/ICP check refuses to present an idea that doesn't map to a confirmed pillar.

**How it compounds:** after a few months a tenant's PLAN layer encodes decisions no competitor can see, and the engine's output is mistuned for anyone else's brand. That mistuning *is* the switching cost.

**Why not 5:** a human consultant seeds and curates the files. Nothing is learned automatically.

### Domain Context Loop — 4/5

**What you capture today:** the PLAN layer plus normalized, source-tagged DATA SOURCE RESOLUTION records (SEARCH_PERFORMANCE / SITE_ANALYTICS / AI_VISIBILITY / EMAIL_PERFORMANCE), every figure tagged `[DATA: provider]` or `[INFERRED]`, a connection ledger, and campaign IDs threading the attribution spine.

**How it compounds:** this is what PLAN/PRODUCE structurally buys. One decision layer improves **every** asset type — post, ad, lead magnet, email, website copy, testimonial — because all of them derive from the same plan through one shared PRODUCE spine. Improve a pillar and six asset types get better at once. That is real cross-domain transfer.

**Why not 5:** it is transfer *within* an account. Across accounts, zero.

### Network Loop — 1/5 today, designed for 4

**What you capture today:** nothing crosses a tenant boundary. Each tenant is an isolated S3 prefix with no cross-tenant read path — by design, for privacy reasons that are correct. Client #10 makes the product no better for client #1.

**Scored 1, not higher, on the module's own rule:** score what you capture *today*, and "we plan to capture this later" is a 1. There is a fair argument for **2** — the feed already exists in usable form (normalized, source-tagged DATA SOURCE RESOLUTION records in T&G's own versioned S3, with the privacy design already decided: company-level only, k-anonymity at N=5–10, CRM/audience/email excluded, B2B commercial opt-in). Only the aggregation *read* is missing. That is materially further along than a loop that would need instrumenting from scratch. But the loop does not turn, so it does not score.

**Why this is the most valuable loop in the product, not the most broken one:** a benchmark clients can see is a genuine network effect — each new tenant improves the benchmark and every existing tenant gains without doing anything. Network is among the strongest of the eight moats, and it is the only loop here that would make Mariella compound **as a company** rather than per client. This is not a gap to patch; it is the mechanism that changes what kind of business this is.

**Two versions, and only one is a strong network effect:**

| Version | What it is | Network strength | Built score |
|---|---|---|---|
| **Benchmark as a report** | Clients read "what we're seeing in the market this quarter." Differentiating, good marketing, a fair two-sided trade for opt-in. | **Saturates.** Improves a lot from 5 tenants to 20; barely at all from 200 to 400, given the N≥5 cohort floor. | ~3 |
| **Benchmark as engine input** | Cross-tenant performance priors feed the PLAN layer — the engine recommends pillars and hook types from what is actually working across comparable firms now. Every client's results improve every client's *outputs*. | **Doesn't saturate the same way** — it compounds into the decision layer, where the moat already is. | 4–5 |

Version 2 is the prize, and the existing privacy design already permits it: company-level, pre-aggregated rates per tenant, no PII, no verbatim content. **No policy change needed — this needs the pipe, not a new decision.**

**Total Flywheel Score: 13/20**

**Weakest Loop:** Network — 1/5

**Fix — sequenced:**
1. **Pipe it.** Read each tenant's normalized DATA SOURCE RESOLUTION records from their S3 prefix into one company-level benchmark table, N≥5 suppression, no named individuals.
2. **Ship the report version.** One benchmark cut, to prove the trade and open the opt-in conversation with clients.
3. **Feed it back into PLAN.** Cross-tenant priors informing pillar and hook recommendations. This is the step that turns a marketing asset into a compounding product, and it is the one to hold as the actual target.

> **The shape of the diagnosis.** Three loops at 4 and one at 1 is not a balanced 13/20 — it is a product that compounds hard per client and not at all as a company. Every client makes their own Mariella better and the company's Mariella no better. **The cross-client benchmark is the only loop that changes that, which makes it the strategy rather than a phase-3 item.** Everything else in the hosted pivot is plumbing in service of it.

---

## Encroachment Threat Assessment

### 1. Platform Encroachment
**Attacker:** Anthropic (anthropic.com — Claude Agent Skills / skills marketplace)
**Vector:** Agent Skills, a public marketplace and Managed Agent templates make "a marketing agent with a plan layer and a weekly cadence" forkable. The engine is markdown; the open-source library it descends from is already public and free. T&G's fork was made private on 22 Jul to protect it — correct, and an admission of how copyable it is.
**Time-to-threat:** 6–12 months (arguably underway)
**% of value at risk:** ~50% — the engine IP specifically
**Double exposure:** the same vendor is both the runtime and the substitute. See `kill-switch.md`.

### 2. Vertical Competitor
**Attacker:** Copy.ai (copy.ai — "GTM AI Platform")
**Vector:** already sells agentic GTM workflows to B2B teams. Going one layer deeper into lean-team content operations is a roadmap item, not a pivot. They hold prompt/output performance data across thousands of accounts that T&G does not.
**Time-to-threat:** 6–9 months
**% of value at risk:** 30–40%

### 3. Adjacent Expansion
**Attacker:** HubSpot Breeze (hubspot.com)
**Vector:** clients already pay for it, the data is already inside, and Breeze agents arrive as "one more thing" with no incremental sale. Critically, it attacks the attribution spine from the inside — the join key is the CRM contact/company, which HubSpot owns and Mariella has to reach into.
**Time-to-threat:** ~12 months
**% of value at risk:** ~40%, and the harder 40% — it takes the decision surface, not the content output.

---

## 90-Day Encroachment Plan

> **Self-run — I played both sides.** The module is explicit that self-assessment is generous, so treat this as a floor. Redo with a real partner before M6.

**Attacker:** HubSpot Breeze

**Attack vector (weakest loop):** the Network loop (1/5). Breeze attacks with the one thing T&G structurally cannot answer — it already has cross-account data, and it owns the CRM join key the attribution spine depends on.

**Weeks 1–4 — what they ship:** "Marketing Benchmarks" in the HubSpot dashboard. Free, every customer, from aggregate portal data. Zero integration work, because it's already connected — while Mariella's integrations are still unbuilt and its audits run on public-web inference.

**Weeks 5–8 — how they poach users:** a Breeze content agent that cites those benchmarks in its recommendations and reports attribution natively, because the deal data never leaves the system. Pitch: *"your agency's engine infers what's working. Ours measures it, across hundreds of thousands of portals."* Marginal price: zero.

**Weeks 9–12 — why users don't come back:** the plan, the assets and the attribution now sit in one system with the CRM. T&G's differentiator — a consultant-seeded PLAN layer — reads as *setup cost* against something that works on day one.

**Your defense:**
1. **Ship the integrations.** Until GA4 + Search Console + LinkedIn are live through Vaults, the data story that converts the marketer buyer is inference, and this attack lands unopposed. This is the highest-leverage build in the product, not a phase-3 item.
2. **Own cross-platform.** Mariella reads GA4 + Search Console + LinkedIn *together*, including organic and search channels HubSpot doesn't own. HubSpot can only attribute what passes through HubSpot.
3. **Own PLAN, concede the CRM.** Don't fight for the contact record. The defensible layer is the decision lineage — pillar → campaign ID → asset → enquiry — which no CRM models.
4. **Ship the benchmark loop before they define the category.** The source-tagged records already exist; this is a pipe and a suppression rule.
5. **Price the consultant honestly.** A named consultant accountable for the strategy is a services moat. Real, but it should be priced as services and not counted as product defensibility.
6. **Stop calling the engine the IP.** It is the most copyable asset T&G owns. The PLAN layer, the attribution spine and the tenant data are the durable ones.
