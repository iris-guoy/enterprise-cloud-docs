---
title: "业务日志中出现“Connection reset by peer”的错误"
description: 介绍如何处理负载均衡器 Connection reset by peer。
keyword: QingCloud, 青云, 云计算, 网络, 负载均衡器, 报错
draft: false
---

## 问题现象

负载均衡后端配置 TCP 服务端口后，后端业务日志中频繁出现类似如下网络连接异常错误信息。首先可以通过抓包分析这条日志产生是否是负载均衡器的锁发出的请求导致，如果不是则需要检查其他地方配置是否有问题。本主要分析由负载均衡器产生的问题。

![img](../../_images/peer_reset.png)

## 问题原因

该问题和负载均衡的健康检查机制有关。由于 TCP 对上层业务状态无感知，同时，为了降低负载均衡健康检查成本和对后端业务的冲击，负载均衡针对 TCP 协议服务端口的健康检查只会做简单的TCP 三次握手，而后直接发送 RST 包断开 TCP 连接。

简单的来说，四层健康检查，会对后端服务器发起一次请求，后端服务器的服务端口只要应答了负载均衡器则认为此次检查是成功的，就会主动关闭连接，并未进行业务层面上的数据交互，从而导致上层业务（例如 Java 连接池等）认为相应的连接是异常的。

## 解决方法

对于以上情况主要有两种解决方法。

### 1、更换 TCP 协议为 HTTP 协议。

此方案是将健康检查更换七层健康检查，会进行业务层面的数据交互，所以也需要后端服务提供相应的接口去供 LB 进行健康检查。

### 2、在业务层面，对来自 LB 服务器 IP 地址段的相关请求做日志过滤，忽略相关错误信息。

此方案仍旧是基于第四层的健康检查，因为业务日志中出现此报错就已经代表四层健康检查成功了，所这个报错本身就可以忽略。