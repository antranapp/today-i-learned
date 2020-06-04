---
title: Fixed: Multiple sheet(isPresented:) doesn't work in SwiftUI

createdAt: 2020-05-28T11:05:21Z
---

# Fixed: Multiple sheet(isPresented:) doesn't work in SwiftUI

Can also add the sheet to an EmptyView placed in the view's background. This can be done multiple times:

```swift
.background(EmptyView()
    .sheet(isPresented: isPresented, content: content))
```

---

https://stackoverflow.com/questions/58837007/multiple-sheetispresented-doesnt-work-in-swiftui