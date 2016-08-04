---
title: genymotion-play
date: 2015-03-03 15:57 JST
tags:
---

D & D で flashing 出来なかった時の覚書。

genymotion を立ち上げておく。

READMORE

```
❯ cd /Applications/Genymotion.app/Contents/MacOS/player.app/Contents/MacOS/tools
❯ ./adb push ~/Downloads/Genymotion-ARM-Translation_v1.1.zip /sdcard/Download
❯ ./adb push ~/Downloads/gapps-kk-20140105-signed.zip /sdcard/Download
❯ ./adb shell flash-archive.sh /sdcard/Download/Genymotion-ARM-Translation_v1.1.zip
# reboot player on genymotion
❯ ./adb shell flash-archive.sh /sdcard/Download/gapps-kk-20140105-signed.zip
```
