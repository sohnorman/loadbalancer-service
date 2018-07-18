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

瞭解 IBM Cloud Load Balancer 中新增及更新的功能。

## 2018 年 4 月
### 水平調整
現在，當負載增加時，IBM Cloud Load Balancer 會自動擴增，而負載降低時則會縮減。建立負載平衡器時，會從兩個應用裝置開始，但當我們的監視系統偵測到負載增加時，應用裝置的數目可以增加（截至本文撰寫之時，最高達 16）。每一個作用中應用裝置的 IP 位址會當作 DNS A-Records 新增至負載平衡器的「完整網域名稱 (FQDN)」。

### 內部負載平衡器
現在提供高度需求的 IBM Cloud Load Balancer「內部」版本。此負載平衡器不會公開給大眾使用，但仍可用來對其 IBM Cloud 專用網路內的應用程式進行負載平衡（例如，在多層部署中，如圖所示）。它既安全且與公用端上的舊版 IBM Cloud Load Balancer 一致。 

![內部負載平衡器](./images/InternalLB.png)

### 監視度量值
您現在可以運用 IBM Cloud Monitoring 服務，來監視與負載平衡器及應用程式相關聯的效能度量值：

* 傳輸量
* 連線速率
* 作用中連線

![監視度量值](./images/Metrics.png)

負載平衡器 Web 使用者介面最多收集及顯示兩週的樣本。也可以在 IBM Cloud Monitoring 服務入口網站上檢視資料。如果您需要超過兩週的資料，則根據您可能傳送至「雲端監視」實例之其他雲端度量值的數量，可能需要升級您的監視方案。

此功能需要鏈結您的 IBM Cloud IaaS 及 PaaS 帳戶，只需幾個[簡單步驟](https://console.bluemix.net/docs/account/linking_accounts.html#unifyingaccounts)即可。 

### 密碼組合自訂作業
您現在可以自訂在負載平衡器配置為執行 SSL 終止時所使用的密碼組合。

當您在 IBM Cloud Load Balancer 啟用 SSL 終止（方法為選取 HTTPS 作為前端通訊協定）時，我們會啟用仔細選取的一組預設密碼組合，其符合最佳安全作法。我們會仔細監看任何可能探索到的新漏洞，並相應地更新清單。此功能連同軟體及硬體元件的無縫安全更新可協助保持您的應用程式始終安全無虞。
