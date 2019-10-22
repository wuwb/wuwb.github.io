---
title: mac 安装 minikube 方法
date: 2019-10-22 13:25:19
tags:
---

## 需求

- macOS 10.12(Sierra)
- 安装有 Hyperkit, Parallels, VirtualBox 或 VMware Fusion 虚拟层

## 安装

有两种安装方法，一个通过 brew 安装，也是推荐的方式，一个是通过脚本直接安装。

<!--more-->

用 brew 安装

{% codeblock %}
brew cask install minikube
{% endcodeblock %}

{% codeblock %}
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-darwin-amd64 \
  && sudo install minikube-darwin-amd64 /usr/local/bin/minikube
{% endcodeblock %}

## 升级

通过 brew 安装的升级比较简单，执行下列命令即可

{% codeblock %}
rm /usr/local/bin/minikube
brew cask reinstall minikube
{% endcodeblock %}

通过脚本安装的话，应该重新执行下脚本就可以（猜测）。

## 虚拟层配置

mac 下推荐使用 Hyperkit, 比较简单

### 需要

- macOS 10.11+
- HyperKit

### Hyperkit 安装

- 如果电脑已经装了 Docker for Desktop，那就已经有 Hyperkit 了。
- 没有的话可以通过 brew 安装

{% codeblock %}
brew install hyperkit
{% endcodeblock %}

- 另外也可以通过 [github 源码安装](https://github.com/moby/hyperkit)

### 使用方法

使用 hyperkit 驱动启动 cluster

{% codeblock %}
minikube start --vm-driver=hyperkit
{% endcodeblock %}

将 hyperkit 设置为默认驱动

{% codeblock %}
minikube config set vm-driver hyperkit
{% endcodeblock %}

## 了解 Kubernetes

启动后，可以通过常规的 Kubernetes 命令来和 minikube cluster 进行交互。比如，可以通过下列命令来查看 pod 的状态。

{% codeblock %}
kubectl get po -A
{% endcodeblock %}

## 增加分配的内存

minikube 默认值分配 2GB 内存，只够普通的部署，如果需要更大规模的部署，可以通过 `--memory` 标签增加分配的内存。或者通过下列命令将内存分配参数存起来持久化。

{% codeblock %}
minikube config set memory 4096
{% endcodeblock %}

### 参考

- https://github.com/kubernetes/minikube
- https://minikube.sigs.k8s.io/docs/start/macos/
