---
title: How to instantiate PreviewProvider when View requires @Binding in initializer
createdAt: 2020-05-14T17:39:50Z
---

# How to instantiate PreviewProvider when View requires @Binding in initializer

Using `.constant``

```swift
struct AddProjectView: View {
    @Binding public var showModal: Bool
    var body: some View {
        return VStack {
            Text("Add Project View")
            Button("Dismiss") {
                self.showModal = false
            }
        }
    }
}

struct AddProjectView_Previews: PreviewProvider {
    static var previews: some View {
        AddProjectView(showModal: .constant(true))
    }
}
```

---

https://stackoverflow.com/questions/56685964/swiftui-binding-initialize
https://stackoverflow.com/questions/58701826/swiftui-how-to-instantiate-previewprovider-when-view-requires-binding-in-initia