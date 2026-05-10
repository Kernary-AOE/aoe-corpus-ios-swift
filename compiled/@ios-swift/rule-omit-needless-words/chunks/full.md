# OmitNeedlessWords [rule] v0.1.0
Every word in a name should carry information at the call site. Words that merely repeat type information already present in the signature are noise: `removeElement(_ element: Element)` is `remove(_ element: Element)`. Words restating the receiver are noise: `string.appendString(...)` is `string.append(...)`. Words restating the return type are noise: `tableView.numberOfSectionsInTableView` is `tableView.numberOfSections`.
domain: ios-swift

## Checks
- [ ] Read each word of the API name and ask: does removing this word make the call site less clear? If no, remove it.
- [ ] Method names do not repeat the type of an argument that already has its type spelled out (`add(observer:)`, not `addObserver(observer:)`).
- [ ] Method names do not repeat the receiver type (`Color.darker()`, not `Color.colorByMakingDarker()`).
- [ ] Property names do not repeat the type (`isFavorite: Bool`, not `favoriteFlag: Bool`; `name: String`, not `nameString: String`).

## Label
Omit words that the type system already makes obvious

## Label
Omit words that the type system already makes obvious
