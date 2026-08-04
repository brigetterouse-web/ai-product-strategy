# Compounding System, Governance & Shadow AI

**Product:** Mariella — hosted multi-tenant AI marketing engine (Think & Grow)
**The pair of questions:** does this get smarter the more it is used, and what is already happening around it that nobody scheduled?

---

## Feedback Loops

Five loops rather than the template's three, because Mariella's attribution spine and its eval layer are distinct circuits from the three canonical mechanisms and they fail in different ways.

| Loop | Input | Output | Compounds? | Status |
|------|-------|--------|-----------|--------|
| **Recursive learning** (correction + preference) | Every approval-gate edit, rejection and deferral, with its reason, captured to the tenant's signals log | Next run suppresses rejected hook types, resurfaces deferred ideas as deferred, and applies monthly recommendations over general defaults | **Y** — within the tenant | **active** |
| **Cross-domain transfer** | One confirmed PLAN layer — strategy, pillars, calendar, budget, per-event ROI | Six asset types improve at once from a single sharpened pillar: post, ad, lead magnet, email, website copy, testimonial | **Y** — within the tenant | **active** |
| **Attribution learning** | Campaign IDs joining pillar → asset → traffic → enquiry → deal | Evidence of which pillars and hooks actually produce revenue, feeding back into PLAN recommendations | **Y** — the highest-value loop in the product | **broken** |
| **Network intelligence** | Normalized, source-tagged performance records across tenants, company-level and above a minimum-cohort floor | Cross-tenant priors informing pillar and hook recommendations for every tenant | **Y** — the only loop that compounds at company level | **missing** |
| **Quality / eval** | Corrections promoted into golden-dataset rows; judge scores against the frozen set | A company-level quality bar that improves for all tenants, and a regression gate on every engine change | **Y** — turns per-tenant tuning into a company asset | **missing** |

**Why "broken" and "missing" are the honest labels, not a softer word:**

- **Attribution learning is broken, not missing.** The spine is real and campaign IDs are minted on every publishing item, so the loop exists end to end on paper. It does not close because the join to *closed revenue* depends on CRM connectivity that is partial across the tenant base. The decisions are logged, the outcomes are not reliably returned. A loop that logs its inputs and loses its outcomes is broken in the exact sense the module means.
- **Network intelligence is missing, not broken.** The substrate exists — records are normalized and source-tagged, and the privacy model is settled — but no pipe has been built, so there is nothing to fail. Calling it broken would flatter it (see [`../02-the-moat/data-flywheel.md`](../02-the-moat/data-flywheel.md), where it scores 2/5).
- **The eval loop is missing by sequence, not by oversight.** It is fully specified in M4 and is the next thing built (see [`../04-the-contract/golden-dataset.md`](../04-the-contract/golden-dataset.md)).

### The freeze test

**Freeze Mariella for three months — one frontier cycle. No engine updates, no model swap, no new features. Still winning?**

**For an existing tenant: yes, and legitimately.** The signals log keeps accumulating, the PLAN layer keeps encoding decisions no competitor can see, and the engine's output keeps getting better tuned to that tenant. Nothing about that improvement depends on a model upgrade. That is a genuine compounding loop, not a beneficiary of someone else's.

**For Think & Grow as a company: no.** Frozen for three months, the company learns almost nothing transferable. Tenant three onboards to exactly the same starting quality as tenant one. What would degrade instead is raw copy fluency relative to the frontier — and fluency is the one thing model vendors ship for free, so riding it was never the bet.

> **Verdict: Mariella compounds per client and scales as a company.** The freeze test reproduces the M2 flywheel finding by a completely different route — three loops strong inside a tenant, the cross-tenant loop absent — which is a useful independent confirmation rather than a coincidence. Two of the five loops above are the entire difference between a compounding product and excellent delivery tooling.

### Broken loop and fix plan

**Broken loop:** attribution learning. Named flow, concrete failure, measurable consequence — campaign IDs are written at publish and the enquiry-to-deal outcome never returns for tenants whose CRM is unconnected, so the engine recommends pillars on engagement proxies while the one signal that would prove marketing ROI sits unjoined in a system Mariella can read but is not required to.

**Fix plan:** promote the deal-outcome join from an optional integration to a **gating onboarding requirement**, alongside GA4 and Search Console in the integration gate. The gate already decides whether the data story lands (kill criterion 4); this makes the revenue half of that story mandatory rather than best-effort. Measurable: percentage of published campaign IDs that resolve to a deal outcome within the quarter, reported per tenant.

---

## Context Connectivity

Knowledge silos in three places, and only the first is deliberate.

**By design:** per-tenant stores are isolated from each other. That is the privacy model and it is what makes the multi-tenant trade sellable — not a break to fix.

**The break that matters:** resolution knowledge stays with the consultant who resolved it. When an exception is handled in a session, the correction reaches that tenant's signals log and stops there. It does not reach a shared quality asset, so the same class of correction is discovered independently for each new tenant. This is the single reason the product does not learn from real usage at company level, and it is what the M4 golden set exists to fix — promoting recurring corrections into rows is the connective tissue.

**The second break:** engine improvements are authored centrally rather than derived from tenant signal. The signals exist, and the living-strategy amend prompt already reads patterns *within* a tenant, but nothing reads patterns *across* tenants to propose an engine change. That path is the same pipe the network loop needs, which is why one piece of infrastructure closes two loops.

---

## Governance Policy

### Maturity placement

**Level 2 — trust architecture — climbing to Level 3.** M4 built the evals, confidence tiers and reliability contract, which is Level 2. Level 3 is unusually available here: the client publishes Mariella's output under their own brand, so "show me how you test this" is not a procurement formality for this buyer, it is the purchase decision. Two artifacts already function as sales assets — the tier distribution showing the engine declining to answer when it should, and the credential vault making "no T&G staff member can read your tokens" a structural claim rather than a policy promise. Governance is GTM for this product specifically.

### The one-pager

| Field | Policy |
|---|---|
| **Scope** | All client-facing AI output produced by the Mariella engine for T&G tenants: the PLAN decision layer, every PRODUCE asset, performance reporting, and the cross-tenant benchmark plane. **Excludes** T&G staff use of general-purpose AI tools for internal work, which is a separate internal policy and a security concern rather than a product one. |
| **Autonomy boundaries** | **Read and analyse** connected sources — auto. **Draft any asset** — auto. **Publish or send anything** — never auto; requires the client's own trigger, and email is always drafted. **Amend a confirmed PLAN** — never auto; ask-first with the driver logged. **Write back to a client system** — not permitted at all; integrations are read-only. **Cross-tenant aggregation** — company-level only, opt-in, above the minimum-cohort floor, with CRM, audience and email record types excluded by policy. |
| **Escalation triggers** | (1) Held tier — missing plan input, dead connection, or a figure that would have to be invented. (2) Any unsourced numeral detected in a gated field. (3) Prompt-injection flag on ingested content. (4) A PLAN amendment request. (5) First cadence run for a new tenant. (6) Any request to waive the approval gate. (7) Any claim in client-facing copy touching legal, financial, regulated or health matters. |
| **Audit cadence** | **Continuous** — rule-based provenance checks at assembly, every asset. **Weekly** — judge run against the frozen golden set (owner: engine owner). **Monthly** — review of the Derived / Flagged / Held distribution plus every escalation (owner: accountable consultant per tenant). **Quarterly** — full policy and privacy review, required before any change to the aggregation plane (owner: T&G leadership). Owners are named by role deliberately, so the policy survives staffing changes. |
| **Regulatory exposure** | **EU AI Act: limited risk.** Marketing content generation is neither prohibited nor high-risk; transparency obligations apply — the client always knows the output is AI-generated, which the approval gate makes structural. **Australian Privacy Act and the APPs** are the primary regime, since the ICP is AU-focused: data minimisation in prompts, no training on client data, and credentials held in a vault that staff cannot read. **GDPR** applies to any tenant with EU-resident contacts. **Spam legislation** — because email is drafted and never sent, the client remains the sender of record and holds the consent obligation, which is a deliberate allocation of liability, not an accident of design. **Log retention** to SOC-2-style controls, treated as a procurement requirement rather than a compliance floor. |

---

## Agent Topology

Mariella ships agents, so this is not optional. Four governance knobs, applied.

| Agent | Can | Cannot | Approval |
|---|---|---|---|
| **Orchestrator** | Start and stop sessions, mount the engine plus that tenant's files, harvest outputs back to the tenant store | Read client credentials — the vault substitutes them at egress · publish anything · cross a tenant boundary | No client-facing output, so no approval surface |
| **Consultant layer** (setup) | Research a company, read connected sources, write the tenant knowledge base | Publish · send email · amend a confirmed PLAN without asking | Client confirms the strategy before any PRODUCE run |
| **Client layer** (cadence) | Read PLAN, tenant knowledge and performance records; draft assets; propose amendments | Send · publish · write to any client system | Client approves every asset, every time |

**Tool calls.** Allow-listed read-only connectors only — GA4, Search Console, LinkedIn, email/CRM read. There is no write-back tool in the allow-list, which removes an entire class of irreversible action rather than governing it. Every call is logged with its result, and credentials are substituted at egress so no agent ever holds a plaintext token.

**Memory classes.** *Short-term:* the session. *Long-term:* the per-tenant store, isolated. *Shared across tenants:* company-level pre-aggregated rates only, opt-in, above the cohort floor, no PII and no verbatim content — and a hard no, permanently, for CRM, audience and email records. The usual advice is that shared memory is a hard no for anything customer-facing; Mariella's variation is that shared memory is permitted **only in aggregate**, which is precisely what makes the network loop legal to build.

**Chain ownership.** Consultant layer hands to client layer through an explicit handover marker in the tenant store. The **PLAN-FIRST gate is the stop-the-chain trigger**: if the handover marker or any required plan input is absent, the chain halts and escalates rather than proceeding on assumption. Named ownership at the handoff sits with the accountable consultant for that tenant.

---

## Shadow AI Audit

User-side, not CISO-side. What Mariella's users build with AI *around* the product.

**On the numbers.** Frequency is labelled from observed tenant behaviour where it exists and marked **expected** where the tenant base is too small to support a frequency claim. Stage is a fact about the audit, not a reason to skip it or to invent counts.

| Workaround | Signal source | Signal type | Frequency | Decision |
|---|---|---|---|---|
| Pasting an approved asset into a general chatbot to shorten or restyle it per channel | Observed in tenant sessions | **Workflow gap** | Recurring | **Build** — channel-native variants at generation, not as a post-step |
| Zapier / Make recipes pushing approved copy into a scheduler | Integration behaviour | **Workflow gap** | Recurring | **Partner** — make the handoff official. Publishing is a deliberate governance boundary, so absorbing it would trade the liability position for convenience |
| AI design tools turning a lead magnet's copy into a finished designed asset | Observed | **Capability gap** | Recurring | **Partner** — Mariella produces copy and strategy, not design, and owning design would widen scope without deepening the moat |
| Re-asking a chatbot to verify a statistic Mariella already sourced | Observed | **Trust gap** | Expected, low volume | **Neither build nor partner — re-open M4.** Someone double-checking a sourced figure is telling you the provenance is present but not legible at the point of use |
| Ad-hoc competitor or market questions taken elsewhere between scheduled runs | Observed | **Pricing / packaging gap** | Expected | **Ignore** — the ad-hoc strategy chat already covers this at $10/month of usage; the gap is awareness and packaging, not capability |

**Workarounds found:** 5
**Build candidates:** 1 build · 2 partner · 1 re-opens M4 · 1 ignore
**Adjacent spend:** **~$90–160 per tenant per month**, modelled from the tools these workarounds imply — chatbot seats for one to three people, an AI design subscription, an automation plan. Marked modelled, not measured.

**The finding is not the spend.** At roughly 4–6% of a $2,500 subscription, adjacent spend is not a pricing threat and pretending otherwise would be the flattering read. The valuable signal is *shape*: three of five workarounds are the product's output being carried somewhere else, which says the boundary of Mariella is drawn one step short of where the work actually finishes. The trust-gap row is the one worth losing sleep over, because it is the only one that reports a weakness in something already shipped rather than an absence.

**The trap avoided.** One build out of five. Two partners, because a workaround caused by a deliberate boundary should be made official rather than absorbed — the scheduler row exists *because* publishing is gated, and that gate is a liability allocation worth keeping.

---

## Red-team — where the guardrails would fail first

Run adversarially against the policy above rather than in defence of it.

**1. "Read-only integrations" is a boundary that will be pushed.** The most requested next capability from a lean team is inevitably "just post it for me," and every part of the liability position — client as sender of record, client as approver, client as publisher — rests on refusing that. **Response:** the refusal is priced, not absolute. Publishing can only be revisited behind the reliability contract's >99% bar on the specific action, and the Partner decision in the shadow AI audit exists so that saying no does not mean saying nothing.

**2. The approval gate is the trust product and the fatigue risk simultaneously.** A gate on every asset is legible and defensible; it is also the thing a busy client will start clicking through without reading, at which point it provides liability cover without providing review. **Response:** the Flagged tier is what carries the load — it names the specific figure to check rather than asking for blanket approval — and first-pass acceptance plus oversight hours are reported as a pair precisely because approval volume alone cannot show whether review is real.

**3. Two of five loops being unbuilt is a strategy risk, not a backlog item.** The network and eval loops are the only two that compound at company level, and both are one shared pipe away. Every quarter they stay unbuilt, the freeze-test verdict stays "scales as a company," and the M1 compounding kill criterion moves closer to firing. **Response:** they are sequenced as one piece of work, not two, and the kill criterion is the deadline.

**4. Governance-as-GTM has a shape problem at this size.** Level 3 assumes a buyer who runs a procurement process. A lean team of one to three often has no security review at all, so the governance artifacts may impress nobody in the room where the deal closes. **Response:** the audience for Level 3 here is the *next* tier of buyer, and the artifacts are being built at the standard that tier requires rather than the standard the current tier demands — which is a deliberate bet on where the ICP moves, and should be stated as one rather than assumed.
