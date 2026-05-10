# NameByRoleNotType [rule] v0.1.0
A name should describe what a value *is for*, not what its concrete type happens to be. `var greeting: String = "Hello"` is better than `var string: String = "Hello"`; `protocol View { associatedtype Content }` is better than `associatedtype T`. The type system already says the type; the name carries the role.
domain: ios-swift

## Checks
- [ ] Variables and parameters use role nouns (`destination`, `recipients`, `subject`, `body`), not type echoes (`url`, `array`, `dict`, `string`).
- [ ] Associated types in protocols use descriptive role names (`Element`, `Iterator`, `Index`, `Failure`) — single capital letters appear only when the role really is 'any type' (e.g. `Optional<Wrapped>` uses `Wrapped`, not `T`).
- [ ] Generic parameters on functions name their role when there is one (`func sort<C: Collection>(_ collection: C)`); use a single letter only for true universals.
- [ ] Protocol names describing capability end in `-able`/`-ible` (`Equatable`, `Comparable`); names describing what something *is* read as nouns (`Collection`, `Sequence`).

## Label
Name variables, parameters, and associated types by role, not by type
