---
title: why fastlane working directory different than what I set
createdAt: 2021-05-21T00:16:51Z
---

# why fastlane working directory different than what I set

> ...every action and every plugin's code runs in the root of the project, while all user code from the Fastfile runs inside the ./fastlane directory. This is important to consider when migrating existing code from your Fastfile into your own action or plugin. To change the directory manually you can use standard Ruby blocks:
>
>```
>Dir.chdir("..") do
>    # code here runs in the parent directory
>end
>```
>
> This behavior isn't great, and has been like this since the very early days of fastlane. As much as we'd like to change it, there is no good way to do so, without breaking thousands of production setups, so we decided to keep it as is for now.

---
https://stackoverflow.com/a/48086544/452115