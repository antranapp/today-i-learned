---
title: Hide Seperator in List
createdAt: 2020-05-12T20:50:09Z
---

# Hide Seperator in List

```swift
List {
    ForEach(self.tasks) { task in
        Button(action: {
            guard let index = self.tasks.firstIndex(of: task) else { return }
            self.toggleTask(at: index)
        }) {
            TaskView(task: task)
        }
        
    }
    .onDelete { indexSet in
        guard let index = indexSet.first else { return }
        self.deleteTask(at: index)
    }
}
.onAppear {
    // To remove only extra separators below the list:
    UITableView.appearance().tableFooterView = UIView()

    // To remove all separators including the actual ones:
    UITableView.appearance().separatorStyle = .none
}
.onDisappear {
    UITableView.appearance().separatorStyle = .singleLine
}
```

https://stackoverflow.com/questions/56553672/how-to-remove-the-line-separators-from-a-list-in-swiftui-without-using-foreach