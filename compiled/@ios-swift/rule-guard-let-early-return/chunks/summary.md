# GuardLetEarlyReturn [rule] v0.1.0
When the rest of a function does not make sense without a particular optional being non-nil, write `guard let x = optionalX else { return ... }`. The bound name is in scope for the entire remainder of the function, and the failure case sits at the top where it is easy to read. Use `if let` only when both branches do real work; do not use `if let` to bind a precondition and then put the entire function body inside the `if`.
domain: ios-swift
