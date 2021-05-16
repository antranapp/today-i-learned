---
title: Do not mix RPi.GPIO and gpiozero
createdAt: 2021-05-16T08:15:27Z
---

# Do not mix RPi.GPIO and gpiozero

NOTE that gpiozero, by default uses RPi.GPIO

> GPIO Zero builds on a number of underlying pin libraries, including RPi.GPIO and pigpio, each with their own benefits. You can select a particular pin library to be used, either for the whole script or per-device, according to your needs. See the section on changing the pin factory.

NOTE GPIO.cleanup() is superfluous as gpiozero automatically cleans up on exit.

---
https://raspberrypi.stackexchange.com/questions/109235/please-set-pin-numbering-mode-using-gpio-setmodegpio-board-or-gpio-setmodegpi