---
title: Rounded Borders in SwiftUI
createdAt: 2021-05-24T22:11:44Z
---

# Rounded Borders in SwiftUI

```
 extension View {
     public func addBorder<S>(_ content: S, width: CGFloat = 1, cornerRadius: CGFloat) -> some View where S : ShapeStyle {
         let roundedRect = RoundedRectangle(cornerRadius: cornerRadius)
         return clipShape(roundedRect)
              .overlay(roundedRect.strokeBorder(content, lineWidth: width))
     }
 }
```
---
https://stackoverflow.com/questions/57753997/rounded-borders-in-swiftui