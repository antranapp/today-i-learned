---
title: How to open a video in Quick Time programatically on macOS?
createdAt: 2022-12-29T07:57:13Z
---

# How to open a video in Quick Time programatically on macOS?

```swift
let stringUrl = "/Users/whoever/Desktop/myrec.mov"
let url = URL(fileURLWithPath: stringUrl)

let config = NSWorkspace.OpenConfiguration()
config.activates = true

NSWorkspace.shared.open(
    [url],
    withApplicationAt: URL(fileURLWithPath: "/System/Applications/QuickTime Player.app"),
    configuration: config
)
```

-----
https://stackoverflow.com/a/65874325/452115