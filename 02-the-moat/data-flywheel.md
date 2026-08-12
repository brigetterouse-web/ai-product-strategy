# Data Flywheel Map

**Product:** Mariella — hosted multi-tenant AI marketing engine.

Mechanisms built and proven on internal use; company-level loops need the server and more clients.

## Flywheel Loops

| Loop | What it measures | Score |
|------|------------------|-------|
| Correction | fixes captured and reused | 3/5 |
| Preference | learns team preferences | 3/5 |
| Domain Context | one area lifts adjacent ones | 3/5 |
| Network | each client improves it for everyone | 1/5 |

**Correction — 3.** Signals logged, applied as overrides next run; proven internally, not on a paying client, no retraining.
**Preference — 3.** Brand voice, style guide and PLAN enforced per client; human-seeded, internal only.
**Domain Context — 3.** One PLAN improves six asset types; used heavily internally.
**Network — 1.** Cross-client benchmark impossible with one client; not built yet.

**Total: 10/20. Weakest: Network (1)** — the loop HubSpot Breeze attacks directly.
**Fix for weakest loop:** ship the server, onboard client #2, stand up the aggregation pipe.

## Encroachment Threat Assessment

| Attacker | Vector | Time | Value at risk |
|----------|--------|------|---------------|
| Anthropic (platform) | agent-skill marketplaces fork a plan-layer agent | 6–12 mo | ~50% (engine) |
| Copy.ai (vertical) | already sells agentic GTM, goes deeper | 6–9 mo | 30–40% |
| HubSpot Breeze (adjacent) | owns the CRM join key, already paid for | ~12 mo | ~40% (decision surface) |
| Mutinex (measurement) | channel-level MMM, needs 2+ yrs and $1M+ | low | low on ICP |

## 90-Day Encroachment Plan

**HubSpot Breeze:** ships free portal benchmarks, then a content agent that attributes natively at no cost, until our setup reads as overhead.
**Defense:** win on cohort relevance — read GA4, Search Console and LinkedIn together, keep PLAN in-house, let HubSpot keep the CRM, and price the consultant as services. The durable assets are the plan, the attribution lineage and the benchmark.
