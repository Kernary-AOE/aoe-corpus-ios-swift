# PreferSendable [rule] v0.1.0
Under Swift 6 strict concurrency, any value passed across an `actor` boundary, into a detached task, or stored in `@Sendable` state must conform to `Sendable`. Public APIs benefit from being Sendable-by-default: it lets clients use the type freely from any isolation context. For value types with Sendable stored properties the conformance is automatic; for reference types it requires the type to be immutable, an `actor`, or to enforce its own synchronisation.
domain: ios-swift
