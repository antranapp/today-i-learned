---
title: How to create NSImage from NSColor
createdAt: 2023-05-20T08:21:03Z
---

# How to create NSImage from NSColor

If you're using AppKit, here's a Swift 5 convenience initializer version of the other answers. Sadly, this doesn't work in UIKit 😞

```
extension NSImage {
    convenience init(color: NSColor, size: NSSize) {
        self.init(size: size)
        lockFocus()
        color.drawSwatch(in: NSRect(origin: .zero, size: size))
        unlockFocus()
    }
}
```

Usage example:

```
let redSwatchImage = NSImage(color: .red, size: NSSize(width: 128, height: 128))
```

-----

https://stackoverflow.com/a/40748898/452115