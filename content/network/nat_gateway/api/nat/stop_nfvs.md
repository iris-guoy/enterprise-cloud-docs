---
title: "StopNFVs"
description: 关闭网络组件(NFV)
draft: false
weight: 11
keyword: 青云, QingCloud, 云计算, API, NFV, NAT 网关, 网络组件
---



关闭一个或多个网络组件(NFV)。

**Request Parameters**

| Parameter name | Type | Description | Required |
| --- | --- | --- | --- |
| nfvs.n | String | 网络组件的 ID | Yes |
| zone | String | 区域 ID，注意要小写 | Yes |

[_公共参数_](../../get_api/parameters/)

**Response Elements**

| Name | Type | Description |
| --- | --- | --- |
| action | String | 响应动作 |
| job_id | String | 关闭一个或多个网络组件(NFV) job ID 号 |
| ret_code | Integer | 执行成功与否，0 表示成功，其他值则为错误代码 |

**Example**

_Example Request_

```
https://api.qingcloud.com/iaas/?action=StopNFVs
&nfvs.1=nfv-1234abcd
&COMMON_PARAMS
```

_Example Response_:

```
{
  "action":"StopNFVsResponse",
  "ret_code":0,
  "job_id":"j-0om6hgcokm4"
}
```
