# The Prototype Bet

## What I Built

A hosted multi-tenant runtime for the Mariella engine. An orchestrator drives one session per tenant: it mounts the engine plus that tenant's PLAN and knowledge files from their isolated store, drives the conversation through the engine's human-approval gates, and harvests the outputs back into versioned per-tenant storage. Client credentials live in a vault and are substituted into outbound API calls at egress, so they never enter the running agent — no T&G staff member can read a client token, and every access is logged.

Proven end to end: a full consultant setup pass researched a real company and wrote its complete knowledge base; nested folder structure round-trips in both directions; a client-layer run then located and drew from that tenant's brand voice. The two engine layers (consultant for setup, client for the recurring cadence) share one tenant store with a handover marker between them.

## Tool Used

Cursor / Claude Code — Node against a managed agent runtime, with per-tenant object storage and a credential vault.

Deliberately **not** v0 or Lovable. The bet is a *runtime* — multi-tenant, secret-isolated, scheduled — not a screen. A clickable mock would prove less than the working thing does.

## Prototype Link

**The gap is a client-facing demo, and it's the one thing worth building next.** What exists is the runtime and a recorded internal walk-through; what's missing is the artefact a prospect can watch. The primary user is producing a screen recording of the real workflow — that's what belongs in this field, and it doubles as sales collateral.

Interim for M6: link the walk-through recording, or a 60-second capture of a live tenant run.

## AI Value Archetype

**Orchestrator** (dominant) — two modes and a mode router: PLAN decides what and when, PRODUCE makes the assets from the plan, both reading and writing the same living decision layer, with campaign IDs threading attribution from pillar to deal, on a scheduled cadence.

- **Copilot** surface: human approval on every asset; never publishes without an explicit trigger; email always drafted, never sent.
- **Creator** output: the assets themselves — social, ads, lead magnets, emails, website copy, testimonials.

Orchestrator economics dominate: high value, high infra spend, autonomy risk. That's why M3 (margin) and M5 (guardrails) are the sharp modules for this product.

## The Bet in One Sentence

That lean marketing teams of 1–3 at $200K–$1M+ spend will pay for a marketing function that **runs** — a living plan that produces every asset against it and attributes the result back to a deal — instead of hiring a $120–180k/yr content person or driving a copilot themselves; and that Think & Grow can host it multi-tenant without any staff member ever seeing a client secret.

## Kill Criteria

Evidence, with dates. Any one firing means stop, not "review."

1. **Rework.** If two consecutive tenants' weekly deliverables need >30% human rework before they can ship, the cadence isn't autonomous enough to sell as work. → Stop; reprice as a consultant tool, not a product.
2. **Labour, not tokens.** If human oversight per tenant exceeds 4 hours/month at steady state, gross margin falls below 80% and the product is a service with a software price. → Stop and either raise price or cut the human from the loop. *(M3 shows this is the real margin risk — inference is under 1% of revenue.)*
3. **Compounding.** If the cross-tenant benchmark plane is not live by **31 Dec 2026**, concede that Mariella is delivery tooling rather than a product and stop investing in it as one.
4. **The wedge.** If more than 1 in 3 onboardings can't clear the GA4 + Search Console + LinkedIn integration gate, the data story that converts the marketer buyer never lands, and the product is competing on speed alone. → Re-scope the wedge or stop.

---

## Artifact #0 — the CEO question

See [`ceo-question.md`](ceo-question.md). Private until M6.
