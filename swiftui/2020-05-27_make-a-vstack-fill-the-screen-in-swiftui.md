---
title: Make a VStack fill the screen in SwiftUI

createdAt: 2020-05-27T08:29:53Z
---

# Make a VStack fill the screen in SwiftUI

```swift
struct ContentView: View {
    var body: some View {
        HStack() {
            VStack(alignment: .leading) {
                Text("Hello World")
                    .font(.title)
                Text("Another")
                    .font(.body)
                Spacer()
            }
            Spacer()
        }.background(Color.red)
    }
}
```

![Gif](https://i.stack.imgur.com/5Ob2W.gif)

---

https://stackoverflow.com/a/56496498/452115