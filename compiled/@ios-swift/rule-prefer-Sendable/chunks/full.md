# PreferSendable [rule] v0.1.0
Under Swift 6 strict concurrency, any value passed across an `actor` boundary, into a detached task, or stored in `@Sendable` state must conform to `Sendable`. Public APIs benefit from being Sendable-by-default: it lets clients use the type freely from any isolation context. For value types with Sendable stored properties the conformance is automatic; for reference types it requires the type to be immutable, an `actor`, or to enforce its own synchronisation.
domain: ios-swift

## Checks
- [ ] Public structs / enums / tuples with Sendable stored properties declare `: Sendable` (or are inferred Sendable in Swift 6 frozen modes).
- [ ] Public final classes that hold only let-properties of Sendable types declare `: Sendable`.
- [ ] Reference types that mutate internal state across threads use `actor` rather than `class + lock` whenever possible.
- [ ] Where a class cannot be made Sendable, the API documents the isolation requirement and any escape hatch (`@unchecked Sendable` paired with a comment justifying the synchronisation discipline).
- [ ] Closures stored or escaped across actor boundaries are typed `@Sendable`.

## Label
Public types crossing concurrency boundaries are Sendable; document why anything is not

## Label
Public types crossing concurrency boundaries are Sendable; document why anything is not
