---
title: Overlapping Navigation Titles In SwiftUI
createdAt: 2021-08-08T22:51:04Z
---

# Overlapping Navigation Titles In SwiftUI

##Fixes

1. Add the `.isDetailLink` modifier to your `NavigationLink` view and pass false. 

2.  Set the navigation display mode explicitly to be .inline in the detail view.  To do this you can use the .`navigationBarTitleDisplayMode` or `.navigationBarTitle(_, displayMode: _ )` modifiers.

---

https://www.dabblingbadger.com/blog/2020/12/11/a-quick-fix-for-overlapping-navigation-titles-in-swiftui