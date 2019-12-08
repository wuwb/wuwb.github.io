---
title: minikube 介绍
date: 2019-11-19 12:20:05
category: 运维
tags:
- minikube
- kubectl
- docker
---

minikube 是一个用来在个人电脑的虚拟机上运行单节点 Kubernetes 集群的工具。

## 安装前准备

### 一

先要确认电脑是否支持 minikube 需要的虚拟机化技术。mac 电脑的话执行

```sh
sysctl -a | grep -E --color 'machdep.cpu.features|VMX'
```

如果返回值中包含高亮的 `VMX` 值，说明系统是支持的。

<!--more-->

### 二

要确认电脑上已经安装 `kubectl`, 这个工具安装 docker for desktop 后就有了。

### 三

安装一个虚拟层管理工具。可以是下面三个之一。

- HyperKit
- VirtualBox
- VMware Fusion

HyperKit 在安装 docker for desktop 后就有了。

## 安装

安装很简单，brew 安装就好了。

```sh
brew install minikube
```

## 清理本地环境

如果原来安装过 minikube， 执行

```
minikube start
```

命令的时候可能会报错,

```
machine does not exist
```

这种情况下，执行

```
minikube delete
```

清理环境后重新执行 `minikube start` 启动集群。

## 参考

- https://kubernetes.io/docs/tasks/tools/install-minikube/
