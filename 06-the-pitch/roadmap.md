# Three-Horizon Roadmap & Board Pitch

**Product:** Mariella — hosted multi-tenant AI marketing engine (Think & Grow)
**Audience for this pitch:** CEO + leadership team — internal funding review
**The ask in one line:** **$150k over six months**, one senior engineer plus half a product FTE, hard review at month 3 against the H2 kill criteria.

> **Horizon windows are AI-compressed on purpose.** H1 = 0–4 weeks, H2 = 1–3 months, H3 = 3–6 months, not the quarterly/annual version. A roadmap whose H3 sits twelve months out is planning in a world that no longer exists — three months is roughly one frontier cycle, and nothing in this plan needs a longer commitment than that to produce a signal.

---

## The AI Bet Evaluator — six lenses, run against this repo

Run against the assembled strategy rather than in defence of it. The output that matters is not what held up; it is the sentence that got rewritten.

| Lens | Verdict | What it found |
|---|---|---|
| **Bet validation** (M1) | **Holds** | Paying engagements, unprompted daily use, a quantified alternative, and a demand type named honestly as non-consumption rather than displacement. Confidence is stated as a distribution, not a letter |
| **Defensibility** (M2) | **Holds, with the weak point named** | The engine is conceded as copyable; the claim sits on the PLAN layer, the campaign-ID lineage and the benchmark. The uncomfortable part — the same vendor supplies the runtime and the substitute — is stated rather than buried |
| **Pricing alignment** (M3) | **Strongest component** | Measured unit costs, 92.2% margin, a 3× token shock costing six points, cascading correctly dismissed as a non-lever at 0.06 points. Priced against a salary, not a seat |
| **Trust & reliability** (M4) | **Specified, not yet running** | The contract is explicit and measurable, and provenance-based tiering is a better design than a confidence bar. But the golden set is frozen on paper and the harness does not exist |
| **Impact & scale** (M5) | **The honest weak spot** | Two of five loops are unbuilt and they are the only two that compound at company level. The freeze test says the product compounds per client and scales as a company |
| **Capability gaps** | **The real constraint** | Every open item — the aggregation pipe, the eval harness, the deal-outcome join — is one engineer away, and there is no engineer allocated. The strategy is not blocked on knowledge; it is blocked on capacity |

### The weakest sentence, and its rewrite

**Was:** *"Payback against the platform build cost is unquantified — build cost is not yet costed."*

That sentence is fatal in a funding conversation. Every other number in the repo is measured or explicitly modelled; this one asks the room to fund something unpriced, and no board can say yes to it.

**Now:** *"The build is $150k over six months. At $2,310 of monthly contribution per tenant, it repays against **5.4 tenants held for one year** — and the same spend closes the two loops that decide whether this is a product or delivery tooling."*

The ask below **is** that rewrite. M3 named the gap; M6 is where it gets a number.

---

## Roadmap

Every initiative links to a strategy component. Anything that linked to nothing was cut rather than carried.

### Horizon 1 — Ship · 0–4 weeks · high confidence

*Execute what is already decided. H1 earns the credibility that funds H2 — and three of the six board metrics below do not exist until it lands.*

| Initiative | Component | Metric | Confidence |
|---|---|---|---|
| Freeze the 12-row golden set and wire the rule-based provenance checks into assembly | **Contract** | Unsourced-figure rate reportable, target 0% | **H** |
| Ship the eval dashboard v1 — quality, judge setup, drift, loop | **Contract** + **Moat** | Screen-shareable in a sales call | **H** |
| Per-stage model field as a provider-swap seam | **Moat** | Portability moves Locked → Partial | **H** |
| Effort tuning: drop mechanical sessions from `xhigh` | **Margin** | Cost per turn down without a cache invalidation | **H** |

### Horizon 2 — Validate · 1–3 months · medium confidence · every bet has a kill line

*This is where the living strategy lives. Each row states a number, a window and a verb.*

| Bet | Component | Signal we need | Kill criterion |
|---|---|---|---|
| **The shared aggregation pipe** — normalized tenant records into one company-level benchmark table | **Moat** | Pipe reading live records, cohort suppression working | If the pipe is not reading records by **week 8**, stop the engine-input version and ship report-only |
| **Benchmark-as-report v1** — one cut, to prove the trade and open the opt-in conversation | **Moat** | Tenants accept the two-sided trade | If fewer than **3 tenants opt in by week 10**, stop building toward engine-input and treat the benchmark as marketing collateral only |
| **Deal-outcome join promoted to a gating onboarding requirement** | **Bet** + **Moat** | Campaign IDs resolving to closed revenue | If **<50% of published campaign IDs resolve to a deal outcome by week 12**, drop attribution from the pitch and reposition on planning speed |
| **Oversight reduction to ≤1 hr/tenant/month** | **Margin** | Consultant exception queue shrinking as golden rows grow | If oversight is still **>2 hrs at month 3**, raise price or cut scope — do not add tenants |
| **Confidence legibility at the point of use** (the M5 trust-gap finding) | **Contract** | Users stop re-verifying already-sourced figures | If the re-verification behaviour persists at **month 3**, rebuild the Flagged tier rather than adding features |

### Horizon 3 — Explore · 3–6 months · low confidence · optionality

*Small investment. At least one of these should be uncomfortable.*

| Experiment | Component | Why it might be the next curve |
|---|---|---|
| **Benchmark as engine input** — cross-tenant priors feeding PLAN recommendations | **Moat** | The prize. It compounds into the decision layer where the moat already is, and it is the only loop that makes Mariella compound as a company |
| **Outcome-based pricing pilot** — meter on attributed enquiries | **Margin** | The unit the founder buyer already thinks in, and the strongest pricing move available. Held back only until first-touch attribution is trustworthy |
| **Self-hosted-sandbox drill on one tenant** | **Moat** + **Guardrails** | Converts a documented exit into a tested one, and decides the lock-in question deliberately rather than by default |
| **Publishing autonomy behind the >99% bar** | **Guardrails** | The scariest line here. It would trade the liability position that keeps the client as sender of record, so the experiment is whether the bar can be met at all — not whether to ship it |

---

## The six AI metrics for the board slide

Alongside the standard metrics, not instead of them. Three are reportable today; three are exactly what H1 creates — which is the cleanest argument for funding H1 first.

| Metric | Mariella's version | Status | Board band |
|---|---|---|---|
| **Hallucination rate** | Unsourced-figure rate in client-facing output. Target **0%** — defensible because the check is a regex, not a judgement | Enforced at assembly; **not yet reported** | Good <1% · Bad >5% |
| **Drift velocity** | Weekly decay in first-pass acceptance, four-week rolling | **Needs the golden set** (H1) | Good <0.5%/wk |
| **Confidence distribution** | The **Derived / Flagged / Held** tier split. Healthy is bimodal — mostly Derived with a real Held tail. A fat **Flagged** middle means provenance is half-present, which is the actual failure shape | **Needs the dashboard** (H1) | Good: thin middle |
| **HITL rate** | **Report the consultant exception queue only.** The client approval gate is 100% by design and must stay there — counting it as HITL would read the trust product as a defect rate | Queue measurable now | Good: trending down |
| **Inference ROI** | **~42×** — $2,500 revenue against $59 of AI COGS | **Measured** | Good >10x · Bad <3x |
| **Eval regression catch** | Share of engine changes gated on the frozen set pre-deploy | **0% — no harness exists** | Good: 100% caught |

**Say the 42× out loud, then move on.** It is the number that ends the "AI will eat your margin" line of questioning in one figure, and dwelling on it invites the board to think tokens are the risk. They are not: **one hour of human oversight per tenant costs more than twice the month's inference**, and that is the number the roadmap is actually managing.

---

## Board Pitch

**Thesis (1 sentence):** A marketing team of one to three people, at a firm spending $200K–$1M a year, cannot fund the hire that would make that spend work — so we sell them that person's job, running: a living plan that produces every asset against it and attributes the result back to a closed deal.

### The case

**1. Why now.** Three things changed at once. The reasoning is finally good enough that the bottleneck is a confirmed plan rather than the writing. Hosting moved from client-side to T&G-side, which converts the tenant knowledge base from something the client owns into something we hold — that is a moat change, not an infrastructure change. And the alternative got more expensive: the content hire this replaces is a $120–180k salary that this ICP was already failing to fill.

**2. What's defensible.** Not the engine — it is markdown, it descends from a public library, and the vendor supplying our runtime is also the most likely to ship the substitute. Defensible: the client's confirmed PLAN layer, the campaign-ID lineage joining a marketing decision to the revenue it produced, per-tenant data in our own store behind an integration gate no single platform owns end to end, and a cross-tenant benchmark that is only possible because we host it. **Stop calling the engine the IP.**

**3. The economics.** $2,500/month against $194 of COGS — **92.2% gross margin**, and AI is 2% of revenue. A 3× token shock costs six points and never threatens the business. Cascading, the industry's standard defence against AI margin compression, is worth 0.06 points here because 95% of turns are strategic reasoning with no cheap tier to route to. The margin risk is human hours, not tokens: one hour per tenant holds 92%, four takes it to 77%.

### The risks

**1. Trust and failure modes.** The client publishes our output under their own brand, so a confident error is a false claim in market — the Air Canada shape. The response is structural, not procedural: provenance rules that refuse to put an unsourced number in a gated field, three tiers keyed to what is checkable rather than to what the model claims about itself, and an approval gate that cannot be waived by instruction. The gap is honest — the harness that scores all of this is specified and unbuilt, and H1 is what builds it.

**2. Scale and governance.** No write-back tool exists in the allow-list at all, which removes a class of irreversible action rather than governing it. Email is drafted and never sent, so the client remains sender of record and holds the consent obligation — a deliberate allocation of liability. Cross-tenant memory is permitted only in aggregate, which is what makes the benchmark legal to build rather than a privacy problem to solve later.

**3. Competitive.** HubSpot Breeze is the real threat, not a model vendor: clients already pay for it, the data is already inside, and it owns the CRM join key our attribution spine has to reach across. It attacks the one thing we cannot yet answer. The defence is to ship the benchmark before the category is defined, own cross-platform where HubSpot can only attribute what passes through HubSpot, and concede the contact record while keeping the decision lineage.

**4. The risk I would name unprompted.** The product compounds per client and barely at all as a company. Every client makes their own Mariella better; the company's Mariella improves marginally. Two of five learning loops are unbuilt, they are the only two that compound at company level, and they are one shared pipe away from each other. That is what this ask buys, and if it is not bought the honest position is that this is excellent delivery tooling rather than a product.

### The ask

**$150k over six months.**

| Line | Amount |
|---|---|
| 1 senior engineer, 6 months — aggregation pipe, eval harness, dashboard, deal-outcome join | **$95k** |
| 0.5 FTE product/consultant time — golden-set labelling, tier design | **$35k** |
| Inference + infrastructure through the build | **$12k** |
| Eval tooling | **$8k** |

**Payback:** at $2,310 monthly contribution per tenant, the build repays against **5.4 tenants held for one year**.
**Gate:** hard review at **month 3** against the five H2 kill criteria. Two of them can fire before any further money is committed.
**What I am not asking for:** a pricing decision — subscription, 13-month contract at the 12-month price, credit allowance with overage, all already settled. This is a capacity ask, not a strategy ask.

---

## Coaching notes

**The opening line, said first, exactly:** *"A two-person marketing team spending three-quarters of a million a year can't hire the person who would make that spend work — so it doesn't get made to work. We sell them that person's job, running."* No model name, no vendor, no architecture. The technology stays invisible until the risks section, and if it surfaces earlier it is because someone asked.

**If I only get sixty seconds:** the thesis, the 92% margin with AI at 2% of revenue, the honest weak spot (compounds per client, not as a company), and the ask with its payback number. Drop the roadmap, drop the six metrics, drop the competitive section. **Never drop the weak spot** — volunteering it is what buys the room's trust in every other number.

**The hardest question this audience opens with:** *"What are we giving up to fund this?"* — because one senior engineer for six months is capacity not billed to a client. The answer: the alternative is growth that stays headcount-bound, where revenue and cost scale together forever. $150k against 5.4 tenant-years is the cheapest test available of whether this becomes a product, and month 3 is where we stop if it doesn't. The trade is six months of one engineer against finding out.

**The second hardest:** *"You've told us the engine is copyable and the vendor might replace you. Why are we funding it?"* — Because the copyable part is not the part being funded. $150k builds the pipe, the lineage and the harness, none of which a model vendor ships.

---

## M1 Baseline vs. Now

**M1 baseline** — written before any framework landed, unpolished, in [`../01-the-bet/ceo-question.md`](../01-the-bet/ceo-question.md). Deliberately unedited: the delta is the point, and polishing it would destroy the comparison.

**Now, three sentences:**

We're betting that lean B2B marketing teams will pay for a marketing function that *runs* — a living plan that produces every asset against it and attributes the result back to a closed deal — because they cannot fund the $120–180k hire that is the only alternative, which makes this a non-consumption market rather than a fight with an incumbent.

What's defensible isn't the engine, which is copyable markdown running on the vendor most likely to replace it; it's the client's confirmed plan, the campaign-ID lineage joining decisions to revenue, and a cross-tenant benchmark that only exists because we host it — priced against a salary rather than a seat, which holds **92% gross margin** and makes inference 2% of revenue.

It's fundable because the risks are instrumented rather than hoped away — provenance rules that refuse to publish an unsourced number, an approval gate that cannot be waived, and four kill criteria I would genuinely stop on — and the one thing that would change the answer is whether the cross-tenant loop turns, which is exactly what I'm asking for.

**The delta:** the M1 answer named a product and an ambition. This one names a bet with odds, a mechanism, a margin, a liability position, and the condition under which I would stop. Same product, and the second answer would survive a board.
