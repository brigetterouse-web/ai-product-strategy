# Data Flywheel Map

**Product:** Mariella — hosted multi-tenant AI marketing engine.
Mechanisms built and proven on internal use; company-level loops need the server and more clients.

## Flywheel Loops

| Loop | What It Measures | Score 1 | Score 5 | Score |
|------|------------------|---------|---------|-------|
| Correction | Do users fix AI outputs? Is that signal captured and reused? | No capture | Automated retraining | 3/5 |
| Preference | Does the product learn individual / team preferences over time? | Stateless | Deep personalization | 3/5 |
| Domain Context | Does usage in one area improve quality in adjacent areas? | Siloed | Cross-domain transfer | 3/5 |
| Network | Does each new user / team make the product better for everyone? | Isolated | Strong network effects | 1/5 |

### Correction Loop — 3/5
What do you capture today? Approval edits and rejections, logged as signals.
How does it compound? Applied as overrides next run. Proven internally, not on a paying client; no retraining.

### Preference Loop — 3/5
What do you capture today? Brand voice, style guide and PLAN, per client.
How does it compound? Enforced every run. Human-seeded, internal only.

### Domain Context Loop — 3/5
What do you capture today? One confirmed PLAN per client.
How does it compound? One PLAN improves six asset types. Used heavily internally.

### Network Loop — 1/5
What do you capture today? Nothing cross-client yet.
How does it compound? Cross-client benchmark is impossible with one client; not built yet.

**Total Flywheel Score:** 10/20
**Weakest Loop:** Network (1) — the loop HubSpot Breeze attacks directly.
**Fix for weakest loop:** ship the server, onboard client #2, stand up the aggregation pipe.

## Encroachment Threat Assessment

### 1. Platform Encroachment
Attacker: Anthropic.
Vector: agent-skill marketplaces fork a plan-layer agent.
Time-to-threat: 6–12 mo.
% of value at risk: ~50% (the engine).

### 2. Vertical Competitor
Attacker: Copy.ai.
Vector: already sells agentic GTM, goes deeper. Data they hold that we don't: a far larger GTM usage corpus.
Time-to-threat: 6–9 mo.
% of value at risk: 30–40%.

### 3. Adjacent Expansion
Attacker: HubSpot Breeze.
Vector: owns the CRM join key, already paid for. Distribution advantage: already inside the client's CRM and seat.
Time-to-threat: ~12 mo.
% of value at risk: ~40% (the decision surface).

## 90-Day Encroachment Plan

Attacker: HubSpot Breeze.
Attack vector (target the weakest loop — Network): free benchmarks then native attribution, attacking the cross-client loop before we have one.
Weeks 1 to 4, what they ship: free portal benchmarks.
Weeks 5 to 8, how they poach users: a content agent that attributes natively at no cost.
Weeks 9 to 12, why users don't come back: our setup reads as overhead next to something already paid for.
Your defense: win on cohort relevance — read GA4, Search Console and LinkedIn together, keep PLAN in-house, let HubSpot keep the CRM, and price the consultant as services. The durable assets are the plan, the attribution lineage and the benchmark.
