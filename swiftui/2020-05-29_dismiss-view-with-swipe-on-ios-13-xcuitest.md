---
title: Dismiss view with swipe on iOS 13 XCUITest

createdAt: 2020-05-29T14:55:16Z
---

# Dismiss view with swipe on iOS 13 XCUITest

```swift
var tablesQuery = app.tables.element(boundBy: 0)
let start = tablesQuery.coordinate(withNormalizedOffset:  CGVector(dx: 0.0, dy: 0.0))
let finish = tablesQuery.coordinate(withNormalizedOffset: CGVector(dx: 0.0, dy: 3.0))
start.press(forDuration: 0.5, thenDragTo: finish) 
```

---

https://stackoverflow.com/questions/59463536/dismiss-view-with-swipe-on-ios-13-xcuitest