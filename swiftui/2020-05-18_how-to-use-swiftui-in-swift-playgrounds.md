---
title: How to use SwiftUI in Swift Playgrounds

createdAt: 2020-05-18T18:15:23Z
---

# How to use SwiftUI in Swift Playgrounds

```swift
import SwiftUI
import PlaygroundSupport

struct ContentView: View {
    var body: some View {
        Text("Hello World")
    }
}

PlaygroundPage.current.setLiveView(ContentView())
```

---

https://www.hackingwithswift.com/articles/203/how-to-use-swiftui-in-swift-playgrounds