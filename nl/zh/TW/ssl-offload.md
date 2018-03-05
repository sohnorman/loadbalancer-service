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

# SSL 卸載

對於所有送入的 HTTPS 連線，負載平衡器服務會終止 SSL 連線，並建立與後端伺服器的純文字 HTTP 通訊。因此，會卸載後端伺服器，不執行 CPU 密集 SSL 信號交換及加密/解密作業，讓它們可以使用其所有 CPU 週期來處理應用程式資料流量。需要有 SSL 憑證，負載平衡器才能執行 SSL 卸載作業。您可以使用預先存在的 SSL 憑證或購買新的 SSL 憑證，然後透過 [IBM Cloud 憑證庫](https://control.softlayer.com/security/sslcerts)進行管理。 

**附註：**負載平衡器服務支援含 SSL 卸載的 TLS 1.2 版。它因為漏洞而不支援 SSLv3。目前無法自訂 SSL 密碼清單。 
