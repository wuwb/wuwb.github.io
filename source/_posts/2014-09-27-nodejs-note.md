---
title: "nodejs-note"
date: 2014-09-27 15:09:01
categories:
- 代码
tags:
- nodejs
---


https://github.com/koajs/session
Simple cookie-based session middleware

### 用法

``` nodejs
var session = require('koa-sess')

app.use(session({
  cookie: {
    maxAge: 1000 * 60 * 5
  },
  store: redisStorage()
}));
```
