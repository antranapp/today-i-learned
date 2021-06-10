---
title: How do you clip an image to a square inside a lazy grid? (SwiftUI)
createdAt: 2021-06-02T01:36:21Z
---

# How do you clip an image to a square inside a lazy grid? (SwiftUI)

Some were asking about the image appearing off center. You can adjust that by adding in the line .position(x: gr.frame(in: .local).midX, y: gr.frame(in: .local).midY). So the full thing would be:

Number of Columns

```swift
// Somewhere in my view struct
private let threeColumnGrid = [
    GridItem(.flexible(minimum: 40)),
    GridItem(.flexible(minimum: 40)),
    GridItem(.flexible(minimum: 40)),
]
```

Creating the Grid

```swift
LazyVGrid(columns: threeColumnGrid, alignment: .center) {
    ForEach(model.imageNames, id: \.self) { item in
        GeometryReader { gr in
            Image(item)
                .resizable()
                .scaledToFill()
                .frame(height: gr.size.width)
                .position(x: gr.frame(in: .local).midX, y: gr.frame(in: .local).midY)
        }
        .clipped()
        .aspectRatio(1, contentMode: .fit)
    }
}
```
---

https://stackoverflow.com/questions/62791912/how-do-you-clip-an-image-to-a-square-inside-a-lazy-grid-swiftui