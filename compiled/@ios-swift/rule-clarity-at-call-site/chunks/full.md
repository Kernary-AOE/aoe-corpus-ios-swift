# ClarityAtCallSite [rule] v0.1.0
Code is read far more often than it is written. Every naming and signature decision — argument labels, method vs. free function, default values, presence or absence of a verb — must be evaluated by reading a sample call out loud and asking whether it reads like English documenting its own intent. Brevity in the declaration is not the goal; clarity at the use site is.
domain: ios-swift

## Checks
- [ ] Read three real call sites of the API aloud — they form grammatical English phrases describing what the call does.
- [ ] Argument labels appear unless their omission produces a more fluent phrase (see prefer-label-args-by-grammar).
- [ ] Names that read fluently at the call site are kept even when the declaration looks slightly longer.
- [ ] Documentation comments echo the same phrasing the call site already produces — no surprises.

## Label
Optimise every name and signature for the reader of the call site

## Label
Optimise every name and signature for the reader of the call site
