---
title: How to show complete List when keyboard is showing up in SwiftUI

createdAt: 2020-05-24T19:00:51Z
---

# How to show complete List when keyboard is showing up in SwiftUI

```swift
struct AdaptsToSoftwareKeyboard: ViewModifier {

    @State var currentHeight: CGFloat = 0.0

    func body(content: Content) -> some View {
        content
            .padding(.bottom, currentHeight)
            .edgesIgnoringSafeArea(currentHeight == 0 ? Edge.Set() : .bottom)
            .onAppear(perform: subscribeToKeyboardEvents)
    }

    private let keyboardWillOpen = NotificationCenter.default
        .publisher(for: UIResponder.keyboardWillShowNotification)
        .map { $0.userInfo![UIResponder.keyboardFrameEndUserInfoKey] as! CGRect }
        .map { $0.height }

    private let keyboardWillHide =  NotificationCenter.default
        .publisher(for: UIResponder.keyboardWillHideNotification)
        .map { _ in CGFloat(0.0) }

    private func subscribeToKeyboardEvents() {
        _ = Publishers.Merge(keyboardWillOpen, keyboardWillHide)
            .subscribe(on: RunLoop.main)
            .assign(to: \.currentHeight, on: self)
    }
}
```

---

https://stackoverflow.com/a/57147043/452115