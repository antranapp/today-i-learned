---
title: How to bring a running application window to front most?
createdAt: 2022-12-18T08:28:30Z
---

# How to bring a running application window to front most?

Solution from [StackOverFlow](https://stackoverflow.com/questions/2114283/setting-the-front-most-window-using-accessibility-api) [^1]

```swift
let currentPid = NSRunningApplication.currentApplication().processIdentifier
if let pid = (the pid of the app in question) where pid != currentPid {
  NSRunningApplication(processIdentifier: pid)?.activateWithOptions(.ActivateIgnoringOtherApps)
}
```

---

[^1]: https://stackoverflow.com/questions/2114283/setting-the-front-most-window-using-accessibility-api