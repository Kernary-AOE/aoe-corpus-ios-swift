# ClarityAtCallSite [principle] v0.1.0
The thesis of the Swift API Design Guidelines: APIs are read more often than they are written, and Swift's type system, default-argument support, and argument-label syntax exist specifically to let you make every call site self-documenting. Optimise for the reader of the use site — not for the brevity of the declaration, not for symmetry with Objective-C, not for what feels easy to type.
> Clarity at the point of use is your most important goal. Code is read far more often than it is written. Strive to make the call site of every API a grammatical English phrase that documents its own intent. When clarity and brevity conflict, choose clarity. When fluency at the use site requires a longer name or an extra label, the name and the label are correct.
domain: ios-swift

## Applies To
- Naming methods, properties, parameters, types, and modules — every named thing the user of the API will read.
- Choosing argument labels and default values: the call site is the test, not the declaration.
- Deciding between method, free function, and computed property — the question is which form reads best at use, not which is shortest to write.
- Documentation: when the call site is clear, the doc comment becomes a short summary, not a substitute for the name.
