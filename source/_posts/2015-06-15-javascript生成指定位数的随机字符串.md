---
title: javascript生成指定位数的随机字符串
date: 2015-06-15 10:53:08
categories:
- 代码
tags:
- javascript
---

先是一个比较low的方法，效率也比较低

```javascript
/**
 * 返回指定位数的随机字符串
 */
var getRndString = function(len) {
  var s = [];
  var a = parseInt(Math.random() * 25) + (Math.random() > 0.5 ? 65 : 97);
  for (var i = 0; i < len; i++) {
    s[i] = Math.random() > 0.5 ? parseInt(Math.random() * 9) : String.fromCharCode(parseInt(Math.random() * 25) + (Math.random() > 0.5 ? 65 : 97));
  }
  return s.join("");
}
```

下面是好看一点的

```javascript
/**
 * 返回指定位数的随机字符串
 */
var getRndString = function (length) {
    var arr = 'abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789';
    var arrLen = arr.length;
    var s = '';
    for (var i = 0; i < length; i++) {
        s += arr.charAt((Math.random() * arrLen));
    }
    return s;
}
```

性能测试地址
[http://jsperf.com/getrndstring](http://jsperf.com/getrndstring)
