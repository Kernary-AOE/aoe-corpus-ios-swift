# NeverForceUnwrapPublicly [anti-pattern] v0.1.0
Reaching for `!` on an `Optional` whose value originates from input — a network response, user input, an `Info.plist` lookup, a `URL(string:)`, a forced cast (`as!`), an IBOutlet that happens to be wired most of the time — turns every nil into an immediate runtime crash. The same applies to `try!`: if the throwing call can fail under any input the user might supply, it must not be force-tried.
domain: ios-swift
