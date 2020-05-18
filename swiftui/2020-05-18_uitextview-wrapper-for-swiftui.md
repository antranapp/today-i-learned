---
title: UITextView wrapper for SwiftUI
createdAt: 2020-05-18T07:33:27Z
---

# UITextView wrapper for SwiftUI

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
            TextView(
                text: $input,
                isEditing: $isEditing,
                placeholder: "Enter text here"
            )
        }
    }
}
```

---

https://github.com/kenmueller/TextView