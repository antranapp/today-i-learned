---
title: How to ake HDMI hot-pluggable on PI?
createdAt: 2021-05-09T08:15:14Z
---

# How to ake HDMI hot-pluggable on PI?

In `/boot/config.txt`:

```
hdmi_force_hotplug=1
hdmi_group=1
hdmi_mode=16
```

Those are explained here: https://www.raspberrypi.org/documentation/configuration/config-txt/video.md

There is also this: https://www.raspberrypi.org/documentation/configuration/hdmi-config.md -- But if the group 1, mode 16 as above works, you don't have to worry about all that.

---
https://raspberrypi.stackexchange.com/questions/107044/how-do-you-make-the-hdmi-hot-pluggable-on-a-pi