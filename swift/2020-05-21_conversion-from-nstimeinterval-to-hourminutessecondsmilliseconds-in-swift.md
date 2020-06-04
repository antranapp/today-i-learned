---
title: conversion from NSTimeInterval to hour,minutes,seconds,milliseconds in swift

createdAt: 2020-05-21T16:37:02Z
---

# conversion from NSTimeInterval to hour,minutes,seconds,milliseconds in swift

```swift
extension TimeInterval{

func stringFromTimeInterval() -> String {

    let time = NSInteger(self)

    let seconds = time % 60
    let minutes = (time / 60) % 60
    let hours = (time / 3600)

    var formatString = ""
    if hours == 0 {
        if(minutes < 10) {
            formatString = "%2d:%0.2d"
        }else {
            formatString = "%0.2d:%0.2d"
        }
        return String(format: formatString,minutes,seconds)
    }else {
        formatString = "%2d:%0.2d:%0.2d"
        return String(format: formatString,hours,minutes,seconds)
    }
}
}
```

---

https://stackoverflow.com/questions/28872450/conversion-from-nstimeinterval-to-hour-minutes-seconds-milliseconds-in-swift