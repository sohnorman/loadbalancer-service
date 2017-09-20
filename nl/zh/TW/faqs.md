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

# 常見問題 (FAQ)

本節包含一些 IBM Bluemix Load Balancer 服務常見問題的回答。

## 可以定義的負載平衡器服務的虛擬埠數目上限為何？

嘗試建立新的負載平衡器服務時，您最多可以定義兩個虛擬埠。建立服務之後，可以定義其他虛擬埠。容許的虛擬埠數目上限為 10。 

## 可以與負載平衡器建立關聯的計算實例數目上限為何？

50。

## 可以建立只有內部用戶端才能存取的僅限內部專用負載平衡器嗎？  

目前不行。IBM Bluemix 負載平衡器上所管理的服務，將會獲指派可從公用網際網路存取的完整網域名稱。 

## 各種性能檢查參數的預設值及容許值為何？

預設值及容許值列示如下：

* **性能檢查間隔：**預設值是 5 秒，範圍是 2 - 60 秒
* **性能檢查回應逾時：**預設值是 2 秒，範圍是 1 - 59 秒
* **重試上限：**預設值是 2 次重試，範圍是 1 到 10 次重試。

**附註：**性能檢查回應逾時值一律必須小於性能檢查間隔值。 

## 可以搭配使用位於遠端資料中心內的計算實例與此服務嗎？ 

建議您的負載平衡器服務與計算實例位在相同資料中心本端內。負載平衡器服務的圖形介面 (GUI) 不會顯示來自其他遠端資料中心的計算實例。不過，GUI 將包括相同城市內其他資料中心的計算實例（例如，名稱的前三個字母相同的資料中心，如 `DALxx`）。不過，您可以使用 API 介面來新增任何遠端資料中心的計算實例。 

## 哪些 TLS 版本支援 SSL 卸載？支援哪些密碼？

Bluemix Load Balancer 服務支援含 SSL 終止的 TLS 1.2。 

下列清單詳述支援的密碼（依優先順序列出）：  

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

## 可以自訂 SSL 密碼清單嗎？

目前不行。

## 在我的帳戶內，可以建立的 Load Balancer 服務實例數目上限為何？ 

目前，您最多可以建立 20 個服務實例。如果您需要更多實例，請與 IBM 支援中心聯絡。 


