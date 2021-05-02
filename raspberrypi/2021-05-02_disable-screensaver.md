---
title: Disable screensaver
createdAt: 2021-05-02T09:19:08Z
---

# Disable screensaver

- Open lightdm using your prefer text editor, eg using default editor(nano).:

```shell
sudo nano /etc/lightdm/lightdm.conf
```

- Add this line

```shell
xserver-command=X -s 0 -p 0 -dpms
```

---
Source: https://stackoverflow.com/a/51631102/452115