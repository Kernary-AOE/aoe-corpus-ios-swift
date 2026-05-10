# NamesOfSideEffectsAreImperative [rule] v0.1.0
The grammar of a method name signals whether it mutates. Mutating methods use imperative verb phrases: `array.sort()`, `set.insert(x)`, `string.append("!")`. Their non-mutating counterparts use the past participle (`-ed`) or present participle (`-ing`) form: `array.sorted()`, `string.appending("!")`. When `-ed` is awkward, prefer the noun phrase: `x.union(y)` (non-mutating) vs. `x.formUnion(y)` (mutating).
domain: ios-swift

## Checks
- [ ] Mutating methods are imperative verbs (`sort`, `reverse`, `append`, `remove`).
- [ ] Non-mutating versions of the same operation use `-ed` / `-ing` (`sorted`, `reversed`, `appending`) or `form-` prefix on the mutating side (`formUnion`, `formIntersection`).
- [ ] Side-effect-free methods that return a value read as a noun phrase describing the value (`x.distance(to: y)`, `array.lazy`).
- [ ] Boolean methods read as assertions about the receiver (`isEmpty`, `contains(x)`, `intersects(other)`).

## Label
Mutating methods read as imperatives; non-mutating versions read as nouns or past participles

## Label
Mutating methods read as imperatives; non-mutating versions read as nouns or past participles
