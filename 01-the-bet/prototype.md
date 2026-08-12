# The Prototype Bet

**What I built:** a multi-tenant runtime, in build. The engine has run end-to-end as a prototype (a setup pass wrote a real client's knowledge base; a client run drew from it). The production server (per-tenant isolation, a credential vault that substitutes secrets at egress, scheduled runs) is still in build. Two layers share one store: consultant setup (one-off) and client cadence. Onboarding is charged as a services fee and kept out of the product moat; there's no ongoing curation.

**Tool:** Cursor / Claude Code — Node on a managed agent runtime, object storage, credential vault. A clickable mockup wouldn't test the real risk, which is whether the multi-tenant runtime works.

**Prototype link:** ⟨ add — interim: a 60-second capture of a live tenant run ⟩

**Archetype:** Orchestrator (approval-gated Copilot surface, Creator output).

**The bet:** lean B2B teams already asking "can you do it for us?" will pay for a marketing function that runs and ties results back to a deal, hosted multi-tenant with no secret ever seen by staff.

**Confidence:** ships ~85%; a client pays $2,500/mo ~50%; compounds ~45%.

**Kill criteria:**

- Rework >30% on two consecutive clients → reprice as a consultant tool.
- Oversight (beta 5–7 hrs): target ≤2 hrs by month 3, kill at >4 hrs → reprice as a service. *(Restated in M6 — ≤2 is the target, >4 the trigger; M3 puts ~7 hrs at ~72% margin, so 2–4 hrs is costly, not fatal.)*
- No cross-client benchmark within 6 months → it's delivery tooling.
- >1 in 3 onboardings fail the integration gate → re-scope.
