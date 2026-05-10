# NeverForceUnwrapPublicly [anti-pattern] v0.1.0
Reaching for `!` on an `Optional` whose value originates from input — a network response, user input, an `Info.plist` lookup, a `URL(string:)`, a forced cast (`as!`), an IBOutlet that happens to be wired most of the time — turns every nil into an immediate runtime crash. The same applies to `try!`: if the throwing call can fail under any input the user might supply, it must not be force-tried.
domain: ios-swift

## Label
Force-unwrapping (`!`) optionals on data that crosses an API or input boundary

## Why Bad
Force-unwrap converts a recoverable absence into a `Swift runtime: Fatal error: Unexpectedly found nil ...` crash that takes the whole process down. On iOS, that is a user-visible app crash. Worse, the crash often points at the unwrap site rather than at where the nil was first introduced, making the bug hard to trace. The compiler's optional system exists specifically so that absence is a value the program can reason about; force-unwrap throws that information away.

## Instead Do
```
    Use `guard let` for early-return on a precondition that must hold for
    the rest of the function to make sense. Use `if let` when the rest of
    the function has both a non-nil and a nil branch. Use optional
    chaining (`a?.b?.c`) when one branch produces a value and the other
    produces nothing. Use the nil-coalescing operator (`x ?? default`)
    when there is a sensible fallback. For `try`, prefer `try?` (drops
    the error to nil) or `do { try ... } catch { ... }` over `try!`.

    Force-unwrap is acceptable only in *compile-time impossible* cases
    inside trusted code: a regex literal that cannot fail to construct, a
    static dictionary lookup with a key known to the source. Even then,
    paired with a comment that names why the optional cannot be nil.
  
```
