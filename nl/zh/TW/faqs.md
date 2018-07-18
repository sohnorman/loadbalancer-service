---

copyright:
  years: 2017
lastupdated: "2018-03-14"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# 常見問題 (FAQ)

本節包含一些「IBM Cloud Load Balancer 服務」常見問題的回答。

## {{site.data.keyword.BluSoftlayer_notm}} 中有多少個負載平衡選項可供使用？

如需 IBM 負載平衡器供應項目的詳細比較，請參閱[探索負載平衡器](https://dev-console.bluemix.net/docs/infrastructure/loadbalancer-service/explore-load-balancers.html#explore-load-balancers)。

## 可以為負載平衡器使用不同的 DNS 名稱嗎？

雖然無法自訂負載平衡器自動指派的 DNS 名稱，但是您可以新增 CNAME（標準名稱）記錄，以將偏好的 DNS 名稱指向自動指派的負載平衡器 DNS 名稱。例如，若您的帳號為 123456，而您的負載平衡器部署在 "dal09" 資料中心且其名稱為 "myapp"，則自動指派的負載平衡器 DNS 名稱為 "myapp-123456-dal09.lb.bluemix.net"。您偏好的 DNS 名稱是 "www.myapp.com"。您可以將指向 "www.myapp.com" 的 CNAME 記錄（透過您用來管理 myapp.com 的 DNS 提供者）新增至負載平衡器 DNS 名稱 "myapp-12345-dal09.lb.bluemix.net"。

## 可以定義的負載平衡器服務的虛擬埠數目上限為何？

嘗試建立新的負載平衡器服務時，您最多可以定義兩個虛擬埠。建立服務之後，可以定義其他虛擬埠。容許的虛擬埠數目上限為 10。 

## 可以與負載平衡器建立關聯的運算實例數目上限為何？

50。

## 各種性能檢查參數的預設值及容許值為何？

預設值及容許值列示如下：

* **性能檢查間隔：**預設值是 5 秒，範圍是 2 - 60 秒
* **性能檢查回應逾時：**預設值是 2 秒，範圍是 1 - 59 秒
* **重試次數上限：**預設值為 2 次重試，而範圍是 1 到 10 次重試

**附註：**性能檢查回應逾時值一律必須小於性能檢查間隔值。 

## 可以搭配使用位於遠端資料中心內的運算實例與此服務嗎？ 

建議您的負載平衡器服務與運算實例位在相同資料中心本端內。負載平衡器服務的圖形介面 (GUI) 不會顯示來自其他遠端資料中心的運算實例。不過，GUI 將包括相同城市內其他資料中心的運算實例（例如，名稱的前三個字母相同的資料中心，如 DALxx）。不過，您可以使用 API 介面來新增任何遠端資料中心的運算實例。 

## 哪些 TLS 版本支援 SSL 卸載？

Cloud Load Balancer 服務支援含 SSL 終止的 TLS 1.2。 

下列清單詳述支援的密碼（依優先順序列出）：  

* ECDHE-RSA-AES256-GCM-SHA384
* ECDHE-RSA-AES256-SHA384
* AES256-GCM-SHA384
* AES256-SHA256
* ECDHE-RSA-AES128-GCM-SHA256
* ECDHE-RSA-AES128-SHA256
* AES128-GCM-SHA256
* AES128-SHA256

## 在我的帳戶內，可以建立的 Load Balancer 服務實例數目上限為何？ 

目前，您最多可以建立 20 個服務實例。如果您需要更多實例，請與「IBM 支援中心」聯絡。 

## 「IBM Cloud Load Balancer 服務」可與 VMWare 搭配使用嗎？ 

獲指派 SoftLayer 可攜式專用位址的 VMWare 虛擬機器可以指定為負載平衡器的後端伺服器。目前只能使用 API 來提供此特性，而無法使用 Web 使用者介面 (GUI) 來提供。使用 API 新增的可攜式專用 IP 會在 GUI 中顯示為「不明」，因為它們不是由 SoftLayer 指派。請注意，這種配置也可以與其他 Hypervisor（例如 Xen 及 KVM）搭配使用。

獲指派非 SoftLayer 位址的 VMWare 虛擬機器（例如 VMware NSX 網路）無法直接新增為負載平衡器的後端伺服器。不過，視您的配置而定，可以配置具有 SoftLayer 專用位址的媒介（例如 NSX 閘道）作為負載平衡器的後端伺服器（實際伺服器會以 VM 方式附加到 VMware NSX 所管理的網路）。

## 如果選擇使用帳戶下的公用 VLAN 來部署負載平衡器，而且已在公用 VLAN 上部署防火牆，則防火牆需要進行什麼配置才能使用負載平衡器服務？

TCP 埠 56501 是用於管理。請確定這個埠以及應用程式埠的資料流量並未遭到防火牆封鎖，否則負載平衡器佈建將失敗。

## 當得到「此 SoftLayer 帳戶未鏈結至任何 Bluemix 帳戶」錯誤時，我需要做什麼？

確定您的 SoftLayer 帳戶與您的 Bluemix 帳戶鏈結。如需進一步指示，請參閱 [Softlayer 鏈結](https://console.bluemix.net/docs/account/softlayerlink.html#switching-to-ibmid)。
