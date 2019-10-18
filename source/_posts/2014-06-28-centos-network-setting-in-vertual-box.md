---
title: "centos 配置"
date: 2014-06-28 17：05；00
categories:
- 代码
tags:
- tools
---

要配一个 vagrant box 给同事用。

### 下面是配置过程

1. 在 centos 官网下了 minimal 的版本。

2. 在 virtual 中安装，一切顺利。

3. 安装好后没有网络，启用网络

修改文件```/etc/sysconfig/network-scripts/ifcfg-eth0:```

```
ONBOOT="yes"
NM_CONTROLLED="no"
```

重启后就有网络了。

4. 下一步切换 yum 源

mv /etc/yum.repos.d/CentOS-Base.repo /etc/yum.repos.d/CentOS-Base.repo.backup

minimal 版本没有 wget，所以用 curl

curl -o http://mirrors.163.com/.help/CentOS6-Base-163.repo /etc/yum.repos.d/CentOS6-Base-163.repo

5. 生成 yum 源缓存：
yum makecache

### 参考链接
http://mirrors.163.com/.help/centos.html
