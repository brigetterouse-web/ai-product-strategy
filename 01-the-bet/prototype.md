# The Prototype Bet

## What I Built

A hosted multi-tenant runtime for the Mariella engine. An orchestrator (Node) drives one session per tenant on Anthropic Managed Agents: mounts the engine plus that tenant's PLAN and knowledge files, answers the engine's prompts through its approval gates, then harvests outputs back into the tenant's versioned S3 prefix.

**Verified, not claimed:**
- **Consultant setup end-to-end** (2026-07-23) — dogfooded on Think & Grow's own site; researched the company and wrote all 7 knowledge files, harvested to the store.
- **Folder structure preserved in both directions** (W67, 2026-07-27) — CMA's file transfer carries a filename but never a folder, so `/` is encoded as `~` and decoded on harvest. A consultant run wrote 8 files that landed as real nested directories including a 2-deep path, and a client run against the re-keyed store located and quoted from `brand-voice.md`.
- **Mount paths corrected** (2026-07-27) — CMA re-roots `mount_path` under `/mnt/session/uploads`; the bootstraps now name the real effective paths, so the agent reads the engine directly instead of hunting for it every run.

**And the engine itself is already in production on the older client-hosted path** — this is the stronger proof and it predates the runtime work. Mariella delivered a marketing audit for **Wink Models** (26 Jun) off real client data with Klaviyo and GA4 connected; and **CJ Robinson at T&G uses it daily** — 90-day strategy and budget, event ROI modelling against a $50k-per-10-attendees target, monthly content plans, newsletter click-rate analysis, and recurring scheduled tasks that keep its own SEO/AEO/GEO guidance current.

**Honestly not done on the hosted platform:** Vaults and the integrations re-wired through them, the client-facing interface, the aggregation warehouse, and the always-on host — the orchestrator runs **from a laptop**. The consultant→client handoff has proven transport but not handoff: it gates on `marketing-strategy-confirmed.md`, which needs a full consultant pass no run has completed. These are gaps in the *migration target*, not in the product as delivered.

## Tool Used

Cursor / Claude Code — Node + `@anthropic-ai/sdk` against Anthropic Managed Agents, S3-backed per-tenant store.

Deliberately **not** v0 or Lovable. The bet is about a *runtime* — multi-tenant, secret-isolated, scheduled — not a screen. A clickable mock would prove less than the working thing does.

## Prototype Link

**Not a mock — a product in use.** The assignment asks for a clickable prototype; what exists is better evidence than one. There is a recorded internal walk-through (*Mariella Collateral Walk-Through*, 22 Jul, in Drive) and two live tenants.

**The real gap is a client-facing demo**, and it is already an owned action from the 22 Jul session: CJ — as the primary user — is to produce a screen recording or case study showing the actual workflow, because the team confirmed it has no formal demo. That artifact is what belongs in this field, and it also unblocks sales collateral.

Interim for M6: link the walk-through recording, or a 60-second capture of a live run.

## AI Value Archetype

**Orchestrator** (dominant) — two modes and a mode router: PLAN decides what and when, PRODUCE makes the assets from the plan, both reading and writing the same living decision layer, with campaign IDs threading attribution from pillar to deal.

- **Copilot** surface: human approval on every asset; never publishes without an explicit trigger; email always drafted, never sent.
- **Creator** output: the assets themselves — social, ads, lead magnets, emails, website copy, testimonials.

Orchestrator economics dominate: high value, high infra spend, autonomy risk. That is why M3 (margin) and M5 (guardrails) are the sharp modules for this product.

## The Bet in One Sentence

That lean marketing teams of 1–3 at $200K–$1M+ spend will pay for a marketing function that **runs** — a living plan that produces every asset against it and attributes the result back to a deal — instead of hiring a $120–180k/yr content person or driving a copilot themselves; and that T&G can host it multi-tenant without any staff member ever seeing a client secret.

## Kill Criteria

Evidence, with dates. Any one firing means stop, not "review."

1. **Rework.** If two consecutive tenants' weekly deliverables need >30% human rework before they can ship, the cadence isn't autonomous enough to sell as work. → Stop; reprice as a consultant tool, not a product.
2. **Economics.** If AI COGS per tenant exceeds 25% of that tenant's retainer at target usage once T&G hosts. Post-pivot every token is on T&G's P&L where the client's keys used to pay for it. → Stop before onboarding client #4 and restructure pricing first. *(M3 tests this. There is currently no cost view at all — W45.)*
3. **Compounding.** If the cross-tenant aggregation plane is not live by **31 Dec 2026**, concede that Mariella is delivery tooling rather than a product and stop investing in it as one.
4. **The data story.** If the GA4 / Search Console / LinkedIn integrations are not live by **30 Sep 2026**, the marketer-buyer's data story stays inference-only — "half information" — and the wedge fails on its own USP. → Stop selling the data story and sell speed alone, or stop.

---

## Artifact #0 — the CEO question

See [`ceo-question.md`](ceo-question.md). Private until M6.
