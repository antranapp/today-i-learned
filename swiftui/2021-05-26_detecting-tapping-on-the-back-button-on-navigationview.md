---
title: Detecting tapping on the back button on NavigationView
createdAt: 2021-05-25T23:32:07Z
---

# Detecting tapping on the back button on NavigationView

The quick solution is to create a custom back button because right now the framework have not this possibility.

```swift
struct DetailView : View {

    @Environment(\.presentationMode) var mode: Binding<PresentationMode>

    var body : some View {
        Text("Detail View")
            .navigationBarBackButtonHidden(true)
            .navigationBarItems(leading: Button(action : {
                self.mode.wrappedValue.dismiss()
            }){
                Image(systemName: "arrow.left")
            })
    }
}
```

---
https://stackoverflow.com/a/61931197/452115