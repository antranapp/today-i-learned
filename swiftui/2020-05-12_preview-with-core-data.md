---
title: Preview with Core Data
createdAt: 2020-05-12T21:22:50Z
---

# Preview with Core Data

```swift
struct ContentView_Previews: PreviewProvider {
    static var previews: some View {
        let context = (UIApplication.shared.delegate as! AppDelegate).persistentContainer.viewContext
        
        let task1 = Task(context: context)
        task1.title = "NewTask"
        
        return HomeView().environment(\.managedObjectContext, context)
    }
}
```

https://stackoverflow.com/questions/57700304/previewing-contentview-with-coredata

https://stackoverflow.com/questions/57777915/swiftui-preview-canvas-and-core-data