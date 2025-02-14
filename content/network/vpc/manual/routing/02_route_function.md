---
title: "使用路由表"
keyword: QingCloud, 青云, 云计算, VPC, VPC 网络, 路由表
description: 介绍如何管理自定义路由表以及路由规则。
draft: false
weight: 2
---

除默认路由表外，您还可以创建自定义路由表，管理私有网络的路由流量。

## 创建路由表

1. 登录 [QingCloud 管理控制台](https://console.qingcloud.com/login)。

2. 在控制台顶部的菜单栏中，选择**产品与服务** > **网络服务** > **VPC 网络**，进入**VPC 网络**页面。

3. 在页面左侧导航栏中，点击**路由表**。

4. 选择要创建的路由表的区域。

5. 点击**创建**，弹出**创建路由表**页面。

   <img src="../../../_images/504002_create_routetable.png" alt="创建路由表" style="zoom:50%;" />

6. 输入路由表名称，并选择所属 VPC 网络和关联资源类型。

   > **说明**
   >
   > 一个路由表只能关联同一种类型的资源，且创建后不可修改。例如，路由表需要关联私有网络，则**关联资源类型**选择**私有网络**，创建后，该路由表只能关联私有网络，不可关联负载均衡器。

7. 点击**提交**。

## 绑定路由表

您可以将路由表绑定到负载均衡器或私有网络（这取决于该路由表创建时所选择的**关联资源类型**）。

> **说明**
>
> ▪︎ 一个路由表可以绑定多个相同类型的资源，但一个资源只能绑定一个路由表。
>
> ▪︎ 暂不支持批量绑定和解绑。

以下以绑定路由表到私有网络为例进行介绍，绑定路由表到负载均衡器的操作类似。

您可以在 VPC 网络的私有网络管理页面绑定路由表，具体操作请参见[绑定路由表](../../vxnet/30_bind_route/)。您也可以在路由表详情页面进行绑定，操作如下：

1. 登录 [QingCloud 管理控制台](https://console.qingcloud.com/login)。

2. 在控制台顶部的菜单栏中，选择**产品与服务** > **网络服务** > **VPC 网络**，进入**VPC 网络**页面。

3. 在页面左侧导航栏中，点击**路由表**。

4. 点击目标路由表的 ID，进入路由表详情页面。

5. 在**基本属性**区域，点击<img src="../../../_images/function_icon.png" style="zoom:70%;" />图标，选择**绑定私有网络**。

   >**说明**
   >
   >若该路由表的关联资源类型为负载均衡器，则只能选择**绑定负载均衡器**。

   <img src="../../../_images/504002_bind_vxnet.png" style="zoom:50%;" />

6. 在弹出的页面中，选择要绑定的私有网络，点击**提交**。

   绑定成功后，**资源**字段后将显示已绑定的私有网络名称。

   再次点击<img src="../../../_images/function_icon.png" style="zoom:70%;" />图标，可看到**解绑私有网络**选项，点击可进行解绑操作。

## 管理路由表规则

- 当路由表绑定到私有网络后，将自动添加一条路由规则，用于私有网络内部云资源通信，该路由不可删除。除此条路由规则外，您还可以自定义其他路由规则。

- 无论是默认路由表还是自定义路由表，都可以手动添加路由规则。

### 添加路由规则

> **说明**
>
> 添加路由规则前，需要先将路由表绑定到私有网络或负载均衡器。

1. 登录 [QingCloud 管理控制台](https://console.qingcloud.com/login)。

2. 在控制台顶部的菜单栏中，选择**产品与服务** > **网络服务** > **VPC 网络**，进入**VPC 网络**页面。

3. 在页面左侧导航栏中，点击**路由表**。

4. 点击目标路由表的 ID，进入路由表详情页面。

5. 在**规则**页面，进行路由规则管理。

6. 点击**添加路由**， 在添加路由规则页面，配置路由规则。

   <img src="../../../_images/5040_add_route_rules.png" alt="添加路由" style="zoom:50%;" />

   | 参数     | 说明                                                         |
   | -------- | ------------------------------------------------------------ |
   | 目标网络 | 输入规则名称以及要转发到的目标网段。</br>点击添加更多目标网络，可以添加多个目标网段的路由规则。 |
   | 下一跳   | <ul><li>路由器：将目标网段范围内的流量路由至所选择的 VPC 管理路由器。</li><li>NAT网关：将目标网段范围内的流量路由至所选择的 NAT 网关。</li></ul><div style="background-color: #D8ECDE; padding: 10px 24px; margin: 10px 0; border-left: 3px solid #00a971;"><b> 说明</b><br/><ul><li>仅当路由表关联资源类型为私有网络时，才能配置指向 NAT 网关的路由。</li><li>NAT 网关需要与路由表在同一私有网络。</li></ul></div> |

​	

2. 点击**提交**。
3. 添加完成后，点击**应用修改**使配置生效。

### 路由规则其他操作

<img src="../../../_images/5040_route_rules_function.png" alt="更多操作" style="zoom:50%;" />

在路由规则列表，勾选目标规则后，可进行规则的修改、禁用、启用及删除操作。

- 修改：可修改规则名称、源地址、目标网络及下一跳。
- 禁用：禁用所选规则，禁用后规则失效。
- 启用：启用当前被禁用的规则，使之重新生效。
- 删除：删除所选规则。

> **注意**
>
> 对路由规则执行任何操作后，均需要点击应用修改，操作才会生效。



