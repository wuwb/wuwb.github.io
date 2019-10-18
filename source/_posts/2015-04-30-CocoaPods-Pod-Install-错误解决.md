---
title: CocoaPods Pod Install 错误解决
date: 2015-04-30 09:22:07
categories:
- 代码
tags:
- ios
---

比较喜欢把系统和软件都升级到最新版本。最近看到苹果推送的 xcode 最新版本，于是升级了下。
结果项目都跑不起来了，出了一些比较的错误。

执行 pod install 安装依赖的时候报了好多下面的警告：

``` shell
target overrides the `OTHER_LDFLAGS`...
```


Xcode 升级到 6.0 后，更新 CocoaPods，出现了如下的警告

[!] The `Paopao [Debug]` target overrides the `PODS_ROOT` build setting defined in `Pods/Target Support Files/Pods/Pods.debug.xcconfig'. This can lead to problems with the CocoaPods installation
    - Use the `$(inherited)` flag, or
    - Remove the build settings from the target.

[!] The `Paopao [Debug]` target overrides the `OTHER_LDFLAGS` build setting defined in `Pods/Target Support Files/Pods/Pods.debug.xcconfig'. This can lead to problems with the CocoaPods installation
    - Use the `$(inherited)` flag, or
    - Remove the build settings from the target.

[!] The `Paopao [Release]` target overrides the `PODS_ROOT` build setting defined in `Pods/Target Support Files/Pods/Pods.release.xcconfig'. This can lead to problems with the CocoaPods installation
    - Use the `$(inherited)` flag, or
    - Remove the build settings from the target.

[!] The `Paopao [Release]` target overrides the `OTHER_LDFLAGS` build setting defined in `Pods/Target Support Files/Pods/Pods.release.xcconfig'. This can lead to problems with the CocoaPods installation
    - Use the `$(inherited)` flag, or
    - Remove the build settings from the target.


这种警告是不能忽视的，它带来的直接后果就是无法通过编译。

而产生此警告的原因是项目 Target 中的一些设置，CocoaPods 也做了默认的设置，如果两个设置结果不一致，就会造成问题。

我想要使用 CocoaPods 中的设置，分别在我的项目中定义`PODS_ROOT` 和 `Other Linker Flags`的地方，把他们的值用`$(inherited)`替换掉，进入终端，执行

pod update
 警告没了，回到 Xcode，build通过。

网上还流行另外一种简单粗暴的方法
点击项目文件 project.xcodeproj，右键`显示包内容`，用文本编辑器打开`project.pbxproj`，删除`OTHER_LDFLAGS`的地方，保存，回到 Xcode，编译通过。



参考资料

http://stackoverflow.com/a/18730481
http://www.cnblogs.com/ludashi/p/4046691.html
