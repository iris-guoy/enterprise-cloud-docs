---
title: "升级集群"
description: 介绍如何升级集群版本
draft: false
enableToc: false
weight: 30
keyword: 青云, QingCloud, 云计算, 升级 QKE
---

您可以在控制台上一键升级 QKE 集群版本，从而体验更丰富的功能。

## 升级说明

- 目前不支持 `v1.0.x` 到 `v3.0.x` 的跨版本更新，需要先升级到 `v2.0.x` 再升级到 `v3.0.x`。
- 升级一般需要 12 小时，请耐心等待。

## 注意事项

- 由于升级过程需要消耗较多的磁盘 IO 以及 CPU，**生产环境请在业务低谷期操作，升级过程中请避免部署新工作负载或者变更配置等操作**。
- 客户端节点所有数据以及 Kubernetes 节点 /data 目录以外的数据会在重启后重置，如果有此类自定义的数据请先备份后再升级。
- `QKE v1.0.0` 基于 `Ubuntu 16.04` 操作系统，在升级完成后，可能会在 KubeSphere 页面上遇到 CPU 使用率显示不正确的情况，这是由操作系统内核原因造成，需要在升级后根据业务情况关闭集群然后再开启集群来解决（此操作会把操作系统替换成 `Ubuntu 18.04`）。

## 前提条件


- 升级前请确保所有 Kubernetes 节点（包括主节点和工作节点）的 /data 数据盘至少有 50G 的可用空间。

- 请确保客户端节点处于开机运行状态。

## 操作步骤

1. 登录 QingCloud 管理控制台。

2. 在控制台顶部的导航菜单中，选择**产品与服务** > **容器服务** > **容器引擎 QKE**，进入 QKE 集群列表页面。

3. 在集群列表，右键单击目标集群，选择**升级**。

   <img src="../../../_images/upgrade.png" alt="升级集群"/>

4. 选择需要升级的目标版本，下方对应显示版本特性。

5. 点击**升级**，弹出提示信息框。

6. 确认无误后，点击**确认**。

   开始升级，集群节点状态变为**更新中**，等待所有节点状态变为**活跃**，则升级成功。

