---
title: How to add local Swift Package as dependency?

createdAt: 2020-05-12T17:21:04Z
---

# How to add local Swift Package as dependency?

The root directory of your package repo should look like this, more or less:

```
Package.swift
Sources/
Tests/
SampleProject/
```

Then perform the following steps:

- Use the Xcode GUI to add your package to the sample project. You'll need to use the actual HTTPS URL to the repo origin. Specify a branch name to a branch you're comfortable working from regularly, e.g. a "develop" branch or something.
- Open the sample project's project.pbxproj file in a text editor.
- Find the XCRemoteSwiftPackageReference section.
- Edit the repositoryURL value so the line reads: repositoryURL = "../";

https://forums.swift.org/t/how-to-add-local-swift-package-as-dependency/26457/24