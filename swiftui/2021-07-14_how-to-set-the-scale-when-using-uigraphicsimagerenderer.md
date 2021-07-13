---
title: How to set the scale when using UIGraphicsImageRenderer
createdAt: 2021-07-13T23:28:57Z
---

# How to set the scale when using UIGraphicsImageRenderer

You should use the UIGraphicsImageRendererFormat class when creating your UIGraphicsImageRenderer. If you want to write exact pixels rather than scaled points, use something like this:

```swift
let format = UIGraphicsImageRendererFormat()
format.scale = 1

let renderer = UIGraphicsImageRenderer(size: yourImageSize, format: format)
let image = renderer.image { ctx in
    // etc
}
```
---
https://stackoverflow.com/a/38063691/452115