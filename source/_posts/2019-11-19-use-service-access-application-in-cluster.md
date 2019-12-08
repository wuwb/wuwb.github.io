---
title: 使用服务对象访问集群中的应用
date: 2019-11-19 13:12:24
category: 运维
tags:
---

这篇文章介绍怎么通过服务对象访问集群中的应用。service 给集群中的应用的两个实例提供了负载均衡的功能。

## 文章目标

- 运行 Hello World 应用的两个实例
- 创建服务对象暴露节点端口
- 使用服务对象访问应用

## 开始之前

开始之前需要有一个 `Kubernetes` 集群，和 `kubectl` 命令指向你要操作的集群。如果你还没集群，可以参考前面一篇文章安装 `Minikube`, 创建本地测试集群。或者可以使用下面这些在线的测试环境。

 - [katacoda](https://www.katacoda.com/courses/kubernetes/playground)
 - [Play with Kubernetes](http://labs.play-with-k8s.com/)

<!--more-->

## 为运行在两个 pod 里的应用创建服务

下面是一个用来创建应用发布的配置文件。

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: hello-world
spec:
  selector:
    matchLabels:
      run: load-balancer-example
  replicas: 2
  template:
    metadata:
      labels:
        run: load-balancer-example
    spec:
      containers:
        - name: hello-world
          image: gcr.io/google-samples/node-hello:1.0
          ports:
            - containerPort: 8080
              protocol: TCP
```

通过下面的命令在你的集群中创建应用，如果懒得本地创建这个配置文件，可以直接使用线上连接。

```
kubectl apply -f ./path/to/your/file/hello-application.yaml
kubectl apply -f https://k8s.io/examples/service/access/hello-application.yaml
```

上述的命令，创建了一个发布对象，和一个关联的副本集对象。副本集对象用用两个 pod，每个 pod 中运行着一个 hello world 应用实例。

### 查看一下创建的发布对象

```
kubectl get deployments hello-world
kubectl describe deployments hello-world
```

### 查看一下创建的副本集对象

```
kubectl get replicasets
kubectl describe replicasets
```

### 创建暴露发布的服务对象

```
kubectl expose deployment hello-world --type=NodePort --name=example-service
```

### 查看一下创建的服务对象

```
kubectl describe services example-service
```

输出如下：

```
Name:                   example-service
Namespace:              default
Labels:                 run=load-balancer-example
Annotations:            <none>
Selector:               run=load-balancer-example
Type:                   NodePort
IP:                     10.32.0.16
Port:                   <unset> 8080/TCP
TargetPort:             8080/TCP
NodePort:               <unset> 31496/TCP
Endpoints:              10.200.1.4:8080,10.200.2.5:8080
Session Affinity:       None
Events:                 <none>
```

记录一下输出中的 NodePort 端口号

### 查看一下运行着 hello world 应用 pod

```
kubectl get pods --selector="run=load-balancer-example" --output=wide
```

### 获取公共 ip 地址

这个获取方式和你使用的集群有关，如果是 minikube 集群，可以使用

```
kubectl cluster-info
```

命令获取。如果是 Google Compute Engine, 可以使用

```
gcloud compute instances list
```

### 创建防火墙规则，允许到公共 ip 的 tcp 请求

### 使用公共 ip 和 NodePort 端口访问应用

```
curl http://<public-node-ip>:<node-port>
```

看到结果

```
Hello Kubernetes!
```

## 使用配置文件

上面描述了如果通过命令 `kubectl expose` 创建服务对象。我们还可以通过配置文件创建服务对象。

[见下一篇文章](https://kubernetes.io/docs/concepts/services-networking/service/)

## 清理测试环境

删除服务对象

```
kubectl delete services example-service
```

删除发布对象，副本集对象和运行着应用的 pods

```
kubectl delete deployment hello-world
```

## 参考

- https://kubernetes.io/docs/tasks/access-application-cluster/service-access-application-cluster/
