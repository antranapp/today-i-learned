---
title: Auto start a script at boot
createdAt: 2021-05-02T10:01:34Z
---

# Autostart a script at boot

- Create a `.desktop` file at `/home/pi/.config/autostart`

```
[Desktop Entry]
Encoding=UTF-8
Name=PyServer
Exec=lxterminal -e "sudo python /home/pi/pyserver.py"
Icon=lxterminal
Type=Application
Categories=Utility;
```

---
Source: https://www.raspberrypi.org/forums/viewtopic.php?f=66&t=162947&hilit=terminal