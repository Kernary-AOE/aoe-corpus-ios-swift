# OptionalChainingOverNilCheck [rule] v0.1.0
When the goal is 'do this only if the value is present, otherwise produce nothing or a default', Swift gives three short-circuiting forms that are clearer than an `if x != nil` check followed by a body that uses `x!`. Optional chaining (`a?.b?.c()`) propagates nil. Nil-coalescing (`x ?? default`) supplies a fallback. Pattern matching (`if case let .some(value) = x`) reads the cases explicitly. Each removes a force-unwrap and makes the absence-handling part of the expression.
domain: ios-swift

## Checks
- [ ] `if x != nil { use(x!) }` is rewritten using optional chaining, `if let`, or `guard let` — never paired with a force-unwrap on the same value.
- [ ] Cascading optional access goes through `?.` chains; intermediate `if let` ladders are flattened where the result type tolerates nil.
- [ ] Defaulting an optional to a concrete value uses `??` (`name ?? "Anonymous"`), not a ternary on `!= nil`.
- [ ] Comparing an optional to a non-nil value uses direct equality (`if x == 5`); the compiler wraps the literal in `.some(5)` and the comparison reads naturally.

## Label
Prefer `?.`, `??`, and pattern-matching to manual `!= nil` checks

## Label
Prefer `?.`, `??`, and pattern-matching to manual `!= nil` checks
