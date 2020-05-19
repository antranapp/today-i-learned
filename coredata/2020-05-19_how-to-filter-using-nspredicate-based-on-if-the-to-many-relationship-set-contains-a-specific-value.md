---
title: How to filter using NSPredicate based on if the to many relationship set contains a specific value

createdAt: 2020-05-19T21:14:40Z
---

# How to filter using NSPredicate based on if the to many relationship set contains a specific value

"ANY" can be used with a to-many relationship to find the objects for which at least one of the related objects satisfies a condition. In your case:

```swift
NSPredicate(format: "ANY messages.sent == %@", "success")
```

---

https://stackoverflow.com/questions/40976180/how-to-filter-using-nspredicate-based-on-if-the-to-many-relationship-set-contain