---
title: Workaround about SPM (Swift package manager) deal with Xcode 11.4 and Swift 5.2 with external static libraries. Adding an internal dynamic library to resolve static code duplication error
createdAt: 2020-05-06T19:05:25Z
---

# Workaround about SPM (Swift package manager) deal with Xcode 11.4 and Swift 5.2 with external static libraries. Adding an internal dynamic library to resolve static code duplication error

Since Xcode 11.4 and Swift 5.2 you may experience some trouble regarding SPM and compilation errors due to

- Library code duplication: Swift package product 'your library' is linked as a static library by 'your project' and 'your widget'. This will result in duplication of library code.
- Unable to find a library within your Unit Tests target while using dynamic libraries
- and so on related to SPM libraries

https://github.com/renaudjenny/Swift-Package-Manager-Static-Dynamic-Xcode-Bug