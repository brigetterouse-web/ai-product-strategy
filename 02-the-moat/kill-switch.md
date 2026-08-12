# Kill Switch Audit

**Product:** Mariella — hosted multi-tenant AI marketing engine.
**Test:** provider swap in under 48 hours.

## Vendor Dependency Assessment

| Dimension | State | Risk | 48-hour action |
|-----------|-------|------|----------------|
| Provider | one vendor — the agent control plane (sandboxes, vault, scheduled runs) | M | keep `runtime.*` provider-agnostic; spike a second adapter |
| Abstraction | store and runtime behind one interface | L | new calls go through the interface, not the SDK |
| Routing | single-model; switching breaks the cache | L | populate the per-stage model field |
| Eval | golden set specified (M4), no harness runs it | H | build the harness (MAR-56), then gate deploys on regression |

## Portability Score

**Partial — in build, not tested.** Store is portable and ours; runtime sits behind an interface. The multi-tenant server — what lets learnings compound and lets us turn a client's access on or off — is still being built.

## If the provider doubles pricing

Absorbable, but not the non-issue it first looked like. Inference is ~3–8% of revenue with caching on (M3: ~$75–200 against $2,500) and ~9–40% without it — and caching is still unbuilt (MAR-55). Once it lands, a doubling is covered by the credit allowance passing usage through, and oversight hours still set the margin. Until then, a price rise is a live margin risk.

## If the provider ships a competing product

**Defensible:** the client-owned PLAN, the campaign-ID lineage, per-client data, the benchmark once it exists. **Not defensible:** the engine, which is copyable markdown.
