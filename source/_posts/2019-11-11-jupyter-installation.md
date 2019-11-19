---
title: jupyter 安装
date: 2019-11-11 18:43:34
tags:
---

## 首先安装 miniconda

```bash
brew cask install miniconda
```

查看安装说明

```bash
brew cask info miniconda
```

文档里告诉我们要执行下面的命令进行 shell 的配置

```sh
conda init "$(basename "${SHELL}")"
```

<!--more-->

设置清华大学镜像源

```
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
conda config --set show_channel_urls yes
```

查看源修改是否生效

```
conda info
```

如果已经安装 miniconda, 可以执行下面的命令进行升级

```sh
conda update conda
```

## 安装 jupyter

```
conda install jupyter
```

生成 jupyter 默认配置文件

```sh
jupyter notebook --generate-config
```

启动

```
jupyter notebook
```

打开后默认项目路径是执行启动命令所在文件夹，可以通过修改配置文件中 `c.NotebookApp.notebook_dir` 参数修改默认文件夹路径

需要远程访问的话，可以添加 `--ip` 参数设置允许访问的 ip 段。

```
jupyter notebook --ip='0.0.0.0'
```

## 配置 jupyter

安装环境管理插件

```
conda install nb_conda
```

安装 markdown 目录插件

```
conda install -c conda-forge jupyter_contrib_nbextensions
```

`-c` 参数表示自定义安装包搜索频道，下面是 conda -h 帮助菜单中的描述信息

```
  -c CHANNEL, --channel CHANNEL
                        Additional channel to search for packages. These are
                        URLs searched in the order they are given (including
                        file:// for local directories). Then, the defaults or
                        channels from .condarc are searched (unless
                        --override-channels is given). You can use 'defaults'
                        to get the default packages for conda. You can also
                        use any name and the .condarc channel_alias value will
                        be prepended. The default channel_alias is
                        http://conda.anaconda.org/.
```

## 参考

- https://docs.conda.io
- https://zhuanlan.zhihu.com/p/33105153
- https://www.jianshu.com/p/042fd657e2d4
