# The Prototype Bet

**What I built:** a multi-tenant runtime, in build. The engine has run end-to-end as a prototype (a setup pass wrote a real client's knowledge base; a client run drew from it). The production server (per-tenant isolation, a credential vault that substitutes secrets at egress, scheduled runs) is still in build. Two layers share one store: consultant setup (one-off) and client cadence. Onboarding is charged as a services fee and kept out of the product moat; there's no ongoing curation.

**Tool:** Cursor / Claude Code — Node on a managed agent runtime, object storage, credential vault. A clickable mockup wouldn't test the real risk, which is whether the multi-tenant runtime works.

**Prototype link:** No prototype link — it's mid-build.

**Archetype:** Orchestrator (approval-gated Copilot surface, Creator output).

**The bet:** lean B2B teams already asking "can you do it for us?" will pay for a marketing function that runs and ties results back to a deal, hosted multi-tenant with no secret ever seen by staff.

**Confidence:** M — ~65% if we ship the server, ~25% if it stays as is.

**Kill criteria:**

- Rework >30% on two consecutive clients → reprice as a consultant tool.
- Oversight (beta 5–7 hrs): target ≤2 hrs by month 3, reprice as a service at >4 hrs.
- No cross-client benchmark within 6 months → it's delivery tooling.
- >1 in 3 onboardings fail the integration gate → re-scope.
