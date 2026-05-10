# PreferMethodOverFreeFunction [rule] v0.1.0
Free functions are reserved for cases with no obvious `self`: when the operation has no candidate primary owner, when it is a generic utility over multiple unrelated types, or when it forms part of a domain notation (e.g. `min(x, y)`, `sin(angle)`). Otherwise the operation belongs as a method on the most relevant type, or as a computed property when it is a value-with-no-arguments-and-no-side-effects.
domain: ios-swift
