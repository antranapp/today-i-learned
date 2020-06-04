---
title: Make a VStack fill the screen in SwiftUI

createdAt: 2020-05-27T08:29:53Z
---

# Make a VStack fill the screen in SwiftUI

```swift
struct ContentView : View {

    var body: some View {
        GeometryReader { geometryProxy in
            VStack(alignment: .leading) {
                Text("Title")
                    .font(.title)
                Text("Content")
                    .font(.body)
            }
            .frame(
                width: geometryProxy.size.width,
                height: geometryProxy.size.height,
                alignment: .topLeading
            )
        }
        .background(Color.red)
    }
}
```

---

https://stackoverflow.com/questions/56487323/make-a-vstack-fill-the-width-of-the-screen-in-swiftui/61444475#61444475