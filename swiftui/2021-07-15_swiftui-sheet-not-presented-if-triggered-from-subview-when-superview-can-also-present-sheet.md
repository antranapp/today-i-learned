---
title: SwiftUI: sheet not presented if triggered from subview when superview can also present sheet
createdAt: 2021-07-14T22:13:18Z
---

# SwiftUI: sheet not presented if triggered from subview when superview can also present sheet

Move root view sheet out of NavigationView (tested with Xcode 12.1 / iOS 14.1)

```swift
var body: some View {
    NavigationView {
        VStack {
            Subview()
        }
        .navigationBarTitle("Account", displayMode: .inline)
        .navigationBarItems(leading: aboutButton, trailing: settingsButton)
    }
    .sheet(isPresented: $isSheetPresented) {   // << here !!
        self.activeSheet.sheet
    }
}
```

---
https://stackoverflow.com/a/64703921/452115