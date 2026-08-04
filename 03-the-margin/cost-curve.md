# Cost Curve & Pricing Strategy

**Product:** Mariella — hosted multi-tenant AI marketing engine (Think & Grow)
**Unit:** one tenant = one client (a lean marketing team of 1–3). The billable unit inside a tenant is a **turn** — one model request inside a Managed Agents session.

> **Headline:** at Mariella's price point, AI is **~2% of revenue**. The module's premise — AI compressing 80% margins to 40% — assumes a $20–80/seat product. Mariella is priced against a $120–180k/yr salary, so a 3× token shock moves gross margin by about six points and never threatens the business. **The margin risk is human time in the loop, not tokens.**

## What changed from v1

v1 was modelled on estimates. v2 replaces the biggest ones with measurements taken from real production sessions.

| | v1 (estimated) | v2 (measured) |
|---|---|---|
| Cost per turn | $0.07 inferred from token shapes | **$0.21** from `sessions.retrieve().usage` |
| AI cost per tenant/month | $9 | **~$59** |
| Prompt caching working? | "load-bearing assumption, unverified" | **Verified** — 4.5M cache-read tokens on one run |
| Cascading | 70/30 split, ~28% saving | **~5/95 — cascading does not apply.** Worth $1.40/mo |
| Infrastructure | $15/tenant, source unknown | **$18–19/month for the whole box** |
| Gross margin | 93.6% | **92.2%** |

The headline margin barely moved. The composition was substantially wrong in both directions and the errors happened to cancel.

## Architecture being costed

Mariella runs on **Anthropic Managed Agents (CMA)** with a T&G-owned orchestrator. Two cost surfaces, not one:

| Component | Runs on | Cost behaviour |
|---|---|---|
| The two agents (`mariella-consultant`, `mariella-client`) — engine, agent loop, per-session sandbox | **Anthropic** | Variable, per tenant, scales with usage |
| Orchestrator (`run-session.mjs`) — creates sessions, mounts tenant files, harvests output | **T&G EC2** | Fixed, divides across tenants |
| Per-tenant store | **T&G S3** | Negligible |

The EC2 box does not run the AI. It runs the control plane. This distinction matters: infrastructure is a fixed cost that flattens as tenants grow, while inference is genuinely variable.

## Measured unit costs

Taken from real sessions, Opus 4.8 at `xhigh` effort, list prices.

| Measurement | Output tokens | Cache-read tokens | Cost |
|---|---|---|---|
| Consultant setup — 7 knowledge files, **audit not included** | 48,367 | 4,498,118 | **$3.46** |
| Client — single read turn | 2,791 | 283,994 | **$0.21** |

**Prompt caching is verified and load-bearing.** That consultant run read 4.5 million cached tokens. At the cache rate ($0.50/MTok) it cost $2.25; at the fresh-input rate ($5.00/MTok) the same input would have cost **$22.49**. Caching is saving roughly 90% of the largest cost line, and it is confirmed working in production — not assumed.

**Cache reads are 65% of cost, and they compound within a session.** Every turn re-reads the engine plus the entire accumulated conversation, so the tenth turn of a session costs several times the first. The 4.5M figure came from roughly 50 turns against a ~47K-token engine. Two consequences: the flat per-turn cost used below is optimistic for long sessions, and **session length is a bigger cost lever than model choice** (see Cascading strategy).

## Rate card

| Line | Rate |
|---|---|
| Opus 4.8 / Opus 5 — fresh input | $5.00 / MTok |
| Opus 4.8 / Opus 5 — cache read | $0.50 / MTok |
| Opus 4.8 / Opus 5 — cache write | $6.25 (5-min) · $10.00 (1-hour) / MTok |
| Opus 4.8 / Opus 5 — output | $25.00 / MTok |
| Sonnet 5 — input / output | $2/$10 until 31 Aug 2026, then **$3/$15** |
| CMA session runtime | $0.08 per session-hour, billed only while `running` |
| Web search | $10 per 1,000 searches |
| Web fetch, file storage, vaults, idle sessions | free |

Two rate-card facts that affect the model:

- **Session runtime meters only while the session is `running`.** Idle sessions waiting on a human are free, so leaving sessions open between turns costs nothing.
- **Sonnet 5's introductory pricing ends 31 August 2026.** Every Sonnet figure in this document uses the post-September rate ($3/$15). Modelling on the introductory rate would overstate the cascading saving by a third.

## Cost by feature

Unit cost is measured. Volume is estimated and is the main remaining uncertainty.

| Feature | Class | Sessions/mo | Turns/session | Turns/mo | Cost/mo |
|---|---|---|---|---|---|
| PLAN layer refresh | **Leader** | 1 | 40 | 40 | $10.00 |
| Weekly cadence run | **Leader** | 4 | 15 | 60 | $15.00 |
| Ad-hoc strategy chat | **Leader** | — | — | 40 | $10.00 |
| Campaign production | **Killer** (recurring) | 6 | 12 | 72 | $18.00 |
| Monthly performance report | **Filler** | 1 | 8 | 8 | $2.00 |
| AI-visibility check | **Filler** | 1 | 6 | 6 | $1.50 |
| **Recurring total** | | | | **226** | **$56.50** |
| Session runtime | | ~15 hrs | | | $1.20 |
| Web search | | ~100 searches | | | $1.00 |
| **AI COGS per tenant/month** | | | | | **$58.70** |
| | | | | | |
| Consultant setup pass | **Killer** (one-off) | 1 per client, ever | — | — | **$3.46 measured (partial)** |

### Reading the feature table

**Leader — $35/month.** The PLAN layer plus the weekly cadence is 60% of recurring AI spend and 100% of the reason the contract gets signed. This is where the money should go.

**Filler — $3.50/month.** The report and the visibility check cost almost nothing and materially raise perceived value in the sales conversation. Bundle them without hesitation; there is no case for metering something that costs $3.50.

**Killer, recurring — $18/month.** Heavy campaign production is the only recurring feature with a genuine cost slope. It is 31% of AI spend on an average tenant and would be the first thing to bite on a heavy one. This is what the credit allowance and overage lever exist to catch.

**Killer, one-off — the setup pass.** Measured at $3.46, but that run stopped before the audit and confirm-strategy stages, which are the expensive deep-research portion. Budget materially higher pending a full measured pass. Commercially this is close to irrelevant: it is charged as an onboarding fee priced against **consultant time**, and even $50 of tokens is a rounding error against that fee.

### Packaging decision

| | Feature | Decision | Rationale |
|---|---|---|---|
| **Leader** | PLAN layer + weekly cadence | Bundle | What they come for: a marketing function that runs |
| **Filler** | Report, AI-visibility check, summaries | Bundle | $3.50/month to serve; raises perceived value |
| **Killer (one-off)** | Consultant setup pass | **Onboarding fee** | 100% of tenants, exactly once — a non-recurring event does not belong in a recurring price |
| **Killer (recurring)** | Heavy campaign production | **Meter above the allowance** | The only line with a real cost slope |

**On the 70% rule.** The rule says bundle a Killer used by >70% of users, unbundle below that. The setup pass is used by 100% of tenants — but *once*. The rule governs recurring cost, and applying it to a one-off event is the common mistake. The recurring Killer to watch is campaign production, and that one meters.

## Cost model per tenant

Volume is the remaining unknown, so the model is presented as three scenarios rather than a point estimate.

| Cost line | Light (100 turns) | Expected (226 turns) | Heavy (450 turns) |
|---|---|---|---|
| Inference | $25.00 | $56.50 | $112.50 |
| Session runtime | $0.60 | $1.20 | $2.40 |
| Web search | $0.50 | $1.00 | $2.00 |
| **AI COGS** | **$26.10** | **$58.70** | **$116.90** |
| EC2 orchestrator (÷ 5 tenants) | $3.80 | $3.80 | $3.80 |
| S3 storage | $1.00 | $1.00 | $1.00 |
| Human oversight (1 hr @ $130 loaded) | $130.00 | $130.00 | $130.00 |
| **Total COGS** | **$160.90** | **$193.50** | **$251.70** |
| **Gross margin @ $2,500** | **93.6%** | **92.2%** | **89.9%** |

**Cross-check.** T&G's heaviest internal user of the pre-hosted engine had to be upgraded to a premium Claude Team seat — roughly $100–125/month for one person. That is an independently observed cost for a genuinely heavy user, and it sits at the top of the modelled range. Two unrelated methods landing in the same band is reasonable evidence the band is right.

## Infrastructure

**The box is a `t3.small` in ap-southeast-2 at ~$0.0256/hr ≈ $18–19/month**, plus negligible S3. It runs the orchestrator only.

One networking decision is open and it is worth ~$50/month: the box either takes a public IP (~$19/month all-in) or sits behind a NAT gateway plus SSM VPC endpoints (~$70–80/month). The deployment plan recommends the public-IP path for a single low-risk internal box.

Infrastructure per tenant therefore depends on two variables:

| Tenants | Public IP ($19 box) | NAT ($75 box) |
|---|---|---|
| 1 | $19.00 | $75.00 |
| 5 | $3.80 | $15.00 |
| 10 | $1.90 | $7.50 |
| 25 | $0.76 | $3.00 |

At scale the decision is immaterial. At one or two tenants it is 2 points of margin. **This is the cost line that behaves like software** — it flattens toward zero while inference stays linear.

## Cascading strategy

**Today:** every stage runs on Opus 4.8 at `xhigh` effort. No cascading is implemented.

**The expected cascade ratio is ~5% cheap / 95% frontier — not the 70/30 this module assumes.** Three properties of the product drive that, and they are structural rather than a matter of tuning.

**1. The cascade unit is a session, not a turn.** On Managed Agents the model is a property of the *agent config*. A session references an agent and runs on that model start to finish; there is no per-turn model parameter. Per-turn routing is not available.

**2. Switching models destroys the caching that saves 90% of the cost.** Prompt caches are model-scoped — a model switch invalidates the tools, system, and message caches simultaneously. On the measured consultant run, cache reads cost $2.25 where fresh input would have cost $22.49. Any scheme that switches models mid-conversation pays that 10× penalty repeatedly. Even if per-turn routing existed, it would cost more than it saved.

**3. Applying the routing rule to the real feature list leaves almost nothing on the cheap tier.** The rule — mechanical stages go cheap, anything touching confirmed strategy, the audit, or client-facing copy stays frontier — resolves like this:

| Session type | Turns/mo | Tier |
|---|---|---|
| PLAN refresh | 40 | Frontier — it *is* the confirmed strategy |
| Weekly cadence | 60 | Frontier — derives client-facing assets from PLAN |
| Campaign production | 72 | Frontier — client-facing copy, explicitly |
| Ad-hoc strategy chat | 40 | Frontier — strategy reasoning is the product |
| Monthly performance report | 8 | Cheap — data pull and formatting |
| AI-visibility check | 6 | Cheap |
| **Cheap-eligible** | **14 of 226** | **6%** |

v1 listed search-data refresh, integration maintenance, capture sweep, archive hygiene and calendar mechanics as cheap stages. Most of those are sub-steps *inside* frontier sessions and cannot be routed separately, and the integration-dependent ones describe work that is not built yet.

**Dollar impact:** a 6% cascade at a 40% saving is **$1.40 per tenant per month** — 0.06 points of gross margin.

> **Verdict: cascading does not apply to this product.** The module's canonical defence against AI margin compression is worth six hundredths of a point here. That is not a tuning failure; it is a consequence of building a product whose value is strategic reasoning against a confirmed plan. Almost every turn is the expensive kind by design.

### The decision that is actually on the table

The measured 41% Opus↔Sonnet delta is real, but it is not a cascading saving — it is what running **the entire product** on Sonnet 5 would save: **~$24 per tenant per month**.

That reframes the open item. The question is not "what ratio should we cascade at," it is **"is Opus 4.8 worth 41% more than Sonnet 5 for marketing strategy work?"** That is a quality judgement with a measurable answer: run the same consultant pass on both and compare the output. It is testable in an afternoon and it is the real content of the model choice made on feel on 27 July.

### Two levers that beat model choice

**Effort, not model.** The agents run at `xhigh`. Effort controls thinking depth and total token spend, and — unlike a model switch — it does not invalidate the prompt cache, because it is a generation-time parameter rather than part of the cached prefix. Anthropic's guidance is that `xhigh` suits coding and agentic engineering, with `high` the starting point elsewhere and lower levels often sufficient. Dropping the report and visibility-check sessions to `medium` and testing `high` on cadence runs is a cheaper, safer experiment than swapping models, and it is untested.

**Session length is the largest lever of all.** Cache reads are **65% of measured cost** ($2.25 of $3.46), and they compound *within* a session: every turn re-reads the engine plus the entire accumulated conversation, so the tenth turn costs several times the first. The 4.5M cache-read tokens came from roughly 50 turns against a ~47K-token engine. Shortening sessions, or enabling context compaction, cuts more cost than any model decision — and it is the only lever here that does not trade against output quality.

## Pricing model

**Current pricing:** project/retainer, human-delivered.

**Proposed AI pricing:** **$2,500/month** subscription. 13-month contract at the 12-month price (first month as cooling-off, securing a 12-month commitment). API cost bundled to a credit allowance; overage invoiced the following month with an alert at 90% — no hard stop. A $20–30k one-off was considered and rejected (leadership walk-through, 22 Jul 2026).

**Model:** **hybrid** — base subscription + metered overage.

**Credit allowance:** set at **$120/month** of AI usage — roughly 2× the expected run-rate of $59 and just above the heavy-tenant case of $117. This is a revision from v1, which set the allowance at $25 against a $9 estimate; that allowance would have fired on almost every tenant. At $120 it fires only on genuinely heavy usage, which is exactly when it should.

**Why not outcome-based yet.** The campaign-ID attribution spine means Mariella *could* meter on attributed enquiries — the unit the founder buyer already thinks in, and the strongest pricing move available. Holding it back because first-touch attribution needs to be trustworthy before revenue depends on it. **Outcome pricing is the M6 roadmap item, not today's model.**

## Stress tests

| Scenario | Impact | Response |
|---|---|---|
| Inference costs 3× | AI COGS $59 → $176; margin 92.2% → **86.5%** | Absorb it. Overage exists but wouldn't need to fire. |
| Provider raises prices 50% | AI COGS $59 → $88; margin → **91.0%** | Absorb it. |
| Heaviest tenant (450 turns) | AI COGS → $117; margin → **89.9%** | Absorb it; overage bills above the $120 allowance. |
| Sonnet intro pricing ends 1 Sep | +50% on all Sonnet lines | Already modelled at post-September rates. No exposure. |
| NAT gateway chosen, 1 tenant | Infra $19 → $75; margin → **90.0%** | Real at low tenant count, immaterial past ~10 tenants. |
| **Human oversight rises to 4 hrs/month** | Non-AI COGS $135 → $525; margin → **76.6%** | **This is the real risk.** Cut the human from the loop or raise price. |
| **Self-serve tier at $300/month** | AI $59 + minimal human $33 + infra $5 = $97; margin **67.7%** — and **48.7%** on a heavy tenant | The module's premise applies in full downmarket. Don't go there. |

**The self-serve row is the sharpest finding.** At $2,500 the AI is 2% of revenue. At $300 it is 20% before a human touches it, and a heavy user takes it to 39%. The same product, the same cost base, and a completely different business. This is the number behind "price against a salary, not a seat."

## Break-even

The only true fixed cost in the unit model is the EC2 box at $19/month. Contribution per tenant at expected volume is **$2,500 − $190 = $2,310/month**.

Infrastructure break-even is therefore reached at **well under one tenant** — the first client covers the running platform 120× over.

The meaningful break-even is against the **platform build cost**, not the running cost:

```
months to recover = build cost ÷ (tenants × $2,310)
```

At 5 tenants that is $11,550/month of contribution. Build cost is not yet quantified — see open items.

## Board one-pager

**Before — services delivery.** Revenue is a retainer against human capacity. Gross margin is decent but growth is headcount-bound: every new client needs more delivery hours, so revenue and cost scale together and the business cannot outrun hiring.

**After — hosted product.** $2,500/tenant/month against $194 of COGS, of which **$59 is AI and $130 is one hour of human oversight**. Gross margin ~92% at the unit level, and — the part that matters — **adding a tenant no longer requires adding a person.** The cost curve flattens where the services curve was linear.

**The narrative:** the usual AI story is "margin compresses, defend it with cascading." That is not this business — cascading is worth **0.06 points** here, because a product whose value is strategic reasoning has almost no cheap work to route away. Priced against a salary rather than a seat, inference is 2% of revenue and a 3× cost shock costs six points. **The margin question for Mariella is how much human oversight each tenant needs** — one hour holds 92%, four hours takes it to 77%. Every engineering hour spent reducing oversight is worth more than every hour spent reducing tokens.

**The hedge:** the commercial model already carries a usage lever (credit allowance + overage rolled to the next invoice), so a genuine cost shock passes through without renegotiation. And it caps the downside on the scenario that would hurt — an agent-heavy tenant on a flat fee.

## What is still unmeasured

Stated plainly, because the module rewards knowing which numbers are real.

| Item | Status | How it gets closed |
|---|---|---|
| Turns per tenant per month | **Estimated** — the largest remaining uncertainty | Count a month of real usage from the daily internal user |
| Full consultant setup pass | **Partially measured** ($3.46 without audit) | One complete run through audit + confirm-strategy |
| Human oversight hours at steady state | **Assumed** at 1 hr @ $130 loaded | Track across the first paying tenants |
| Consultant time for onboarding | **Not quantified** | Needed to price the onboarding fee properly |
| Platform build cost | **Not quantified** | Needed for a real payback period |
| NAT vs public IP | **Open decision**, worth ~$50/month | Engineering call |
| Is Opus worth 41% more than Sonnet? | **Untested** — worth ~$24/tenant/month | Run one consultant pass on each agent, compare output quality |
| Effort tuning (`xhigh` today) | **Untested** — cheapest available lever, no cache penalty | Sweep `medium`/`high` on report and cadence sessions |
| Session length / context compaction | **Untested** — the largest lever, no quality trade-off | Measure cost per turn across a long session |

What *is* measured: cost per turn, cost of a partial setup pass, that prompt caching works and saves ~90%, the Opus-vs-Sonnet delta, and the EC2 instance cost. Those were the four biggest unknowns in v1.
