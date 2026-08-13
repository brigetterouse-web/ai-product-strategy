# The Prototype Bet

**What I built:** a multi-tenant runtime, in build. The engine has run end-to-end as a prototype (a setup pass wrote a real client's knowledge base; a client run drew from it). The production server (per-tenant isolation, a credential vault that substitutes secrets at egress, scheduled runs) is still in build. Two layers share one store: consultant setup (one-off) and client cadence. Onboarding is charged as a services fee and kept out of the product moat; there's no ongoing curation.

**Tool:** Cursor / Claude Code — Node on a managed agent runtime, object storage, credential vault. A clickable mockup wouldn't test the real risk, which is whether the multi-tenant runtime works.

**Prototype link:** No protype link, it is mid-build. 

**Archetype:** Orchestrator (approval-gated Copilot surface, Creator output).

**The bet:** lean B2B teams already asking "can you do it for us?" will pay for a marketing function that runs and ties results back to a deal, hosted multi-tenant with no secret ever seen by staff.

**Confidence:** ships ~65%; a client pays $2,500/mo ~50%;# Three-Axis Vulnerability Diagnostic

**Product:** Mariella, a hosted, multi-tenant AI marketing engine for lean B2B marketers. The product is structured in 2 phases; an initial audit of existing marketing activities run by the hosting company (to ascertain any discrepancies and clarify strategic aims) and a subsequent operating cadence. The operating cadence is where majority of the design exists as it is the phase that the client owns the interaction with the product. Because there are many outcomes marketers could achieve by utilizing this product, we have categorised them through 'Plan', 'Produce' & 'Reporting' mechanisms. 'Plan' outcomes include living strategy documents (based on company data and best practice), website assets (based on SEO, GEO & AEO), event planning ROI spreadsheets & content calendars (optimized specially for the platform in use). Whilst 'Produce' outcomes would be the first instagram post on the content calender (for example). Produce stages can be on weekly timers (i.e. every Monday marketers approve 5 linkedin posts based on company data, best practice, what succeeds on linkedin and what is happening in the market with competitors). Finally, a key component of this product is the 'Reporting' mechanism. Informed by company integrations (CRM, website analytics like GA4, linkedin API, Meta API, CDM etc), it assesses 'what works' on each planning mechanism based on the strategic aims set out in the audit. The data, therefore, informs and distinguishes a pattern of what kind of marketing content produces each companies' goals and suggests that for future use.

**Your Role:** Product owner.

## Scores

**Contextual Moat — 2/5**
*Workflow depth × switching cost. Would users leave in a weekend if a competitor showed up?*
Score rationale: No one embedded yet; switching cost is on paper until a client accrues months of use with integrations.
Named attacker: HubSpot Breeze — same CRM data, already paid for.

**Data Advantage — 2/5**
*Proprietary signal that compounds with usage. What do you see that OpenAI doesn't?*
Score rationale: The loop — read a client's platforms together, learn what works, produce from it. Runs internally; unproven on outcomes and revenue.
Named attacker: Semrush — bigger sample, so win on relevance.

**Platform Exposure — 2/5**
*Encroachment risk × pivot speed. If Apple/Google/OpenAI ships your hero feature native, then what?*
Score rationale: Engine is copyable markdown on the vendor's runtime.
Named attacker: Anthropic — supplies our runtime and the substitute.

## Top Vulnerability

Differentiation. A client will happily buy the outcome without needing it to be us.

## Confidence Level

M — ~85% ships · ~50% they pay $2,500/mo (no paying clients) 

**Kill criteria:**

- If we have to rework >30% on two consecutive clients → reprice as a consultant tool.
- The cost of human overversight becoming too high, in beta the target is 5–7 hrs, if it is ~10 → reprice as a service.
- No cross-client benchmark within 6 months → it's delivery tooling.
- >1 in 3 onboardings fail the integration gate → re-scope.
