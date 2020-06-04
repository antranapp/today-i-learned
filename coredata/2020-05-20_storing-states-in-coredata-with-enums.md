---
title: Storing states in CoreData with enums

createdAt: 2020-05-20T11:16:55Z
---

# Storing states in CoreData with enums

```swift

enum ObjStatus: Int16 {
    case State1 = 0
    case State2 = 1
    case State3 = 3
}

class StateFullManagedObject: NSManagedObject {
    @NSManaged var state: Int16
    var stateEnum:ObjStatus {                    //  ↓ If self.state is invalid.
        get { return ObjStatus(rawValue: self.state) ?? .State1 }
        set { self.state = newValue.rawValue }
    }
}
```

---

https://stackoverflow.com/questions/26900302/swift-storing-states-in-coredata-with-enums