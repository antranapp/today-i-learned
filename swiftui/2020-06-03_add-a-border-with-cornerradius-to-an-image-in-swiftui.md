---
title: Add a border with cornerRadius to an Image in SwiftUI
createdAt: 2020-06-03T14:23:02Z
---

# Add a border with cornerRadius to an Image in SwiftUI

```swift
Image("profile")
    .cornerRadius(10)
    .overlay(RoundedRectangle(cornerRadius: 10)
        .stroke(Color.orange, lineWidth: 4))
    .shadow(radius: 10)
```

---

https://stackoverflow.com/questions/57269651/add-a-border-with-cornerradius-to-an-image-in-swiftui-xcode-beta-5