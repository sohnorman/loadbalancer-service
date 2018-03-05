---

copyright:
  years: 2017, 2018
lastupdated: "2018-01-11"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# ロード・バランサーの探索

IBM Cloud では複数のロード・バランシング・ソリューションを提供しており、その中から選択することになります。次の表は、ロード・バランシング・ソリューションを比較したもので、適切なソリューションの選択に役立ちます。個々のオファリングの詳細については、表の中のそれぞれのオファリングの名前をクリックしてください。 

右にスクロールすると、表の残りの部分が表示されます。


|        | [IBM Cloud Load Balancer](https://console.bluemix.net/docs/infrastructure/loadbalancer-service/getting-started.html#getting-started)| [Local Load Balancer](https://console.bluemix.net/docs/infrastructure/local-load-balancer/getting-started.html#getting-started) (共有)| [Local Load Balancer](https://console.stage1.bluemix.net/docs/infrastructure/local-load-balancer/getting-started.html#getting-started) (専用)| [Citrix NetScaler](https://console.bluemix.net/docs/infrastructure/citrix-netscaler-vpx/getting-started.html#getting-started-with-citrix-netscaler) VPX/MPX (標準)| [Citrix NetScaler](https://console.bluemix.net/docs/infrastructure/citrix-netscaler-vpx/getting-started.html#getting-started-with-citrix-netscaler) VPX/MPX (プラチナ) |
|------- | :------: | :------: | :------: | :------: | :------: |
|**パブリック VIP**|あり|あり|あり|あり|あり|
|**プライベート VIP**|なし|なし|あり|あり|あり|
|**Layer 4 LB**|あり|あり|あり|あり|あり|
|**Layer 7 LB**|なし|Cookie パーシスタンス|Cookie パーシスタンス|あり|あり|
|**ヘルス・チェック**|あり|あり|あり|あり|あり|
|**SSL オフロード**|あり|あり|あり|あり|あり|
|**管理**|IBM ポータルを介して|IBM ポータルを介して|IBM ポータルを介して|自己管理 (ベンダー GUI)|自己管理 (ベンダー GUI)|
|**高可用性**|標準装備|標準装備|オプション|オプション|オプション|
|**拡張 LB (TCP 最適化、圧縮、キャッシング、WAF)**|なし|なし|なし|制限付き|あり|
|**グローバル LB (GLB)**|なし|なし|なし|なし|あり|
|**料金**|利用ベース|月額定額|月額定額|月額定額|月額定額|
