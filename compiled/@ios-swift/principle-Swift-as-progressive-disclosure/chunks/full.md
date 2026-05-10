# SwiftAsProgressiveDisclosure [principle] v0.1.0
Swift is designed so that the simple form is the default, and complexity is opted into one feature at a time. A user can write `let x = 1` before they know about types; they can write `func f() { ... }` before they know about access control; they can write a `struct` before they need a `protocol`; they can use `try` before they need typed throws; they can call `f()` before they need `await`. Each feature waits until it is actually needed and only then enters the user's code.
> Build APIs and code in the same shape: the common case is a one-liner; the next-most-common case adds one explicit modifier; only the genuinely complex case pulls in the full machinery. Default arguments, opt-in attributes (`@MainActor`, `@Sendable`, `@escaping`), and progressive type erasure (`some P`, `any P`) all exist so that a beginner's first use is short and a power user's specialised use is precise. Do not invert this by making the simple case carry decoration it does not need.
domain: ios-swift

## Applies To
- Default arguments cover the common case; explicit arguments cover variation.
- Generics: start with concrete types or `some P`; introduce explicit generics only when client code needs them.
- Concurrency: synchronous first; `async` when the operation actually suspends; `actor` when state actually crosses isolation boundaries; `@Sendable` when the closure actually escapes one.
- Types: `struct` before `class`; `class` before `actor`; protocol composition before generic constraints before associated types.
- Error handling: non-throwing first; `throws` when failure is real; typed throws when callers must distinguish failure modes.
