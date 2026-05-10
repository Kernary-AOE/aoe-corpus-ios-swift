# PreferMethodOverFreeFunction [rule] v0.1.0
Free functions are reserved for cases with no obvious `self`: when the operation has no candidate primary owner, when it is a generic utility over multiple unrelated types, or when it forms part of a domain notation (e.g. `min(x, y)`, `sin(angle)`). Otherwise the operation belongs as a method on the most relevant type, or as a computed property when it is a value-with-no-arguments-and-no-side-effects.
domain: ios-swift

## Checks
- [ ] New top-level functions are justified — free function only when there is no natural `self`, or for cross-type utilities, or for domain notation.
- [ ] Operations that primarily act on one type are added as methods (or extensions) on that type, not as `doThing(to:)`-shaped global functions.
- [ ] Side-effect-free, argument-free, O(1) computations expose as computed properties (`array.count`, not `array.count()`).
- [ ] Domain notation utilities (`abs`, `min`, `max`, trig functions) remain free functions for readability.

## Label
Prefer methods and properties to free functions

## Label
Prefer methods and properties to free functions
