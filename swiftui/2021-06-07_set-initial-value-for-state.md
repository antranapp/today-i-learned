---
title: Set initial value for State
createdAt: 2021-06-07T00:57:15Z
---

# Set initial value for State

You can set the value of your @State var in your init like this:

```swift
init(_ yourState:String) {
    _myState = State(initialValue: yourState)
}
```

---
https://www.hackingwithswift.com/forums/swiftui/why-no-setting-of-intial-state/2021