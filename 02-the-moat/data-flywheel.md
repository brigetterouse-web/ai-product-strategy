# Data Flywheel Map

> Score each loop 1-5. Your weakest loop is where competitors attack first.

**Product:** Mariella — hosted multi-tenant AI marketing engine (Think & Grow)

## Flywheel Loops

| Loop | What It Measures | Score 1 | Score 5 | Score |
|------|------------------|---------|---------|-------|
| **Correction** | Do users fix AI outputs? Is that signal captured and reused? | No capture | Automated retraining | **4**/5 |
| **Preference** | Does the product learn individual / team preferences over time? | Stateless | Deep personalization | **4**/5 |
| **Domain Context** | Does usage in one area improve quality in adjacent areas? | Siloed | Cross-domain transfer | **4**/5 |
| **Network** | Does each new user / team make the product better for everyone? | Isolated | Strong network effects | **2**/5 |

### Correction Loop — 4/5

**What you capture:** every PRODUCE turn is captured to a per-tenant signals log. Real-time signals — what the client rejected, deferred or corrected in session — accumulate with timestamps and 60-day archive hygiene, so the active file stays a current cohort rather than an ever-growing log. Engine complaints are captured separately from content signals.

**How it compounds:** two levels, and the second is the unusual one. Tactically, signals apply as overrides on the next run — rejected hook types stop being suggested, deferred ideas re-surface as "previously deferred," monthly recommendations beat general defaults. **Strategically, a living-strategy amend prompt watches for *patterns* — a pillar repeatedly rejected, a stated change in ICP or positioning — and asks the client whether to amend the confirmed strategy, logging what drove the change.** Most correction loops improve the next output. This one can change the plan every future output derives from.

**Why not 5:** the client must say yes (ask-first, never silent — correct for trust, slower to compound), and nothing retrains. It's a prompt reading structured files.

### Preference Loop — 4/5

**What you capture:** durable per-tenant brand voice, style guide, audience and org knowledge, plus the PLAN layer the client confirms and owns — pillars, calendar, budget and per-event ROI. Guardrails enforce it on every asset: an idea that doesn't map to a confirmed pillar isn't presented.

**How it compounds:** within a few months a tenant's PLAN layer encodes decisions no competitor can see, and the engine's output is mistuned for anyone else's brand. That mistuning *is* the switching cost.

**Why not 5:** a human consultant seeds and curates the layer. Nothing is learned automatically.

### Domain Context Loop — 4/5

**What you capture:** the PLAN layer plus normalized, source-tagged performance records across search, site analytics, AI visibility and email — every figure tagged with its provider or marked inferred, backed by a connection ledger — and campaign IDs threading the attribution spine.

**How it compounds:** this is what PLAN/PRODUCE structurally buys. One decision layer improves **every** asset type — post, ad, lead magnet, email, website copy, testimonial — because all of them derive from the same plan through one shared production spine. Sharpen a pillar and six asset types improve at once.

**Why not 5:** transfer happens *within* an account.

### Network Loop — 2/5

**What you capture:** per-tenant stores are isolated by design, and the cross-tenant benchmark plane is designed but not yet turning: company-level aggregates only, a minimum-cohort floor, CRM/audience/email record types excluded by policy, B2B commercial opt-in.

**Scored 2, not higher:** the substrate is real — the performance records are already normalized and source-tagged in T&G's own store, and the privacy model is settled, so this is a pipe rather than a research programme. But the loop doesn't turn yet, and a loop that doesn't turn doesn't score.

**Why this is the most valuable loop in the product, not the most broken one:** a benchmark clients can see is a genuine network effect — each new tenant improves the benchmark and every existing tenant gains without doing anything. Network is among the strongest of the eight moats, and it is **the only loop that makes Mariella compound as a company rather than per client**. This is not a gap to patch; it's the mechanism that decides what kind of business this is.

**Two versions, and only one is a strong network effect:**

| Version | What it is | Network strength | Built score |
|---|---|---|---|
| **Benchmark as a report** | Clients read "what we're seeing in the market this quarter." Differentiating, good marketing, a fair two-sided trade for opt-in. | **Saturates** — improves a lot from 5 tenants to 20, barely at all from 200 to 400 given the cohort floor. | ~3 |
| **Benchmark as engine input** | Cross-tenant performance priors feed the PLAN layer — the engine recommends pillars and hook types from what's actually working across comparable firms now. Every client's results improve every client's *outputs*. | **Doesn't saturate the same way** — it compounds into the decision layer, where the moat already is. | 4–5 |

Version 2 is the prize, and the existing privacy design already permits it: company-level, pre-aggregated rates per tenant, no PII, no verbatim content. **No policy change needed — this needs the pipe, not a new decision.**

**Total Flywheel Score: 14/20**

**Weakest Loop:** Network — 2/5

**Fix — sequenced:**
1. **Pipe it.** Read each tenant's normalized performance records into one company-level benchmark table, minimum-cohort suppression, no named individuals.
2. **Ship the report version.** One benchmark cut, to prove the trade and open the opt-in conversation.
3. **Feed it back into PLAN.** Cross-tenant priors informing pillar and hook recommendations. This is the step that turns a marketing asset into a compounding product, and it's the real target.

> **The shape of the diagnosis.** Three loops at 4 and one at 2 is not a balanced 14/20 — it's a product that compounds hard per client and barely at all as a company. Every client makes their own Mariella better; the company's Mariella improves only marginally. **The benchmark loop is the only thing that changes that, which makes it the strategy rather than a phase-3 item.** Hosting multi-tenant is what makes it possible at all.

---

## Encroachment Threat Assessment

### 1. Platform Encroachment
**Attacker:** Anthropic (anthropic.com — Claude Agent Skills / skills marketplace)
**Vector:** agent-skill marketplaces and templates make "a marketing agent with a plan layer and a weekly cadence" forkable. The engine is markdown, and the open-source library it descends from is public and free. T&G's fork was made private to protect it — correct, and an admission of how copyable it is.
**Time-to-threat:** 6–12 months (arguably underway)
**% of value at risk:** ~50% — the engine IP specifically
**Double exposure:** the same vendor supplies the runtime and the substitute. See `kill-switch.md`.

### 2. Vertical Competitor
**Attacker:** Copy.ai (copy.ai — "GTM AI Platform")
**Vector:** already sells agentic GTM workflows to B2B teams. Going one layer deeper into lean-team content operations is a roadmap item, not a pivot. They hold prompt/output performance data across thousands of accounts.
**Time-to-threat:** 6–9 months
**% of value at risk:** 30–40%

### 3. Adjacent Expansion
**Attacker:** HubSpot Breeze (hubspot.com)
**Vector:** clients already pay for it, the data is already inside, and Breeze agents arrive as "one more thing" with no incremental sale. It attacks the attribution spine from the inside — the join key is the CRM contact/company, which HubSpot owns and Mariella has to reach into.
**Time-to-threat:** ~12 months
**% of value at risk:** ~40%, and the harder 40% — it takes the decision surface, not the content output.

---

## 90-Day Encroachment Plan

> **Self-run — I played both sides.** The module is explicit that self-assessment is generous, so treat this as a floor. Redo with a real partner before M6.

**Attacker:** HubSpot Breeze

**Attack vector (weakest loop):** the Network loop. Breeze attacks with the one thing Mariella can't yet answer — it already has cross-account data, and it owns the CRM join key the attribution spine depends on.

**Weeks 1–4 — what they ship:** "Marketing Benchmarks" in the HubSpot dashboard. Free, every customer, from aggregate portal data. Zero integration work, because it's already connected — while Mariella's benchmark plane is still a pipe waiting to be built.

**Weeks 5–8 — how they poach users:** a Breeze content agent that cites those benchmarks in its recommendations and reports attribution natively, because the deal data never leaves the system. Pitch: *"your agency's engine infers what's working. Ours measures it, across hundreds of thousands of portals."* Marginal price: zero.

**Weeks 9–12 — why users don't come back:** the plan, the assets and the attribution now sit in one system with the CRM. Mariella's differentiator — a consultant-seeded PLAN layer — starts reading as *setup cost* against something that works on day one.

**Your defense:**
1. **Ship the benchmark loop before they define the category.** The records already exist; this is a pipe and a suppression rule, not a research programme.
2. **Own cross-platform.** Mariella reads GA4 + Search Console + LinkedIn *together*, including organic and search channels HubSpot doesn't own. HubSpot can only attribute what passes through HubSpot.
3. **Own PLAN, concede the CRM.** Don't fight for the contact record. The defensible layer is the decision lineage — pillar → campaign ID → asset → enquiry — which no CRM models.
4. **Compete on cohort relevance, not sample size.** A benchmark across comparable lean B2B professional-services firms beats a benchmark across every HubSpot portal, if the cohorting is good.
5. **Price the consultant honestly.** A named consultant accountable for the strategy is a services moat. Real, but it should be priced as services, not counted as product defensibility.
6. **Stop calling the engine the IP.** It's the most copyable asset in the business. The PLAN layer, the attribution spine and the tenant data are the durable ones.
