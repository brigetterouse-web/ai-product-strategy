# Kill Switch Audit

**Product:** Mariella — hosted multi-tenant AI marketing engine.
**Test:** provider swap in under 48 hours.

## Vendor Dependency Assessment

| Dimension | State | Risk | 48-hour action |
|-----------|-------|------|----------------|
| Provider | one vendor — the agent control plane (sandboxes, vault, scheduled runs) | M | keep `runtime.*` provider-agnostic; spike a second adapter |
| Abstraction | store and runtime behind one interface | L | new calls go through the interface, not the SDK |
| Routing | single-model; switching breaks the cache | L | populate the per-stage model field |
| Eval | golden-set harness built, not yet gating deploys | M | freeze the set; gate deploys on regression |

## Portability Score

**Partial — in build, not tested.** Store is portable and ours; runtime sits behind an interface. The multi-tenant server — what lets learnings compound and lets us turn a client's access on or off — is still being built.

## If the provider doubles pricing

Not a real threat: inference is ~2% of revenue and the credit allowance passes usage through. Margin is set by oversight hours; inference cost is minor.

## If the provider ships a competing product

**Defensible:** the client-owned PLAN, the campaign-ID lineage, per-client data, the benchmark once it exists. **Not defensible:** the engine, which is copyable markdown.
