# LabelArgumentsByGrammar [rule] v0.1.0
Argument labels exist to make the call site readable. The decision rule: read the call as English. (1) When the argument is the direct object of a verb method, omit the label: `removeAll()`, `view.add(subview)`. (2) When the first argument is a prepositional complement, fold the preposition into the base name: `move(to: x)`, `dictionary.removeValue(forKey: k)`. (3) When the first argument is part of a noun phrase that names what is constructed, label it: `Color(red:green:blue:)`, `Vector(x:y:z:)`. (4) Trailing arguments always get labels.
domain: ios-swift

## Checks
- [ ] Mutating verb methods on a receiver: first arg is the direct object, no label — `array.append(element)`, `set.insert(item)`.
- [ ] Prepositional first arguments: preposition is part of the base name, no label — `index(of: x)`, `move(to: point)`, not `index(_:)` with `of` as a label.
- [ ] Initialisers and factory methods that construct from parts: first arg labelled by its noun role — `URL(string: s)`, `Date(timeIntervalSince1970: t)`.
- [ ] Arguments after the first always have labels unless they are part of a single noun phrase running across them.
- [ ] Boolean trailing arguments always have labels (`animated: true`, not bare `true`).

## Label
Choose argument labels so the call site reads as a grammatical English phrase

## Label
Choose argument labels so the call site reads as a grammatical English phrase
