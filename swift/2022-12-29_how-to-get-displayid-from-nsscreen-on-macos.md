---
title: How to get displayID from NSScreen on macOS?
createdAt: 2022-12-29T04:15:28Z
---

# How to get displayID from NSScreen on macOS?

```swift
extension NSScreen {
    var displayID: CGDirectDisplayID? {
        return deviceDescription[NSDeviceDescriptionKey(rawValue: "NSScreenNumber")] as? CGDirectDisplayID
    }
}
```

-----
https://gist.github.com/briankc/025415e25900750f402235dbf1b74e42