---
title: dispatch_once_t 的作用
date: 2014-12-25 11:56:42
categories:
- 代码
tags:
- ios
---

主要用来构建单例
如果被多个线程调用，该函数会同步等等直至代码块完成。
进程只创建一次并且是线程全的

有一些优势
  - 线程安全
  - 很好满足静态分析器要求
  - 和自动引用计数（ARC）兼容
  - 仅需要少量代码

也有一些劣势
  - 仍然运行创建一个非共享的实例

### reference
- http://blog.csdn.net/marsdoudouluo/article/details/8190650
- http://bj007.blog.51cto.com/1701577/649413
- http://code4app.com/snippets/one/%E8%8B%B9%E6%9E%9C%E5%AE%98%E6%96%B9%E7%9A%84%E5%8D%95%E4%BE%8B%E5%86%99%E6%B3%95/50d134606803fa377e000000
- https://developer.apple.com/library/mac/documentation/Performance/Reference/GCD_libdispatch_Ref/index.html
