---
title: How to disable git gpg signing?
createdAt: 2023-03-12T07:15:44Z
---

# How to disable git gpg signing?

You can disable this by running `git config commit.gpgsign false`. This sets the configuration locally instead of globally.

Putting this setting in .gitconfig worked for me with what you had, without the [user] configuration:

```
[commit]
    gpgsign = false
```

-----

https://stackoverflow.com/questions/39274739/how-to-disable-git-gpg-signing