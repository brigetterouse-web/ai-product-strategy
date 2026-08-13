# Compounding System Design

## Feedback Loops

| Loop | Input | Output | Compounds? | Status |
|------|-------|--------|-----------|--------|
| Recursive Learning | approval edits, rejections | next run drops rejected hooks, resurfaces deferred ideas | Y | active |
| Cross-Domain Transfer | one confirmed PLAN | one pillar improves six asset types | Y | active |
| Network Intelligence | cross-client records | cross-client priors feed PLAN | Y | missing |
| Attribution Learning | campaign IDs → deal | recommends pillars on what drove revenue | Y | broken |
| Quality / Eval | corrections → golden rows | company quality bar + regression gate | Y | missing |

Broken loop identified by partner: the broken loop is Attribution Learning. Campaign IDs are minted, but the deal-join isn't closed, so revenue never feeds back into the PLAN.
Fix plan: make the deal-outcome join a gating step in onboarding.

## Context Connectivity

Context moves freely within a single client but is deliberately walled off between clients. The only shared asset is the golden set, and the cross-client aggregation pipe that would connect them isn't built yet.

## Governance Policy

Scope: governance covers all client-facing output and excludes internal staff AI use.
Autonomy boundaries: the agent reads and drafts on its own, but publishing, sending and amending the PLAN are never automatic. There is no write-back tool, and cross-client aggregation happens only at company level with human approval.
Escalation triggers: a run escalates to a human on a held-tier item, an unsourced numeral, an injection flag, a PLAN change, a client's first run, a gate-waiver request, or a regulated claim.
Audit cadence:

| When | Check | Owner |
|------|-------|-------|
| Real-time | rule checks at assembly | Brigette |
| Weekly | judge run | Alex |
| Monthly | tier and escalation review | Brigette |
| Quarterly | privacy review | Alex |

Regulatory exposure (EU AI Act / other): AU Privacy Act / APPs primary; GDPR if EU contacts; EU AI Act limited-risk. 
Risk tier: limited. 
Controls: the agent drafts email and the client stays sender of record; a golden-set regression gate covers the quality/eval loop, but it is specified not running, so the weekly judge run has nothing to execute until it lands.

## Agent Topology

| Agent | Can | Can't | Approval owner |
|-------|-----|-------|----------------|
| Orchestrator | run sessions, mount files, harvest output | read credentials, publish, cross a client | Brigette |
| Consultant (setup) | research, write the knowledge base | publish, send, amend PLAN unasked | Alex |
| Client (cadence) | read PLAN and data, draft assets | send, publish, write back | Brigette |

## Shadow AI Audit

| Tool | Owner | Risk Level | Decision |
|------|-------|-----------|----------|
| External chatbot — restyle an asset per channel | client | M | build (bring in-product) |
| Zapier / Make — scheduler | client | M | partner |
| AI design tools — finish the asset | client | L | partner |
| Manual re-check of a sourced figure | client | L | TBD |
| Other AI — ad-hoc market questions | client | L | ignore |

Total tools found: 5
Tools after triage: 3 actioned (1 build, 2 partner); 1 ignore, 1 TBD
Estimated hidden spend: $0/mo (surveyed users)
