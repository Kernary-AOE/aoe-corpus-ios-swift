# WeakSelfInEscapingClosures [rule] v0.1.0
Strong captures inside an `@escaping` closure that the receiver itself stores — completion blocks, Combine subscribers, NotificationCenter observers, async tasks held on a controller, timer handlers — create a retain cycle. The receiver retains the closure, the closure retains the receiver, neither deinits. The fix is `[weak self]` in the capture list, paired with a `guard let self else { return }` (or optional-chained `self?.`) inside the body.
domain: ios-swift
