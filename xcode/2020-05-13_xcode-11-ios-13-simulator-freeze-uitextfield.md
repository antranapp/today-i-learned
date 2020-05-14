---
title: Xcode 11 iOS 13 simulator freeze UITextField

createdAt: 2020-05-13T16:27:33Z
---

# Xcode 11 iOS 13 simulator freeze UITextField

This problem still exists on Xcode 11.1 The solution is:

```
"Simulator -> Edit -> Automatically Sync Pasteboard" canel selected.
"Hardware -> Restart"
```

https://forums.developer.apple.com/thread/122972