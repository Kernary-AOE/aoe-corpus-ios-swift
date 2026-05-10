# GuardLetEarlyReturn [rule] v0.1.0
When the rest of a function does not make sense without a particular optional being non-nil, write `guard let x = optionalX else { return ... }`. The bound name is in scope for the entire remainder of the function, and the failure case sits at the top where it is easy to read. Use `if let` only when both branches do real work; do not use `if let` to bind a precondition and then put the entire function body inside the `if`.
domain: ios-swift

## Checks
- [ ] Functions with multiple optional preconditions chain `guard let` statements at the top, each handling its own failure case.
- [ ] The `else` branch of every `guard` exits the current scope (`return`, `throw`, `break`, `continue`, `fatalError` for compile-time-impossible cases).
- [ ] Pyramid-of-doom `if let` { `if let` { `if let` ... } } is rewritten as a flat list of `guard let` statements.
- [ ] When the failure case has nothing useful to log or report, the `else` branch may still log a one-liner so the absence is observable in production.

## Label
Use `guard let` to bind preconditions and exit early; reserve `if let` for branching logic

## Label
Use `guard let` to bind preconditions and exit early; reserve `if let` for branching logic
