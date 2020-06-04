---
title: Set a given Publishers Failure type to Never in Combine

createdAt: 2020-06-04T12:54:41Z
---

# Set a given Publishers Failure type to Never in Combine


```swift
let publisher: AnyPublisher<AnyType, SomeError> = //...

publisher.catch { error in
  // handle the error here. The `catch` operator requires to
  // return a "fallback value" as a publisher
  return Just(/* ... */) // as an example
}
```

---

https://stackoverflow.com/questions/58227096/set-a-given-publishers-failure-type-to-never-in-combine