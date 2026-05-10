# ErrorThrowsNotResultWherePossible [rule] v0.1.0
Swift has two error-handling shapes: throwing functions (`func f() throws -> T`, `func f() async throws -> T`) and `Result<Success, Failure>`. The throwing form is the language-level mechanism — it integrates with `try`/`catch`, with `async`/`await`, and with typed-throws (Swift 6). Use it for any function whose call site immediately handles or propagates the error. Reserve `Result` for cases where the error must be *stored* alongside the value: callback bridges that cannot be made `async`, completion handlers from older APIs, or stream events that emit successes and failures over time.
domain: ios-swift

## Checks
- [ ] New functions that can fail are declared `throws` (or `async throws`), not `-> Result<T, E>`.
- [ ] Errors thrown are typed: a meaningful enum (`enum NetworkError: Error { ... }`) per failure mode, not `NSError` or `String`-shaped errors.
- [ ] When wrapping a callback API at a module boundary, convert it to `async throws` via `withCheckedThrowingContinuation` rather than exposing `Result` outwards.
- [ ] `Result` is used only when the error must be carried as a value: stored in a property, sent through a publisher, paired with a completion handler that predates `async`.

## Label
Use `throws` for synchronous and async failure; reserve `Result` for stored values and bridges
