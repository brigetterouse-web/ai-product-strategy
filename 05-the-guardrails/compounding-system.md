# Compounding System, Governance & Shadow AI

**Product:** Mariella — hosted multi-tenant AI marketing engine.

## Feedback Loops

| Loop | Input | Output | Compounds? | Status |
|------|-------|--------|-----------|--------|
| Recursive Learning | approval edits, rejections | next run drops rejected hooks, resurfaces deferred ideas | Y | active |
| Cross-Domain Transfer | one confirmed PLAN | one pillar improves six asset types | Y | active |
| Network Intelligence | cross-client records | cross-client priors feed PLAN | Y | missing |
| Attribution Learning | campaign IDs → deal | recommends pillars on what drove revenue | Y | broken |
| Quality / Eval | corrections → golden rows | company quality bar + regression gate | Y | missing |

**Broken loop identified by partner:** Attribution Learning — campaign IDs mint, but the deal-join isn't closed, so revenue never feeds back to PLAN.

**Fix plan:** Make the deal-outcome join a gating onboarding step.

## Context Connectivity

<!-- How does knowledge flow across teams and domains? Where does it silo? -->

**How knowledge flows:** Context moves freely inside one client.

**Where it silos:** Deliberately walled off between clients. The shared asset is the golden set; the cross-client aggregation pipe isn't built yet.

## Governance Policy

**Scope:** all client-facing output; excludes internal staff AI use.

**Autonomy boundaries:** read and draft, auto. Publish, send and PLAN-amend, never auto. No write-back tool. Cross-client aggregation company-level only, and human approval required.

**Escalation triggers:** (1) held tier · (2) unsourced numeral · (3) injection flag · (4) PLAN change · (5) first run for a client · (6) gate-waiver request · (7) regulated claims.

**Audit cadence:**

| When | Check | Owner |
|------|-------|-------|
| Real-time | rule checks at assembly | Brigette |
| Weekly | judge run | Alex |
| Monthly | tier and escalation review | Brigette |
| Quarterly | privacy review | Alex |

**Regulatory exposure:** AU Privacy Act / APPs primary; GDPR if EU contacts; EU AI Act limited-risk. **Risk tier: limited.** Controls: email is drafted by the agent and the client remains sender of record; a golden-set regression gate on the quality/eval loop (corrections → golden rows → company quality bar) — *specified, not yet running (MAR-56), so the weekly judge run has nothing to execute until it lands.*

## Agent Topology

| Agent | Can | Can't | Approval owner |
|-------|-----|-------|----------------|
| Orchestrator | run sessions, mount files, harvest output | read credentials, publish, cross a client | Brigette |
| Consultant (setup) | research, write the knowledge base | publish, send, amend PLAN unasked | Alex |
| Client (cadence) | read PLAN and data, draft assets | send, publish, write back | Brigette |

## Shadow AI Audit (user-side)

### Discover — user-side workarounds

| Workaround | Source | Signal | Freq | Spend | Decision |
|------------|--------|--------|------|-------|----------|
| Paste an asset into a chatbot to restyle per channel | support ticket | workflow gap | H | $0/mo | build |
| Zapier/Make into a scheduler | Zapier/Make | workflow gap | H | $0/mo | partner |
| AI design tools finish the asset | support ticket | capability gap | H | $0/mo | partner |
| Re-verify an already-sourced figure | support ticket | trust gap | L | $0/mo | TBD |
| Ad-hoc market questions elsewhere | support ticket | pricing gap | M | $0/mo | ignore |

### Pattern assessment

**Workarounds found:** 5 · **Build:** 1 · **Partner:** 2 · **Ignore:** 1 · **TBD:** 1

**Adjacent spend:** $0/mo · **Dominant signal:** workflow gap

### Action plan

**Build**
- Per-channel restyling inside the product, so the asset never leaves it.

**Partner**
- Scheduler integration (Zapier/Make) for the publish step.
- AI design tools for asset finishing.

**Ignore + monitor**
- Ad-hoc market questions asked elsewhere — expected, not a product gap.

**TBD**
- Re-verifying an already-sourced figure — a trust gap, low frequency; decide against M4's sourcing contract.

### Roadmap brief

Five user-side workarounds discovered: 1 build · 2 partner · 1 ignore · 1 TBD. Estimated adjacent spend $0/mo across surveyed users. Dominant signal: **workflow gap** — users are stitching Mariella into multi-step pipelines, so the strongest near-term move is partner integrations with the AI tools they already chain in.

Sequence the build column by frequency × strategic relevance. Confirm partner candidates with the external tools' partnership teams. Re-run this audit each quarter — workarounds shift fast.
