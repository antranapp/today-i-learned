---
title: UITests how to test screen edge pan gestures?

createdAt: 2020-05-25T21:20:11Z
---

# UITests how to test screen edge pan gestures?

```swift
let coord1 = app.coordinate(withNormalizedOffset: CGVector(dx: 0.01, dy: 0.15))
let coord2 = app.coordinate(withNormalizedOffset: CGVector(dx: 0.5, dy: 0.15))
coord1.press(forDuration: 0.01, thenDragTo: coord2)
```

---

https://stackoverflow.com/questions/34772202/xcode7-uitests-how-to-test-screen-edge-pan-gestures