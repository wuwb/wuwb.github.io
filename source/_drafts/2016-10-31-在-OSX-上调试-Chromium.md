---
title: 在 OSX 上调试 Chromium
date: 2016-10-31 13:19:19
tags:
- chromium
categories:
---

### 关闭崩溃报告

当二进制程序奔溃时，Mac OS X 会试着向硬盘中写入奔溃报告。这种情况在执行 Chromium 的单元测试的时候也会发生。因为 Chromium 的执行文件非常大，会导致系统不停地写入错误报告，并占用非常高的 CPU。所以在开发调试 Chromium 之前可以将错误报告功能先关闭掉。执行 ```man ReportCrash``` 命令可以了解当前版本的系统如何关闭错误报告。在 10.8 系统里，关闭命令如下：
```
launchctl unload -w /System/Library/LaunchAgents/com.apple.ReportCrash.plist
sudo launchctl unload -w /System/Library/LaunchDaemons/com.apple.ReportCrash.Root.plist
```
需要分别在普通用户和管理员用户下执行上面的命令。
