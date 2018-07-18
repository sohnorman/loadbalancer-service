---

copyright:
  years: 2017
lastupdated: "2018-05-01"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}


# 新增功能

了解 IBM Cloud Load Balancer 中的新增功能和更新功能。

## 2018 年 4 月 
### 水平伸缩
IBM Cloud Load Balancer 现在将随着负载的增加自动向上扩展（并随着负载的减少而向下扩展）。创建负载均衡器时，一开始有两个设备，但是当监视系统检测到负载增加时，设备数量可以增加（目前为止最多 16 个设备）。每个活动设备的 IP 地址将作为 DNS A 记录添加到负载均衡器的标准域名 (FQDN) 。

### 内部负载均衡器
现在，IBM Cloud Load Balancer 的高要求“内部”版本已可用。此 Load Balancer 不向公众公开，但是仍可用于对其 IBM Cloud 专用网络中的应用程序进行负载均衡（例如，在多层部署中，如图所示）。它不但安全，还与公共端先前版本的 IBM Cloud Load Balancer 保持一致。 

![内部负载均衡器](./images/InternalLB.png)

### 监视度量值
您现在可以利用“IBM Cloud Monitoring”服务来监视与负载均衡器和应用程序关联的以下性能指标：

* 吞吐量
* 连接速率
* 活动连接数

![监视度量值](./images/Metrics.png)

负载均衡器 Web UI 收集并显示最多两周的样本。还可以在 IBM Cloud Monitoring 服务门户网站上查看这些数据。如果您需要两周之前的数据，根据您可能发送到 Cloud Monitoring 实例的其他云度量值的量，您可能需要升级监视套餐。

此功能需要链接您的 IBM Cloud IaaS 和 PaaS 帐户，只需[简单几步](https://console.bluemix.net/docs/account/linking_accounts.html#unifyingaccounts)。 

### 密码套件定制
您现在可以定制负载均衡器配置为执行 SSL 终止时使用的密码套件。

在 IBM Cloud Load Balancer 上启用 SSL 终止（通过选择 HTTPS 作为前端协议）时，我们启用了精心选择的符合最佳安全实践的一组缺省密码套件。我们将密切关注可能发现的任何新漏洞，并相应地更新列表。此列表以及软件和硬件组件的无缝安全更新将有助于时刻确保应用程序的安全。
