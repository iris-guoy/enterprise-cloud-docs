---
title: "NAT 网关计费说明"
descriptipn: 介绍 NAT 网关计费相关信息。
draft: false
weight: 1
keyword: QingCloud, 云计算, 青云, NAT网关, NAT，费用, 计费
---

NAT 网关根据您选择 NAT 网关规格和使用时长计费。

## 计费方式

NAT 网关目前支持按需计费。

按需计费是一种后付费模式，每个计费周期的费用不固定。

**计费公式**：

实例费=实例单价（元/小时）× 使用时长（小时）

## 费用详情

| <span style="display:inline-block;width:100px">区域</span> | 小型规格单价（元/小时） | 中型规格单价（元/小时） | 大型规格单价（元/小时） |
| ---------------------------------------------------------- | ----------------------- | ----------------------- | ----------------------- |
| 北京3区<br/>北京3区-A<br/>北京3区T<br/>上海1区<br/>广东2区 | 0.5                     | 0.9583                  | 1.875                   |
| 亚太2区-A                                                  | 0.6667                  | 1.25                    | 2.4583                  |
| 雅达加区                                                   | 0.75                    | 1.4583                  | 2.8333                  |



## 计费变更

不同规格的 NAT 网关的计费价格不一样，您可以根据业务需求升降配，同时费用也将发生变更。

规格变更后立即生效，同时将按照新的规格计费。



## 欠费处理

青云系统会定期检查用户余额和当时名下弹性计费资源的消费预估， 如果检查发现余额即将不足，会提前给用户发送通知。如果您开启了余额预警功能，当账号余额小于设定的预警值时将给予短信或邮件提醒。

NAT 网关欠费后，我们为您提供了缓冲期，具体处理方式如下：

- NAT 网关实例将被暂停使用，暂停资源将保留10天，暂停期间只能进行删除和恢复操作。
- 如果您在资源暂停之后的10天内进行充值并补足欠费，将自动激活资源，恢复正常使用。
- 如果您在资源暂停之后的10天后未及时充值，资源将被销毁，相关配置和数据将不可恢复。



## 充值说明

账户余额不足或欠费后，请及时充值，以保证资源的正常使用。

青云账号支持多种充值途径：支付宝、网上银行、微信支付、线下银行转账。 可在[充值页面](https://console.qingcloud.com/finance/wallet/)选择。

如果需要发票，请到[发票管理](https://console.qingcloud.com/finance/invoices/)提出申请。
