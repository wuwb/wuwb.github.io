---
title: "angular Duplicates in a repeater are not allowed 错误"
date: 2014-05-20 17：05；00
categories:
- 代码
tags:
- javascript
- mean
- angular
---
最近在做一个使用 MEAN.io 开发的项目，用到 angular, mongodb, express 之类比较有意思的框架类库，只是自己这些东西都不是很熟，使用中遇到了很多问题，也只能慢慢看文档。

中午遇到个的错误

```
Angular ng-repeat Error “Duplicates in a repeater are not allowed.”
```

解决办法是在 ng-repeat 后加上 track by $index

具体原因看 stackoverflow 上高手的回答：

> I wanted to mention that you can apply any custom tracking property to define uniqueness, not just $index. Since in this scenario the objects don't have any other properties this works fine. The reason this error happens is that angular is using a dictionary to store the id of an item as the key with the value as the DOM reference. From the code (line 15402 in angular.js) it looks like they are caching previously found DOM elements based on their key as a performance optimization. Since they need unique keys they explicitly throw this error when they find duplicate keys on line 15417

好几万行源码看下来还是很有压力的，先把项目做出来，有时间再去了解下源码。

[angular-ng-repeat-error-duplicates-in-a-repeater-are-not-allowed](http://stackoverflow.com/questions/16296670/angular-ng-repeat-error-duplicates-in-a-repeater-are-not-allowed)
