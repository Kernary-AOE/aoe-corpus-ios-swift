# OmitNeedlessWords [rule] v0.1.0
Every word in a name should carry information at the call site. Words that merely repeat type information already present in the signature are noise: `removeElement(_ element: Element)` is `remove(_ element: Element)`. Words restating the receiver are noise: `string.appendString(...)` is `string.append(...)`. Words restating the return type are noise: `tableView.numberOfSectionsInTableView` is `tableView.numberOfSections`.
domain: ios-swift
