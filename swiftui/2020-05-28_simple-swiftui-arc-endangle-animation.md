---
title: Simple SwiftUI Arc endAngle animation
createdAt: 2020-05-27T22:42:59Z
---

# Simple SwiftUI Arc endAngle animation

```swift
struct Arc: Shape {
    var center: CGPoint
    var radius: CGFloat
    var endAngle: Double

    var animatableData: CGFloat {     // << here !!
        get { CGFloat(endAngle) }
        set { endAngle = Double(newValue) }
    }

    func path(in rect: CGRect) -> Path {
        var path = Path()

        path.addArc(center: center, radius: radius, startAngle: .degrees(180), endAngle: .degrees(endAngle), clockwise: false)

        return path
    }
}
```

---

https://stackoverflow.com/questions/61216954/simple-swiftui-arc-endangle-animation-not-working-only-jump-from-one-state-to-a