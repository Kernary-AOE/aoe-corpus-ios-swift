# NameByRoleNotType [rule] v0.1.0
A name should describe what a value *is for*, not what its concrete type happens to be. `var greeting: String = "Hello"` is better than `var string: String = "Hello"`; `protocol View { associatedtype Content }` is better than `associatedtype T`. The type system already says the type; the name carries the role.
domain: ios-swift
