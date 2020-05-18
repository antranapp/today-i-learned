---
title: disable iOS simulator 'connect hardware keyboard' programmatically

createdAt: 2020-05-18T10:59:00Z
---

# disable iOS simulator 'connect hardware keyboard' programmatically

```shell
killall Simulator
defaults write com.apple.iphonesimulator ConnectHardwareKeyboard -bool false
```

---

https://stackoverflow.com/questions/55845373/disable-ios-simulator-connect-hardware-keyboard-programmatically