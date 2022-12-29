---
title: How to get app icon from window processID on macOS?
createdAt: 2022-12-29T01:57:47Z
---

# How to get app icon from window processID on macOS?

```swift
let runningApp = NSRunningApplication(processIdentifier: pid_t(the_process_id))
let icon = runningApp?.icon
```

-----
https://stackoverflow.com/questions/3329742/get-app-icon-from-window-id-in-cocoa