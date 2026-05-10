# ProtocolVsClassWhenToUse [rule] v0.1.0
When defining a new type, ask what is being modelled. (1) A *capability* shared across unrelated concrete types → `protocol`. (2) A *value* without identity (a coordinate, a measurement, a record) → `struct` or `enum`. (3) A *thing with identity* — a network connection, a file handle, a long-lived UI controller, a node in a shared mutable graph — → `class` (or `actor` if it carries state across concurrent contexts). The default in Swift is value-with-protocol; classes are the exception that buys reference semantics.
domain: ios-swift

## Checks
- [ ] New types start as `struct` unless an explicit reason for reference semantics applies.
- [ ] Shared behaviour across unrelated concrete types is expressed via protocol, with default implementations in a protocol extension where useful — not via a class hierarchy.
- [ ] Inheritance for code reuse is treated as a smell; protocol composition is preferred (`Identifiable & Hashable & Sendable`).
- [ ] `final` is applied to classes that are not designed for subclassing — which is most classes.
- [ ] When state must be shared safely across concurrency boundaries, `actor` is preferred to a class plus locks.

## Label
Reach for protocols + value types first; reach for classes only when reference identity is the point

## Label
Reach for protocols + value types first; reach for classes only when reference identity is the point
