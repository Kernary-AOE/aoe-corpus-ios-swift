# WeakSelfInEscapingClosures [rule] v0.1.0
Strong captures inside an `@escaping` closure that the receiver itself stores — completion blocks, Combine subscribers, NotificationCenter observers, async tasks held on a controller, timer handlers — create a retain cycle. The receiver retains the closure, the closure retains the receiver, neither deinits. The fix is `[weak self]` in the capture list, paired with a `guard let self else { return }` (or optional-chained `self?.`) inside the body.
domain: ios-swift

## Checks
- [ ] Every `@escaping` closure that is stored on `self` (or on an object that outlives `self`) captures `self` with `[weak self]`.
- [ ] After the capture, the body either uses `self?.x` or unwraps once at the top with `guard let self else { return }`.
- [ ] Timer, NotificationCenter, KVO, and Combine subscriptions stored on a view controller use `[weak self]` in their handler closures.
- [ ] Non-escaping closures (e.g. the closure passed to `array.map`, `forEach`, sync `withLock`) do *not* need `[weak self]` — strong is fine because the closure does not outlive the call.
- [ ] When `[weak self]` would force the closure to do nothing useful if `self` is gone, but the work must still complete, capture `[weak self]` plus a strong copy of the specific dependency the closure actually needs.

## Label
Capture `self` weakly in any escaping closure stored on `self` or owned by a longer-lived object
