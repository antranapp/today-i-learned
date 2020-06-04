---
title: Push View programmatically in callback, SwiftUI

createdAt: 2020-05-28T08:16:17Z
---

# Push View programmatically in callback, SwiftUI

1) Create state `@State var pushActive = false`

2) When ViewModel notifies that login is successful set pushActive to true

```swift
func handleSuccessfullLogin() {
    self.pushActive = true
    print("handleSuccessfullLogin")
}
```

3) Create hidden NavigationLink and bind to that state

```swift
NavigationLink(destination: ProfileView(viewModel: ProfileViewModelImpl()), isActive: self.pushActive) {
    Text("")
}.hidden()
```

---

https://stackoverflow.com/questions/57315409/push-view-programmatically-in-callback-swiftui