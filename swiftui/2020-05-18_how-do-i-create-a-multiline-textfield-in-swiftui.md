---
title: How do I create a multiline TextField in SwiftUI?

createdAt: 2020-05-18T11:09:59Z
---

# How do I create a multiline TextField in SwiftUI?

https://github.com/kenmueller/TextView

```swift
import SwiftUI
import TextView

struct ContentView: View {
    @State var input = ""
    @State var isEditing = false

    var body: some View {
        VStack {
            Button(action: {
                self.isEditing.toggle()
            }) {
                Text("\(isEditing ? "Stop" : "Start") editing")
            }
            TextView(text: $input, isEditing: $isEditing)
        }
    }
}
```

---

https://stackoverflow.com/questions/56471973/how-do-i-create-a-multiline-textfield-in-swiftui