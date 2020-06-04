---
title: How to sleep for few milliseconds in swift?
createdAt: 2020-05-22T15:01:47Z
---

# How to sleep for few milliseconds in swift?

`usleep()` takes millionths of a second

```swift
usleep(1000000) //will sleep for 1 second
usleep(2000) //will sleep for .002 seconds
```

OR

```swift
let ms = 1000
usleep(useconds_t(2 * ms)) //will sleep for 2 milliseconds (.002 seconds)
```

OR

```swift
let second: Double = 1000000
usleep(useconds_t(0.002 * second)) //will sleep for 2 milliseconds (.002 seconds)
```

---

https://stackoverflow.com/questions/38119742/how-to-sleep-for-few-milliseconds-in-swift-2-2