# Three-Axis Diagnostic

**Product:** Mariella — a multi-tenant, hosted AI marketing engine for lean B2B marketing teams (Think & Grow)
**Operating model:** PLAN & PRODUCE (two modes)
**Path:** B — AI-native. The intelligence is the product, not a sidebar.
**Dominant archetype:** Orchestrator (Copilot surface, Creator output)

## What the product is

Mariella is a hosted marketing function. Each client is a tenant on Think & Grow's server with their own isolated store; they connect their own systems (GA4, Search Console, LinkedIn, email/CRM) through a credential vault so no T&G staff member ever sees a token. The engine runs two modes: **PLAN** owns a living decision layer — confirmed strategy, content pillars, the content and event calendar, budget and per-event ROI, campaign plans — and **PRODUCE** derives every asset from that plan: social posts, ads, lead magnets, emails, website copy, testimonials. Every publishing item carries a **campaign ID** that threads content → traffic → enquiry → deal. Human approval is required on every asset; nothing publishes without an explicit trigger. Cross-tenant performance is aggregated into a company-level benchmark plane.

**ICP:** Australian-focused. Lean marketing teams of 1–3, $200K–$1M+ annual marketing spend, AI-literate and actively avoiding "AI slop." Two-buyer GTM: the founder buys *desire + speed*, the marketer buys *the data story*. It displaces a **$120–180k/yr content hire**.

**Commercial model:** subscription (a $20–30k one-off was considered and rejected), 13-month contract at the 12-month price, API cost bundled to a credit allowance with overage invoiced the following month and an alert at 90%.

> Scored 1 = pain, 5 = strong. Calibration: Figma = deep moat, thin ChatGPT wrapper = shallow.

| Axis | Score |
|------|-------|
| Contextual Moat | **4**/5 |
| Data Advantage | **4**/5 |
| Platform Exposure | **2**/5 |

---

## 1. Contextual Moat — 4/5

**Workflow depth × switching cost.**

**Rationale:** Mariella isn't a content generator with a briefing document — it's where the marketing function makes decisions. PLAN holds the confirmed strategy, the pillar set and the calendar; PRODUCE cannot route around them, because a PLAN-FIRST gate stops any request that lacks a plan input and explicitly refuses to fabricate a pillar to proceed. The tenant's knowledge base, learnings and campaign-ID history live in T&G's hosted store, and the client's data systems are connected through T&G's vault.

Leaving means re-deciding the strategy, rebuilding the pillars and calendar, re-authorising every integration, and abandoning the attribution lineage that connects past marketing to past revenue. That's rebuilding how the function operates, not swapping which tool writes the posts.

**Workflow depth on the spectrum:** genuine **workflow layer** — for a lean marketing team it approaches an operating system.

**Named attacker:** **HubSpot Breeze** (hubspot.com → Breeze AI). Clients already pay for HubSpot; Breeze agents sit where the CRM and campaign data already live. It attacks the exact seam the attribution spine has to reach across — the CRM contact/company join key — from the inside, with no integration to negotiate.

**Why not 5:** the client's strategy is deliberately *theirs* — they confirm and own the PLAN layer, which is right for trust and caps lock-in by design. The outputs are consumed outside the product, so nothing in the client's business stops if they leave. And a competitor could re-onboard the same client with the same integrations inside a few weeks. Switching is expensive; it isn't architectural.

---

## 2. Data Advantage — 4/5

**Proprietary signal that compounds.**

**Rationale:** Three compounding mechanisms, and the third is what hosting exists to create:

1. **The attribution spine.** Campaign IDs born in PLAN join published asset → traffic → enquiry → deal. That lineage — *which marketing decision produced which revenue* — is signal no platform holds: HubSpot has the deal but not the plan-to-asset provenance; Semrush has search performance but no deal outcome.
2. **The living-strategy amend loop.** A pattern — a pillar repeatedly rejected, a stated change in ICP or positioning — prompts the engine to ask whether to amend the confirmed strategy, and logs what drove the change. The plan learns, not just the next draft. Every PRODUCE turn is captured; real-time signals accumulate per tenant with 60-day archive hygiene.
3. **The cross-tenant benchmark plane.** Normalized, source-tagged performance records (search, site analytics, AI visibility, email) aggregate to company-level benchmarks every tenant can read, and that eventually feed back into PLAN recommendations.

**Named attacker:** **Semrush** (semrush.com). Cross-account search and content performance across millions of domains. Any market-level claim Mariella makes from aggregated tenant data, Semrush can already make from a far bigger sample — so the benchmark has to win on *relevance to a cohort*, not on volume.

**Why not 5:** the privacy model deliberately caps what pools. CRM, audience and email records never enter the aggregation plane, the plane is company-level only with a minimum-cohort floor, and no verbatim content crosses tenants. That's the right call — it's what makes the trade sellable — but it means the pooled signal is thinner than an unconstrained competitor's.

---

## 3. Platform Exposure — 2/5

**If a platform ships your wedge natively tomorrow, then what?**

**Rationale:** The engine is markdown — a written body of marketing judgment — executing on a frontier model. Nothing in the artifact is hard to copy or hard to host. Model vendors ship agent-skill marketplaces, and the open-source marketing-skills library the engine descends from is public and free; T&G's own fork was made private specifically to protect the IP, which is both the correct move and the tell.

The scarce ingredient is the judgment written into the engine. Written judgment is forkable judgment.

**Named attacker:** **Anthropic** (anthropic.com — Claude Agent Skills / skills marketplace). Uncomfortable, and that's the point: **the same vendor supplies the runtime and the substitute.** Second-order: **OpenAI AgentKit** (openai.com).

---

## Top Vulnerability

**Three of Mariella's four learning loops compound inside a tenant and the fourth barely compounds across them — so the product gets better for every client it serves while the asset doing the work is portable text on the runtime of the vendor most likely to replace it.**

## Confidence: **M**

The demand side is answered: a real ICP with a quantified alternative (a content hire), a pricing model agreed at leadership level, paying engagements, and daily power users who reach for it rather than dutifully log in. The architecture is right — per-tenant isolation, credentials the operator can't read, a decision layer the client owns.

M rather than H because the thing that converts this from a well-run service into a compounding product — the cross-tenant benchmark loop — is the newest and least proven part of the design, and because the engine itself is the most copyable asset in the business.

---

## Stress-test — the strongest counter-argument

The most exposed score is **Contextual Moat (4)**, and the sharpest attack on it is this: every artifact in the moat is a file the client owns a copy of, so a switching cost measured in weeks of re-onboarding is a speed bump, not a moat.

That is conceded on the documents and answered on the lineage. The files port; the campaign-ID history joining past decisions to past revenue does not, because it only exists where the plan and the outcome data were joined. **The moat is the lineage, not the documents** — which is also why the attribution spine, not the engine, is the asset worth defending.
