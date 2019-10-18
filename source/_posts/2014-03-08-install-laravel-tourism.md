---
title: "安装 Laravel 教程"
date: 2014-03-08 00:00:00
categories:
- 代码
tags:
- php
---

## 安装 composer

composer 是一个 非官方的 php 包管理工具， Mac 下安装很方便：


```
brew tap josegonzalez/homebrew-php
brew install josegonzalez/php/composer
```

如果这里报错提示：

```
composer: Missing PHP53, PHP54 or PHP55 from homebrew-php. Please install one of them before continuing
Error: An unsatisfied requirement failed this build.
```

可以先执行下面的方法进行修复：

```
brew search bison27
brew install homebrew/versions/bison27

brew install php54-intl
```

## 安装 Laravel

### 通过 Laravel 安装

首先，下载 [Laravel installer PHAR archive](http://laravel.com/laravel.phar), 为了方便，重命名成 **laravel** 放进 **/usr/local/bin**。
之后，就可以使用命令 **laravel new** 在任何目录下安装 laravel 了
