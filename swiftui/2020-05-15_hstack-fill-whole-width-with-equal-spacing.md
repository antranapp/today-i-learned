---
title: HStack fill whole width with equal spacing

createdAt: 2020-05-15T10:08:12Z
---

# HStack fill whole width with equal spacing

```swift
struct ContentView: View {
    var data = ["View", "V", "View Long"]

    var body: some View {
    VStack {

        // This will be as small as possible to fit the data
        HStack {
            ForEach(data, id: \.self) { item in
                Text(item)
                    .border(Color.red)
            }
        }

        // The frame modifier allows the view to expand horizontally
        HStack {
            ForEach(data, id: \.self) { item in
                Text(item)
                    .frame(maxWidth: .infinity)
                    .border(Color.red)
            }
        }
    }
    }
}

---

https://stackoverflow.com/questions/58887526/swiftui-hstack-fill-whole-width-with-equal-spacing