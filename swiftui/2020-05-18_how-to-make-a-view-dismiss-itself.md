---
title: How to make a view dismiss itself

createdAt: 2020-05-18T06:44:39Z
---

# How to make a view dismiss itself

```swift
.sheet(isPresented: $showingNewUserView) {
    NewUserView(isPresented: self.$showingNewUserView)
}
```

Using this approach, SwiftUI will cause those two views to read and write the same Boolean value, which means when `NewUserView` sets the Boolean back to false it will hide the sheet automatically.

---

https://www.hackingwithswift.com/quick-start/swiftui/how-to-make-a-view-dismiss-itself