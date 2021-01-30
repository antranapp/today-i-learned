---
title: Use SwiftUI preview inside Swift Package
createdAt: 2021-01-30T08:08:12Z
---

# Use SwiftUI preview inside Swift Package

I found out that making the product library "dynamic" (instead of static) made my previews work from inside the package's targets.

```
let package = Package(
    name: "Modules",
    platforms: [
        .iOS(.v13)
    ],
    products: [
        .library(
            name: "Modules",
            type: .dynamic,
            targets: ["App"]
        ),
    ],
    dependencies: [],
    targets: [
        .target(
            name: "App",
            dependencies: []
        ),
        .testTarget(
            name: "AppTests",
            dependencies: ["App"]
        ),
    ]
)
```

https://stackoverflow.com/questions/62826612/xcode-cannot-generate-swift-ui-preview-build-aborted-due-to-an-internal-error