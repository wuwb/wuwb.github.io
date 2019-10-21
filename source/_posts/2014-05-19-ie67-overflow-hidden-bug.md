---
title: "ie67 overflow hidden 不起效果的bug"
date: 2014-05-19 18:28:00
categories:
- 代码
tags:
- css
---

中午一个前些天写的页面联调好了，做了下兼容性测试准备上线，结果发现 ie6、7下

```css
overflow: hidden;
```

不起效果。

这其实很常见的 bug 啊，因为 overflow 元素的子元素有用到绝对定位的鼠标 hover 蒙版效果，有 poa, 自然会有 por 的子元素, 而这 bug 就是 por 引起的，再深入的原因也没了解过，但是解决方法也很简单，给 ovh 元素添加 por 或者 去掉子元素的 por 就行。所以这里我果断给 ovh 元素添加了 por.

再来测一次

...

结果还是有问题。

...

纠结了许久后，问了下同事，然后被告知 ovh 没加 width...

好吧， ie 太不智能，宽高什么都不能自适应，记录下，以免下次又忘了。
