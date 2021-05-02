---
title: Using wildcard with scp command
createdAt: 2021-05-02T09:07:21Z
---

# Using wildcard with scp command

Need to escape the `*` character

```shell
scp pi@raspberrypi.local:/home/pi/\*.mp4 . 
```

---
Source: https://unix.stackexchange.com/a/587710/8823