# Cost Curve & Pricing Strategy

**Product:** Mariella — hosted multi-tenant AI marketing engine.
**Today:** one flat Claude seat ($180.89/mo, capped, single-user, doesn't scale). The hosted product runs on the metered API; figures are estimates, caching assumed on. Unit below is per client (tenant)/month, beta.

## Cost Model

| Cost Category | Per-Client/Month | Notes |
|---------------|------------------|-------|
| Inference (primary model) | ~$71–190 | Opus — strategy and client copy; ~95% of turns |
| Inference (cascading/triage) | ~$4–10 | Sonnet — mechanical stages; ~5% of turns |
| Infrastructure | ~$5 | per-tenant object storage, runtime |
| Data/storage | incl. above | folded into infrastructure |
| Human-in-the-loop | ~$375–525 | oversight, beta 5–7 hrs @ ~$75 |
| Total AI COGS | ~$455–730 | — |

Margin @ $2,500: ~75–80% (beta). Without caching, inference runs 3–5× and margin ~65–70%.

## Cascading Strategy

Triage model: Sonnet — mechanical stages.
Frontier model: Opus — strategy and client copy.
Routing rule: stage-based — mechanical → Sonnet, strategy/copy → Opus.
Expected cascade ratio: ~5% cheap / 95% frontier, so cascading barely helps. The levers that matter are oversight hours and caching.

## Pricing Model

Current pricing: one flat Claude seat, $180.89/mo (capped, single-user).
Proposed AI pricing: $2,500/mo subscription (estimate, not yet quoted to a client) + one-off onboarding fee (~$1,800). Credit allowance; 13-month contract at the 12-month price.
Model: hybrid — base + metered overage.

## Stress Tests

| Scenario | Impact on Margin | Response |
|----------|------------------|----------|
| Inference costs 3x (no caching) | ~65–70% — AI moves from ~3–8% to ~9–40% of revenue | ship caching (MAR-55); burst the turns, approve at the end |
| Heaviest segment doubles (oversight → ~12 hrs) | falls toward agency levels (~50%) | reduce via golden rows and eval, or accept a services margin |
| Model provider raises prices 50% | +1.5–4 pts with caching (absorbable); material without it | credit allowance passes usage through; oversight still sets margin |

## Board One-Pager

*Before/After: old retainer/hire economics vs. AI usage revenue. Per client/month.*

**Before (traditional SaaS):** ~$10–15k/mo retainer or $120–180k/yr hire · COGS mostly labour, **fixed** · gross margin ~40–60% · scales by headcount · gross $ ~$5–7.5k.

**After (AI-enabled):** $2,500/mo base + metered overage · COGS ~$455–730, **variable** (oversight-led; inference ~$75–200) · gross margin **~75–80%** → ~90% as oversight falls · scales by software · gross $ ~$1,950.

**Net margin shift:** **+15–40 pts, up not down** — the reverse of the usual AI story. The $2,500 price keeps inference at ~3–8% of revenue and the engine kills delivery hours. Client pays ~80% less than the hire they can't fund; growth comes from client volume + overage, not bigger seats. Hedge: caching (load-bearing) + oversight reduction — lose either and it reverts to agency margins.
