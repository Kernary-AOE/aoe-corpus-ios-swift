# ValueTypesByDefault [rule] v0.1.0
Value types — `struct`, `enum`, tuples — give Swift its data-race safety, predictable equality, and copy-on-write performance. The standard library is built on them: `Array`, `Dictionary`, `String`, `Set`, `Date`, all `URL`-derived types. Use them as the default for any new type that represents data, configuration, or a record. Reach for `class` only when identity, deinit cleanup, or shared mutable state through references is genuinely required.
domain: ios-swift
