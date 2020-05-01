---
title: Launching a command-line command from a macOS app
createdAt: 2020-05-01T11:23:48Z
---

# Launching a command line command from a macOS app

```swift
func shell(_ args: String...) -> Int32 {
    let process = Process()
    process.launchPath = "/bin/bash"
    process.arguments = ["-c"]
    process.arguments = process.arguments! + args
    var environment =  ProcessInfo.processInfo.environment
    environment["PATH"] = "$PATH:/usr/local/bin"
    process.environment = environment

    process.launch()
    process.waitUntilExit()
    return process.terminationStatus
}
```