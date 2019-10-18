---
title: "更新 requests 包之后报 has no attribute '__getitem__' 的错"
date: 2014-03-13 00:00:00
updateed:
categories:
- 代码
tags:
- python
- request
---

翻代码的时候看到段一年多前用 python 写的下载图片站图片的代码。

测试下看还能不能下到图片，结果发现跑不起来了，报了个如下的错误：

TypeError: 'instancemethod' object has no attribute '__getitem__'
谷歌一下发现是 requests 包升级后不兼容老版本造成的

解决方法是安装 requests-transition 这个包，

```
pip install requests-transition
```

然后如果你原来的代码中使用的是 requests 0.x 版本的话，将

```
import requests
```

改成

```
import requests0 as requests
```

如果原来的包是 1.0 版的，改成

```
import requests1 as requests
```

参考：

How to make an orderly transition to Python Requests 1.0 instead of running around in a panic
