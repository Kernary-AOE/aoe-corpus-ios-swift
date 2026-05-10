# ValueTypesByDefault [rule] v0.1.0
Value types — `struct`, `enum`, tuples — give Swift its data-race safety, predictable equality, and copy-on-write performance. The standard library is built on them: `Array`, `Dictionary`, `String`, `Set`, `Date`, all `URL`-derived types. Use them as the default for any new type that represents data, configuration, or a record. Reach for `class` only when identity, deinit cleanup, or shared mutable state through references is genuinely required.
domain: ios-swift

## Checks
- [ ] New domain types are declared `struct` (records, configurations, DTOs, view-state, model values).
- [ ] Closed sets of named cases are declared `enum`, often with associated values for case-specific data.
- [ ] Equatable / Hashable conformance for value types is synthesised by the compiler — declared but not hand-written.
- [ ] Copy-on-write is relied on for performance: large `struct` payloads use COW under the hood (`Array`, `Dictionary`, custom COW box) rather than being prematurely converted to `class`.

## Label
Model new types as struct or enum unless reference semantics are required
