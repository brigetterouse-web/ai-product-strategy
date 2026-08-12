# Three-Horizon Roadmap & Board Pitch

**Product:** Mariella — hosted multi-tenant AI marketing engine. **Audience:** CEO / leadership.

## Roadmap

*24 initiatives rolled up from a 75-item backlog export. Pillar shown in brackets where the table has no component column.*

### Horizon 1, Ship (0-4 weeks)

High confidence. Ship with existing capabilities. Earns H2 credibility.

| Initiative | Strategy Component | Metric | Confidence |
|---|---|---|---|
| Close the consultant-to-client handover | Bet | A consultant run writes the confirmed-strategy marker and a client run reads it | H |
| Always-on host for the orchestrator | Moat | A real tenant session runs from the host, not a laptop | M |
| Orchestrator hardening and unattended cadence | Moat | CLI behaviour byte-identical after the refactor; a second concurrent session is refused | M |
| Engine v7.6 join-first audit | Bet | The content-to-deal join is section 1 of the audit; placeholder parity holds at 99/99 | H |
| Refusal path when no CRM is connected | Contract | An audit with no CRM declines to headline engagement metrics | H |
| Prove isolation and secret containment | Guardrails | Tenant A cannot read tenant B; no secret in any log, store or tool argument | H |
| Cost view and per-run metering | Margin | Cost per session written to `usage.jsonl` on every run | M |
| Finalise pricing and fix the collateral | Margin | Price signed off; zero artefacts still saying EC2 | M |
| Demand tests | Bet | Five ICP discovery calls done; HubSpot Breeze counter-position written | M |

### Horizon 2, Validate (1-3 months)

Medium confidence. Strategic bets with named hypothesis + kill criteria.

| Initiative | Hypothesis | Kill Criteria | Confidence |
|---|---|---|---|
| Land the first paying client at $2,500 *(Margin)* | The ICP pays this price | If we don't see a verbal yes by month 2 and a signature by month 3, we reprice | M |
| Migrate pilot client and onboard client #2 *(Moat)* | Runs stay isolated under real multi-tenancy | If it isn't live by month 3, we stop | M |
| Wire GA4, Search Console and LinkedIn *(Bet)* | Real client data turns the audit from inference into evidence | If integrations aren't live on one tenant by week 10, we stop selling data-led audits | M |
| Credential model and per-tenant Vaults *(Guardrails)* | Credentials substitute at egress so no token ever enters the agent | If a token appears in any prompt or tool argument by week 8, we stop and proxy instead | M |
| Onboarding and integration gate *(Contract)* | Clients will connect the required integrations rather than walk | If more than 1 in 3 onboardings fail the gate by month 3, we re-scope | M |
| Client web interface *(Bet)* | Clients want self-serve access, not a consultant-run session | If no pilot client uses it weekly by month 3, we stay T&G-operated | M |
| Close the deal-outcome join *(Bet)* | Campaign IDs resolve to deals | If under 50% resolve by week 12, we drop attribution | M |
| Cut oversight to two hours per client *(Contract)* | Corrections captured as golden rows shrink the review queue | If oversight is over 4 hours at month 3, we reprice as a service | M |
| Eval harness and acceptance metric *(Contract)* | A regression gate holds quality as the engine changes | If first-pass acceptance is under 70% across two clients by month 3, we reprice as a service | M |
| COGS levers: caching and effort tuning *(Margin)* | Caching holds COGS where the 75-80% margin assumes it | If margin is still under 70% at month 3, we reprice | M |
| Benchmark warehouse and priors *(Moat)* | Cross-tenant records pool with excluded types provably dropped | If there's no cross-client benchmark by month 6, it's delivery tooling, not a product | M |
| Portability seam and escape-hatch drill *(Moat)* | A tenant flips to T&G-owned execution with no rewrite | If the drill needs a rewrite, the portability claim is false and we retract it | M |
| Pre-pilot security, DPA and monitoring *(Guardrails)* | The governance pack clears a paying client without bespoke legal work | If a pilot client's legal review stalls past month 3, we fund counsel | M |

### Horizon 3, Explore (3-6 months)

Low confidence. Small-investment experiments. New behavior or market.

| Initiative | What must be true first | Metric | Confidence |
|---|---|---|---|
| Publishing autonomy *(Guardrails)* | Over 99% accuracy on the action | Assets publish without losing sender-of-record | L |
| Outcome-based pricing pilot *(Margin)* | Attribution is trustworthy enough to meter | Attributed enquiries metered on one tenant | L |

**Unmapped items:** session archiving, brand-token extraction, engine-layer drift reconciliation. None connects to a strategy component on its own — all three were folded into the initiatives above rather than carried as line items.

## AI Evaluation

Run your strategy through the 6 evaluation lenses before the pitch.

| Lens | Verdict | Notes |
|---|---|---|
| Bet Validation, evidence-backed or just conviction? | Weak | Engine proven and in daily use; no paying clients, USP not landing |
| Capability Gaps, realistic to build? | Real | Server in build, deal-join open, caching still to engineer |
| Defensibility, platform-proof or copyable? | Holds, weak point named | The engine is copyable; the moat is PLAN + lineage + benchmark, and the benchmark is unbuilt |
| Pricing Alignment, economics hold under stress? | Holds | ~75-80% in beta; the price is untested and oversight is the swing |
| Trust & Reliability, contract explicit and measurable? | Holds in design | Guardrails running; nothing scores output quality yet |
| Impact & Scale, what breaks at 10x? | Partial | Compounds per client; the company-level loops are broken or missing |

**AI tool used:** Claude.
**Biggest pushback received:** margin overstated, demand assumed.
**What you changed as a result:** margin 95% → ~80% with caching named as load-bearing, top vulnerability moved to differentiation, confidence split by claim, the "paying engagements" claim dropped, and four demand initiatives added because the backlog contained none.

## Board Pitch

**Thesis (1 sentence):** A 1-3 person marketing team spending $200K-$1M a year can't fund the hire that would make that spend work, so we sell them that person's job, running.

**The case:**

- **Why now:** Reasoning is good enough that the bottleneck is a confirmed plan, not content generation; hosting moves the knowledge base to us; the alternative is a $120-180k salary they can't fill.
- **What's defensible:** The plan each client confirms and owns, the campaign-ID trail from decision to revenue, their data behind an integration gate, and a benchmark that only exists because we host it. The engine itself is copyable.
- **The economics:** $2,500/mo against ~$455-730 COGS (~75-80%, contingent on caching, which is in build), plus a one-off onboarding fee of ~$1,800, rising to ~90% as oversight falls.

**The risks:**

- **Trust / failure modes:** Clients publish under their own brand, so provenance rules and an unwaivable approval gate; email is drafted, never sent.
- **Scale / governance:** No write-back tool, liability stays with the client, and all 75 initiatives sit with two people — 47 on one.
- **Competitive:** HubSpot Breeze owns the CRM join key and is already paid for. The honest risk is simpler: no paying clients yet, and the plan is nearly all build.

**The ask:** Capacity to ship the server, run the demand tests, and land the first clients over ~3 months, with a hard review at month 3 against the H2 kill lines.

## M1 Baseline vs. Now

Your 3-sentence AI strategy from Module 1 vs. what you'd say now:

**M1 baseline:** "An AI marketing engine that creates data-led marketing across multiple siloed systems — it runs an audit, integrates a client's systems, and lets marketers plan strategy and produce outcomes based on competitive best practice and their own data on what works. The strategy is to own the professional-services marketing workflow end to end rather than sell another content tool."

**Now:** Lean B2B teams will pay for a marketing function that runs and ties back to a deal, because they can't fund the alternative hire. The durable assets are the confirmed plan, the attribution trail and a hosted benchmark — not the engine, which is copyable. Priced against a salary it holds ~75-80% margin once caching lands, and it's fundable because the risks are instrumented and we'd stop on named kill criteria; the open question the backlog still doesn't answer is whether a client pays and the loop turns.
