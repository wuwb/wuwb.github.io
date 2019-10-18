---
title: "oh-my-zsh-中bundler插件和bower插件冲突"
date: 2014-04-23 00:00:00
categories:
- 代码
tags:
- tools
---

今天使用 MEAN 新建了一个项目，使用 bower 安装依赖的时候的报了一个莫名其妙的错误：

```
Can't 'bundle install' outside a bundled project
```

记得 bundle 好像是 ruby 安装依赖的工具，和 bower 有什么关系啊，
Google 了一下，发现是 oh my zsh 里的插件冲突了。

### 解决方法有好几种：


1. 比如去除 oh my zsh 配置文件中的 bower 插件或者 bundle 插件。

2. 重命名缩写 bi 的值 ```alias bi=bundle_install```


>I stumbled upon this and I think it is because of a name clash within bundler and bower plugins. I have the bundler and bower plugins enabled in my config. Since the bundler plugin specifies a bi function and the bower plugin specifies an alias bi=bower install, there is a clash. Renaming bundle's bi function to bundle_install fixed the issue for me ...


### 参考

[oh-my-zsh/issues/2486](https://github.com/robbyrussell/oh-my-zsh/issues/2486)
