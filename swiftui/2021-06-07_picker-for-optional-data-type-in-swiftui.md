---
title: Picker for optional data type in SwiftUI?
createdAt: 2021-06-07T01:04:46Z
---

# Picker for optional data type in SwiftUI?

```swift
struct FruitView: View {

    @State private var fruit: Fruit?

    var body: some View {
        Picker(selection: $fruit, label: Text("Fruit")) {
            ForEach(Fruit.allCases) { fruit in
                Text(fruit.rawValue).tag(fruit as Fruit?)
            }
        }
    }
}
```

---
https://stackoverflow.com/a/59348094/452115