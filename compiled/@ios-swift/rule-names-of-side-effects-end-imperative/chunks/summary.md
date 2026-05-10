# NamesOfSideEffectsAreImperative [rule] v0.1.0
The grammar of a method name signals whether it mutates. Mutating methods use imperative verb phrases: `array.sort()`, `set.insert(x)`, `string.append("!")`. Their non-mutating counterparts use the past participle (`-ed`) or present participle (`-ing`) form: `array.sorted()`, `string.appending("!")`. When `-ed` is awkward, prefer the noun phrase: `x.union(y)` (non-mutating) vs. `x.formUnion(y)` (mutating).
domain: ios-swift
