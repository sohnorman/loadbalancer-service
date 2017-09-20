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

# 關於

IBM Bluemix Load Balancer 服務可協助客戶改善其企業關鍵應用程式的可用性，方法是將資料流量分散到多個應用程式伺服器實例，並且只將資料流量轉遞至性能良好的實例。

## 特性概觀
IBM Bluemix Load Balancer 服務提供下列特性：

* 公用（網際網路面向）負載平衡器
	* 透過其完整網域名稱可公開存取服務
	* 專用子網路上的後端伺服器實例
* 基本負載平衡
	* 根據第 4 層應用程式埠資訊的資料流量配送
	* HTTP、HTTPS 及 TCP 型應用程式的支援 
	* 各種負載平衡方法（例如循環式 (RR)、加權循環式及最少連線）
	* 位在資料中心本端的虛擬伺服器與裸機計算實例之間的負載平衡
* 伺服器性能檢查
	* 定期監視伺服器性能，以確保只將資料流量轉遞至性能良好的伺服器 
	* TCP 埠是第 4 層性能檢查，而 HTTP 埠是第 7 層性能檢查 
* SSL 卸載
	* 終止送入的 SSL (HTTPS) 資料流量，以進行與後端伺服器的純文字 HTTP 通訊
* 進階資料流量管理
	* 用戶端綁定（階段作業持續性）
	* 每個虛擬埠的連線上限
* 使用直覺式圖形介面及 API 輕鬆進行管理
* 內建可靠性 
* 用量型定價 
