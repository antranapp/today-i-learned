---
title: Binding value from an ObservableObject

createdAt: 2020-05-13T10:20:40Z
---

# Binding value from an ObservableObject

Binding variables can be created in the following ways:

1. @State variable's projected value provides a Binding<Value>
2. @ObservedObject variable's projected value provides a wrapper from which you can get the Binding<Subject> for all of it's properties
3. Point 2 applies to @EnvironmentObject as well.
4. You can create a Binding variable by passing closures for getter and setter as shown below:
```swift
let button = SaleButton(isOn: .init(get: { car.isReadyForSale },
                                    set: { car.isReadyForSale = $0} ))
```

**Note:**
- As @nayem has pointed out you need @State / @Observed / @EnvironmentObject in the view for SwiftUI to detect changes automatically.
- Projected values can be accessed conveniently by using $ prefix.

https://stackoverflow.com/questions/59259921/binding-value-from-an-observableobject