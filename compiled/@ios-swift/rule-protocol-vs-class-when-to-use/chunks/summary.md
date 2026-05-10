# ProtocolVsClassWhenToUse [rule] v0.1.0
When defining a new type, ask what is being modelled. (1) A *capability* shared across unrelated concrete types → `protocol`. (2) A *value* without identity (a coordinate, a measurement, a record) → `struct` or `enum`. (3) A *thing with identity* — a network connection, a file handle, a long-lived UI controller, a node in a shared mutable graph — → `class` (or `actor` if it carries state across concurrent contexts). The default in Swift is value-with-protocol; classes are the exception that buys reference semantics.
domain: ios-swift
