---
title: "DeleteRouterStatics"
description: 删除一条或多条 VPC 网络规则。
keyword: QingCloud, 青云, 云计算, VPC, VPC 网络规则
weight: 30
draft: false
---

删除一条或多条 VPC 网络规则。在删除 VPC 网络规则之后，你需要执行 [_UpdateRouters_](../update_routers/) 来使规则删除生效。

**Request Parameters**

| Parameter name | Type | Description | Required |
| --- | --- | --- | --- |
| router_statics.n | String |  VPC 网络规则ID | Yes |
| zone | String | 区域 ID，注意要小写 | Yes |

[_公共参数_](../../get_api/parameters/)

**Response Elements**

| Name | Type | Description |
| --- | --- | --- |
| action | String | 响应动作 |
| ret_code | Integer | 执行成功与否，0 表示成功，其他值则为错误代码 |
| router_statics | Array | 删掉的 VPC 网络规则ID列表 |

**Example**

_Example Request_:

```
https://api.qingcloud.com/iaas/?action=DeleteRouterStatics
&router_statics.1=rtrs-wls7otet
&router_statics.2=rtrs-j1tsul7v
&router_statics.3=rtrs-b3epyxu5
&zone=pek3a
&COMMON_PARAMS
```

_Example Response_:

```
{
  "action":"DeleteRouterStaticsResponse",
  "ret_code":0,
  "router_statics":[
    "rtrs-wls7otet",
    "rtrs-j1tsul7v",
    "rtrs-b3epyxu5"
  ]
}
```
