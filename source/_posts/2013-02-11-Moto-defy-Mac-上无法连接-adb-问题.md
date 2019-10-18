---
title: "Moto defy Mac 上无法连接 adb 问题"
date: 2013-02-11 00:00:00
categories:
- 代码
tags:
- android
---

还在用一代神机 defy，虽然已经老的不行，价格从入手时的 2k 掉到现在 150软妹币，用来调试程序还是可以的。
速度至少比模拟器快不少吧。另外就是老态龙钟的 defy 还有幸刷上了第三方提供的 android 4.4 rom。

defy 通过 usb 插上电脑后，在终端中输入

```
adb devices
```

发现社设备列表没有出现defy。
查了下问题，找到了解决方法。
在终端中输入

```
system_profiler SPUSBDataType
```

查看系统所有 usb 设备信息。
找到手机的Vender ID，记录下来。
打开用户目录下的.android/adb_usb.ini文件，把上面的 Vender ID 输进去，保存之。
重启下 adb 服务，重新插拔下 usb。

```
adb kill-server
adb start-server
```

再执行

```
adb devices
```

时就可以看到设备了。

reference:

http://blog.csdn.net/duanyipeng/article/details/8836040

Brought to you by PressCoders.com!
