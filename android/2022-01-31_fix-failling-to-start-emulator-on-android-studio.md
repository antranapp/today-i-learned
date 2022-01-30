---
title: Fix failling to start emulator on Android Studio
createdAt: 2022-01-30T22:47:40Z
---

# Fix failling to start emulator on Android Studio

## Run emulator from a separated window

go to Android Studio -> Preferences -> Tools -> Emulator -> Uncheck “Launch in a tool window”.

## Kill emulator

Solution 1:
May be adb kill-server helps for you?

or

adb -s emulator-5554 emu kill, where emulator-5544 - emulator name.

Solution 2:
To stop all running emulators we use this command:


adb devices | grep emulator | cut -f1 | while read line; do adb -s $line emu kill; done
Solution 3:
FOR MAC:
Run:
```
ps -ax | grep emulator 
```
which gives you a wider result something like:

```shell
 6617 ??         9:05.54 /Users/nav/Library/Android/sdk/emulator/qemu/darwin-x86_64/qemu-system-x86_64 -netdelay none -netspeed full -avd Nexus_One_API_29
 6619 ??         0:06.10 /Users/nav/Library/Android/sdk/emulator/emulator64-crash-service -pipe com.google.AndroidEmulator.CrashService.6617 -ppid 6617 -data-dir /tmp/android-nav/
 6658 ??         0:07.93 /Users/nav/Library/Android/sdk/emulator/lib64/qt/libexec/QtWebEngineProcess --type=renderer --disable-accelerated-video-decode --disable-gpu-memory-buffer-video-frames --disable-pepper-3d-image-chromium --enable-threaded-compositing --file-url-path-alias=/gen=/Users/nav/Library/Android/sdk/emulator/lib64/qt/libexec/gen --enable-features=AllowContentInitiatedDataUrlNavigations --disable-features=MacV2Sandbox,MojoVideoCapture,SurfaceSynchronization,UseVideoCaptureApiForDevToolsSnapshots --disable-gpu-compositing --service-pipe-token=15570406721898250245 --lang=en-US --webengine-schemes=qrc:sLV --num-raster-threads=4 --enable-main-frame-before-activation --service-request-channel-token=15570406721898250245 --renderer-client-id=2
 6659 ??         0:01.11 /Users/nav/Library/Android/sdk/emulator/lib64/qt/libexec/QtWebEngineProcess --type=renderer --disable-accelerated-video-decode --disable-gpu-memory-buffer-video-frames --disable-pepper-3d-image-chromium --enable-threaded-compositing --file-url-path-alias=/gen=/Users/nav/Library/Android/sdk/emulator/lib64/qt/libexec/gen --enable-features=AllowContentInitiatedDataUrlNavigations --disable-features=MacV2Sandbox,MojoVideoCapture,SurfaceSynchronization,UseVideoCaptureApiForDevToolsSnapshots --disable-gpu-compositing --service-pipe-token=--lang=en-US --webengine-schemes=qrc:sLV --num-raster-threads=4 --enable-main-frame-before-activation --service-request-channel-token=  --renderer-client-id=3
10030 ttys000    0:00.00 grep emulator
```

The first (left) column is the process ID (PID) that you are looking for.

Find the first PID (in the above example, it's 6617).

Force kill that process:

```
kill -9 PID
```

In my case, the command is:

```
kill -9 6617
```

---

- https://stackoverflow.com/a/70891877/452115
- https://stackify.dev/732720-android-stop-emulator-from-command-line