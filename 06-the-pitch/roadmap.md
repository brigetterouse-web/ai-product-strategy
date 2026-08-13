# Three-Horizon Roadmap & Board Pitch

## Roadmap

### Horizon 1, Ship (0-4 weeks)

High confidence. Ship with existing capabilities. Earns H2 credibility.

| Initiative | Strategy Component | Metric | Confidence |
|-----------|--------------------|--------|------------|
| Close the consultant-to-client handover | Bet | Consultant run writes the strategy marker; client run reads it | H |
| Always-on host for the orchestrator | Moat | A tenant session runs from the host, not a laptop | M |
| Orchestrator hardening and unattended cadence | Moat | CLI byte-identical after refactor; second concurrent session refused | M |
| Engine v7.6 join-first audit | Bet | Content-to-deal join is section 1; placeholder parity 99/99 | H |
| Refusal path when no CRM is connected | Contract | No-CRM audit declines to headline engagement metrics | H |
| Prove isolation and secret containment | Guardrails | Tenant A can't read B; no secret in any log, store or tool arg | H |
| Cost view and per-run metering | Margin | Cost per session written to usage.jsonl every run | M |
| Finalise pricing and fix the collateral | Margin | Price signed off; no artefact still says EC2 | M |
| Demand tests | Bet | 5 ICP calls done; Breeze counter-position written | M |

### Horizon 2, Validate (1-3 months)

Medium confidence. Strategic bets with named hypothesis + kill criteria.

| Initiative | Hypothesis | Kill Criteria | Confidence |
|-----------|-----------|---------------|------------|
| Land the first paying client at $2,500 (Margin) | The ICP pays this price | No verbal yes by month 2, signature by month 3 → reprice | M |
| Migrate pilot client and onboard client #2 (Moat) | Runs stay isolated under real multi-tenancy | Not live by month 3 → stop | M |
| Wire GA4, Search Console and LinkedIn (Bet) | Real client data turns the audit from inference to evidence | Not live on one tenant by week 10 → stop selling data-led audits | M |
| Credential model and per-tenant Vaults (Guardrails) | Credentials substitute at egress; no token enters the agent | Token in any prompt or tool arg by week 8 → proxy instead | M |
| Onboarding and integration gate (Contract) | Clients connect the required integrations rather than walk | >1 in 3 onboardings fail the gate by month 3 → re-scope | M |
| Client web interface (Bet) | Clients want self-serve, not a consultant-run session | No pilot uses it weekly by month 3 → stay consultant-operated | M |
| Close the deal-outcome join (Bet) | Campaign IDs resolve to deals | <50% resolve by week 12 → drop attribution | M |
| Cut oversight to two hours per client (Contract) | Golden rows shrink the review queue | Oversight over 4 hours at month 3 → reprice as a service | M |
| Eval harness and acceptance metric (Contract) | A regression gate holds quality as the engine changes | First-pass acceptance under 70% across two clients by month 3 → reprice as a service | M |
| COGS levers: caching and effort tuning (Margin) | Caching holds COGS where the 75-80% margin assumes it | Margin under 70% at month 3 → reprice | M |
| Benchmark warehouse and priors (Moat) | Cross-tenant records pool; excluded types provably dropped | No cross-client benchmark by month 6 → delivery tooling, not a product | M |
| Portability seam and escape-hatch drill (Moat) | A tenant flips to in-house execution with no rewrite | Drill needs a rewrite → portability claim is false, retract it | M |
| Pre-pilot security, DPA and monitoring (Guardrails) | The governance pack clears a paying client without bespoke legal work | Pilot's legal review stalls past month 3 → fund counsel | M |

### Horizon 3, Explore (3-6 months)

Low confidence. Small-investment experiments. New behavior or market.

| Initiative | What must be true first | Metric | Confidence |
|-----------|-------------------------|--------|------------|
| Publishing autonomy (Guardrails) | Over 99% accuracy on the action | Assets publish without losing sender-of-record | L |
| Outcome-based pricing pilot (Margin) | Attribution trustworthy enough to meter | Attributed enquiries metered on one tenant | L |

Unmapped items: session archiving, brand-token extraction, engine-layer drift reconciliation — none maps to a component on its own, so all three were folded into the initiatives above.

## AI Evaluation

Run your strategy through the 6 evaluation lenses before the pitch.

| Lens | Verdict | Notes |
|------|---------|-------|
| Bet Validation, evidence-backed or just conviction? | Weak | Engine proven and in daily use; no paying clients, USP not landing |
| Capability Gaps, realistic to build? | Real | Server in build, deal-join open, caching still to engineer |
| Defensibility, platform-proof or copyable? | Holds, weak point named | Engine copyable; moat is PLAN + lineage + benchmark, and the benchmark is unbuilt |
| Pricing Alignment, economics hold under stress? | Holds | ~75-80% in beta; price untested, oversight the swing |
| Trust & Reliability, contract explicit and measurable? | Holds in design | Guardrails running; nothing scores output quality yet |
| Impact & Scale, what breaks at 10x? | Partial | Compounds per client; company-level loops broken or missing |

AI tool used: Claude.
Biggest pushback received: margin overstated, demand assumed.
What you changed as a result: dropped the margin from 95% to ~80% and named caching as load-bearing, moved the top vulnerability to differentiation, split confidence by claim, cut the "paying engagements" claim, and added four demand initiatives the backlog didn't have.

## Board Pitch

Thesis (1 sentence): a 1-3 person marketing team spending $200K-$1M a year can't fund the hire that would make that spend work, so we sell them that person's job, running.

The case:
Why now: the reasoning is now good enough that the bottleneck is a confirmed plan rather than content generation, hosting moves the knowledge base to us, and the alternative these teams face is a $120-180k salary they can't fill.
What's defensible: the durable assets are the plan each client confirms and owns, the campaign-ID trail that runs from decision to revenue, their data held behind an integration gate, and a benchmark that exists only because we host it. The engine itself is copyable.
The economics: we charge $2,500 a month against roughly $455-730 in COGS, which holds a 75-80% margin that depends on caching still being built, plus a one-off onboarding fee of about $1,800, and the margin rises towards 90% as oversight falls.

The risks:
Trust / failure modes: because clients publish under their own brand, provenance rules and an unwaivable approval gate apply, and email is drafted but never sent.
Scale / governance: there is no write-back tool and liability stays with the client, but the 24 initiatives sit with two people, one of whom is departing.
Competitive: HubSpot Breeze owns the CRM join key and is already paid for, though the more honest risk is simpler, which is that we have no paying clients yet and the plan is nearly all build.

The ask: we need the capacity to ship the server, run the demand tests and land the first clients over about three months, with a hard review at month 3 against the H2 kill lines.

## M1 Baseline vs. Now

Your 3-sentence AI strategy from Module 1 vs. what you'd say now:

M1 baseline: "An AI marketing engine that creates data-led marketing across multiple siloed systems — it runs an audit, integrates a client's systems, and lets marketers plan strategy and produce outcomes based on competitive best practice and their own data on what works. The strategy is to own the professional-services marketing workflow end to end rather than sell another content tool."

Now: lean B2B teams will pay for a marketing function that runs and ties back to a deal, because they can't fund the alternative hire. The durable assets are the confirmed plan, the attribution trail and a hosted benchmark — not the engine, which is copyable. Priced against a salary it holds ~75-80% margin once caching lands, and it's fundable because the risks are instrumented and we'd stop on named kill criteria; the open question the backlog still doesn't answer is whether a client pays and the loop turns.
