---
title: "通过 Samba 实现 Win/Mac 访问 Linux"
date: 2014-04-08 00:00:00
categories:
- 代码
tags:
- tools
---

今天看公wiki看到samba，上面的后端开发者还推荐使用samba将测试服务器上开的用户目录映射到本地做开发。

试了试,好像挺不错的。

不过我电脑本地已经配置了开发环境了，所以也没有什么必要。还没试过是否可以直接在samba映射目录里调用shell执行远程命令，如果可以这样的话直接在本地就能更新测试机上的svn，还是十分方便的。

mac下配好权限后，打开 finder，按 commond + k，输入 smb://username@ip 将远程文件映射到本地

http://blog.csdn.net/poechant/article/details/7365290
http://zh.wikipedia.org/wiki/Samba
http://linux.vbird.org/linux_server/0370samba.php
https://www.samba.org/
