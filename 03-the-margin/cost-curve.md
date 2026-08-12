# Cost Curve & Pricing Strategy

**Product:** Mariella — hosted multi-tenant AI marketing engine.

Today: one flat Claude seat ($180.89/mo, capped, single-user, doesn't scale). The hosted product runs on the metered API; figures are estimates, caching assumed on.

## Cost Model (hosted, per client/month, beta)

| Line | Estimate |
|------|----------|
| AI (~200–450 turns) | ~$75–200 |
| Infrastructure | ~$5 |
| Oversight (beta 5–7 hrs @ ~$75) | ~$375–525 |
| **COGS** | **~$455–730** |
| **Margin @ $2,500** | **~75–80%** |

At ~1 hr oversight, ~90%. Without caching, AI runs 3–5× and margin ~65–70%.

## Cascading Strategy

Sonnet for mechanical stages, Opus for strategy and client copy. ~5% cheap / 95% frontier, so cascading barely helps. The levers that matter are oversight hours and caching.

## Packaging Decision

- **Leader:** PLAN, cadence, campaign production.
- **Filler:** reports, visibility check.
- **Killer:** human onboarding — ~3 days, ~$1,800.
- **Killer usage:** 100%, but once each — one-off setup fee.
- **Decision:** bundle Leader + Filler; charge onboarding separately.

## Pricing Model

$2,500/mo subscription (current estimate, not yet quoted to a client), hybrid base + metered overage, 13-month contract at the 12-month price, credit allowance, one-off onboarding fee.

## Stress Tests

| Scenario | Margin | Response |
|----------|--------|----------|
| No caching | ~65–70% | burst the turns, approve at the end |
| Oversight stuck ~7 hrs | ~72% | reduce, or accept a services margin |
| Oversight → 1 hr | ~90% | the target |
| Self-serve $300/mo | negative | oversight alone exceeds the price |

## Board One-Pager

Before: a retainer against human capacity, headcount-bound. After: $2,500 against ~$455–730 COGS (mostly oversight), ~75–80% now, rising to ~90% as oversight falls. It clears the usual 40–60% only because the $2,500 price keeps AI small and the engine keeps delivery hours down; lose either and it drops back to agency margins. It pays back within the first client.
