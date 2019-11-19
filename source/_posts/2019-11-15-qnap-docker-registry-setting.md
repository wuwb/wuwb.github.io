---
title: '威联通使用: docker registry 设置'
date: 2019-11-15 10:06:27
tags:
---

威联通 Container Station 里的 Registry 设置不生效，不知道做这么个界面的意义是什么。

只能试试 ssh 连上 nas，看看通过文件配置。

连上 nas 后，执行 `which docker` 命令，查看 docker 的安装路径

```sh
which docker
/share/CACHEDEV1_DATA/.qpkg/container-station/bin/docker
```

<!--more-->

进到 `/share/CACHEDEV1_DATA/.qpkg/container-station` 目录，看到有 `etc` 子目录。

进 `etc` 子目录，看到 docker.json, 这应该就是 docker 配置文件了，在里面加上我们的加速源。

```json
{
  "registry-mirrors": ["https://docker.mirrors.ustc.edu.cn"]
}
```

再回到 `container-station` 目录，执行目录下的 `./container-station.sh restart` 命令对服务进行重启。

重启后源设置就生效了，愉快的玩耍吧。

## 更新

nas 重启后配置失效
