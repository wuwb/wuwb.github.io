---
title: ps aux命令显示的状态列中的Ss+，Rsl，R+，S<sl 的意思
categories: 其他
categoriesAlias: others
date: 2016-10-28 10:28:33
timestamp: 2016-10-28 10:28:33
updated:
tags:
---

```
ps aux | grep phantomjs

mapp 27466  5.0 0.0 2188340 37596 ? Sl 10:26 0:00 /usr/local/bin/phantomjs /home/mapp/mogu-spider/src/spider/H5spider.js http://i.mogujie.com/dapei/16n51o
mapp 27896 27.5 0.0 2187268 36180 ? Sl 10:26 0:00 /usr/local/bin/phantomjs /home/mapp/mogu-spider/src/spider/H5spider.js http://i.mogujie.com/1109x2
mapp 27899 26.0 0.0 2187268 37712 ? Sl 10:26 0:00 /usr/local/bin/phantomjs /home/mapp/mogu-spider/src/spider/H5spider.js http://i.mogujie.com/detail/18haeae
mapp 27937 44.0 0.0 2034388 33456 ? Sl 10:26 0:00 /usr/local/bin/phantomjs /home/mapp/mogu-spider/src/spider/H5spider.js http://i.mogujie.com/dapei/1si2k
mapp 27940 33.0 0.0 2032320 29912 ? Sl 10:26 0:00 /usr/local/bin/phantomjs /home/mapp/mogu-spider/src/spider/PCspider.js http://ai.mogujie.com/13fosi
```

<!--more-->

```shell
D    不可中断     Uninterruptible sleep (usually IO)
R    正在运行，或在队列中的进程
S    处于休眠状态
T    停止或被追踪
Z    僵尸进程
W    进入内存交换（从内核2.6开始无效）
X    死掉的进程

<    高优先级
N    低优先级
L    有些页被锁进内存
s    包含子进程
+    位于后台的进程组；
l    多线程，克隆线程  multi-threaded (using CLONE_THREAD, like NPTL pthreads do)
```
