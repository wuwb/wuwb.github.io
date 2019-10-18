---
title: "-ms-interpolation-mode 属性介绍"
date: 2015-07-18 23:32:14
categories:
- 代码
tags:
- css
---
-ms-interpolation-mode: bicubic;

IE中的图片如果缩小显示效果会很差。
```
<img class="img" src="pic_500x500.jpg" width="50" height="50">
```
但是使用下面的样式后，可以使IE7支持自定义双三次“重采样模式”，显示效果会有明显的提升。

``` css
.img {
  -ms-interpolation-mode: bicubic;
}
```

-ms-interpolation-mode还有另外一个属性值：nearest-neighbor。它使用的是最近邻近插值算法，会产生比较明显的锯齿，图片模糊。

与其它浏览器比较，opera中图像边缘略显粗糙。总体来说，主流浏览器中缩略图片质量还不错。
遗憾的是IE6不支持这些属性对缩略图片作平滑处理。

留意一下一些大站的代码，发现阿里巴巴首页上图片都加了这个属性。
