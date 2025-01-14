---
title: "VPC 中云服务器之间网络不通"
keyword: QingCloud, 青云, 云计算, VPC, VPC 网络, 网络
description: 如何排查 VPC 中云服务器之间网络不通的问题。
draft: false
weight: 5
---



**1.确认源和目的地址、源和目的实例ID**

获取源ECS实例和目的ECS的实例ID、IP地址，以便后续步骤使用。


**2.检查安全策略相关配置**

检查安全策略相关配置分为同vxnet和跨vxnet场景，以下是具体内容：

    同私有网络：需要检查：
        ECS互通的前提是在同一组内互信的安全组下，如未开启组内互信，需要在安全组下放通彼此的IP地址。
    跨私有网络：需要检查：
        ECS互通的前提是在同一组内互信的安全组下，如未开启组内互信，需要安全组下放通彼此的IP地址。
        若使用网络ACL，网络ACL的出入方向需要放通彼此的网段或IP地址。


**3.检查VPC层面路由相关配置**

检查VPC层面路由相关配置分为同VPC场景和跨VPC场景，以下是具体内容：

    同VPC场景：一般情况下，不存在路由问题，可以忽视该场景的隐患。
    跨VPC场景：分为隧道互通和边界路由器互通场景。
        隧道互通场景下需要关注是否配置了感兴趣流，及隧道规则是否匹配。
        边界路由器互通场景下需要排查是否正确的添加了内网路由策略或者路由表指向正确的下一跳。

**4.检查ECS内部配置**

    不同操作系统进行以下排查操作：
        Linux系统中排查ECS内部是否有iptables的drop相关策略。
        Windows系统中排查是否允许的ICMP回显功能。
    排查系统内是否配置了三方VPN软件、安全软件，吸走流量或者对ICMP存在限制。
    排查是否有自建Docker等，在系统内将远端的路由引流到容器内。



    

