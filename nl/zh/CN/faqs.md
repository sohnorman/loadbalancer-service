---

copyright:
  years: 2017
lastupdated: "2017-08-21"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# 常见问题及解答

本节包含一些 IBM Bluemix Load Balancer 服务常见问题的解答。

## 使用 Load Balancer 服务可以定义的最大虚拟端口数是多少？

尝试创建新的 Load Balancer 服务时，您最多可以定义两个虚拟端口。在创建服务后，您可以定义附加虚拟端口。所允许的最大虚拟端口数目为 10。 

## 可以与 Load Balancer 相关联的最大计算实例数是多少？

50。

## 可以创建仅能由内部客户机访问的仅限内部专用的 Load Balancer 吗？  

目前还不行。IBM Bluemix Load Balancer 上托管的服务将会分配一个可从公共互联网访问的标准域名。 

## 各种运行状况检查参数的缺省设置和允许值是什么？

缺省设置和允许值如下所示：

* **运行状况检查间隔：**缺省值为 5 秒，范围为 2 – 60 秒
* **运行状况检查响应超时：**缺省值为 2 秒，范围为 1 –59 秒
* **最大重试次数：**缺省值为 2 次，范围为 1 到 10 次

**注：**运行状况检查响应超时值必须始终小于运行状况检查间隔值。 

## 可以将远程数据中心内的计算实例与此服务一起使用吗？ 

建议 Load Balancer 服务和计算实例位于相同数据中心的本地内。Load Balancer 服务的图形界面 (GUI) 不会显示来自其他远程数据中心的计算实例。但是，GUI 将包括同一城市其他数据中心的计算实例（例如，名称共享前三个字母的数据中心，如 `DALxx`）。不过，您可以使用 API 接口，添加任何远程数据中心的计算实例。 

## SSL 卸载支持哪个 TLS 版本？支持哪些密码？

Bluemix Load Balancer 服务支持具有 SSL 终止功能的 TLS 1.2。 

下表详细说明受支持的密码（按优先顺序列出）：  

* ECDHE-RSA-AES256-GCM-SHA384 
* ECDHE-RSA-AES256-SHA384 
* DHE-RSA-AES256-GCM-SHA384 
* DHE-RSA-AES256-SHA256 
* AES256-GCM-SHA384 
* AES256-SHA256 
* ECDHE-RSA-AES128-GCM-SHA256 
* ECDHE-RSA-AES128-SHA256 
* DHE-RSA-AES128-GCM-SHA256 
* DHE-RSA-AES128-SHA256 
* AES128-GCM-SHA256 
* AES128-SHA256 

## 可以定制 SSL 密码列表吗？

目前还不行。

## 在帐户中可以创建的最大 Load Balancer 服务实例数是多少？ 

目前，最多可以创建 20 个服务实例。如果您需要更多实例，请联系 IBM 支持人员。 


