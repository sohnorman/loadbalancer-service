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

# SSL 卸载

对于所有入局 HTTPS 连接，Load Balancer 服务会终止 SSL 连接并与后端服务器建立纯文本 HTTP 通信。由此，后端服务器会卸载掉执行 CPU 密集型 SSL 握手和加密/解密任务，因此它们可以使用所有 CPU 周期来处理应用程序流量。Load Balancer 需要 SSL 证书才能执行 SSL 卸载任务。您可以使用预先存在的 SSL 证书或购买一个新证书，并通过 [Bluemix/Softlayer 证书库](https://control.softlayer.com/security/sslcerts)对其进行管理。 

**注：**Load Balancer 服务支持具有 SSL 卸载功能的 TLS V1.2。它因其自身的漏洞，不支持 SSLv3。目前不能定制 SSL 密码列表。 
