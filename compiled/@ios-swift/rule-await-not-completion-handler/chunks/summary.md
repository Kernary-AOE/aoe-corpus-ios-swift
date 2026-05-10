# AwaitNotCompletionHandler [rule] v0.1.0
New async APIs are written as `func f(...) async throws -> T`. The call site reads as straight-line code, errors propagate through `try`, cancellation propagates through the cooperative cancellation system, and the structured-concurrency model (`Task`, `TaskGroup`, `async let`) composes naturally. Completion-handler APIs (`(Result<T, E>) -> Void` callbacks) are reserved for two cases: (1) wrapping platform APIs that have not yet adopted `async`, and (2) interop with Objective-C code that calls back via blocks.
domain: ios-swift
