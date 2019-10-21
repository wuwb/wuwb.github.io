---
title: contos 安装 python 3.3
categories: 其他
categoriesAlias: others


author: Wenbin
date: 2016-03-29 10:10:37
timestamp: 2016-03-29 10:10:37
updated:
tags:
keywords:
description:
---

查看当前系统中的python版本

```shell
python --version
```

安装所有的开发工具包
```shell
yum groupinstall "Development tools"
```shell
yum install zlib-devel bzip2-devel openssl-devel ncurses-devel
```
下载、编译和安装Python
在官网下载python 3.3版本源码：

```shell
wget http://www.python.org/ftp/python/3.3.0/Python-3.3.0.tar.bz2
tar -jxv -f Python-3.3.0.tar.bz2
cd Python-3.3.0
./configure
make install
```
