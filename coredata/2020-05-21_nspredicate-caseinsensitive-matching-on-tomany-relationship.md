---
title: NSPredicate case-insensitive matching on to-many relationship

createdAt: 2020-05-21T20:48:40Z
---

# NSPredicate case-insensitive matching on to-many relationship

```objectivec
[NSPredicate predicateWithFormat:@"keywords.name CONTAINS[cd] %@", self.searchString];
```

String comparisons are by default case and diacritic sensitive. You can modify an operator using the key characters c and d within square braces to specify case and diacritic insensitivity respectively

https://developer.apple.com/library/content/documentation/Cocoa/Conceptual/Predicates/Articles/pSyntax.html

---

https://stackoverflow.com/a/1594822/452115