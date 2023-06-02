---
title: How to prepare QuickTime recorder for App Store Review?
createdAt: 2023-06-02T16:17:00Z
---

# How to prepare QuickTime recorder for App Store Review?

```shell
# Crop video to 1920x1080. Cut off the bottom part
ffmpeg -i SimRecorder_demo4_1080.mov  -vf "crop=iw:1080:0:0" SimRecorder_demo4_1080_output.mov

# Create a silent audio track
ffmpeg -f lavfi -i anullsrc=r=44100:cl=stereo -t <duration> silent_audio.mp3

# Add the silent audio track to the video
ffmpeg -i SimRecorder_demo4_1080_output.mov -i silent_audio.mp3 -c:v copy -map 0 -map 1 -shortest SimRecorder_demo4_1080_with_audio_output.mov
```

```shell
# Crop image to the correct side for App Store upload
convert SimRecorder_screenshot2.png -gravity northwest -crop 2880x1800+0+0 SimRecorder_screenshot2_appstore.png
```