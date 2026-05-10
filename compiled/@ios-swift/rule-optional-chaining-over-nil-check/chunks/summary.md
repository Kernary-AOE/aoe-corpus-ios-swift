# OptionalChainingOverNilCheck [rule] v0.1.0
When the goal is 'do this only if the value is present, otherwise produce nothing or a default', Swift gives three short-circuiting forms that are clearer than an `if x != nil` check followed by a body that uses `x!`. Optional chaining (`a?.b?.c()`) propagates nil. Nil-coalescing (`x ?? default`) supplies a fallback. Pattern matching (`if case let .some(value) = x`) reads the cases explicitly. Each removes a force-unwrap and makes the absence-handling part of the expression.
domain: ios-swift
