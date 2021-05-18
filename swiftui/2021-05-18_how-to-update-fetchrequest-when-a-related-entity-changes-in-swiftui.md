---
title: How to update @FetchRequest, when a related Entity changes in SwiftUI?
createdAt: 2021-05-18T01:20:54Z
---

# How to update @FetchRequest, when a related Entity changes in SwiftUI?

You have to wrap the row in a separate view and use @ObservedObject in that row view on the entity.

Here's my code:

WineList:

```swift
struct WineList: View {
    @FetchRequest(entity: Wine.entity(), sortDescriptors: [
        NSSortDescriptor(keyPath: \Wine.name, ascending: true)
        ]
    ) var wines: FetchedResults<Wine>

    var body: some View {
        List(wines, id: \.id) { wine in
            NavigationLink(destination: WineDetail(wine: wine)) {
                WineRow(wine: wine)
            }
        }
        .navigationBarTitle("Wines")
    }
}
```

WineRow:

```swift
struct WineRow: View {
    @ObservedObject var wine: Wine   // !! @ObserveObject is the key!!!

    var body: some View {
        HStack {
            Text(wine.name ?? "")
            Spacer()
        }
    }
}
```

---
https://stackoverflow.com/a/63524550/452115