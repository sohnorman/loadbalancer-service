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

# SSL オフロード

すべての着信 HTTPS 接続について、ロード・バランサー・サービスは SSL 接続を終了し、バックエンド・サーバーとのプレーン・テキスト HTTP 通信を確立します。それにより、バックエンド・サーバーは、CPU 集中型の SSL ハンドシェークおよび暗号化/暗号化解除のタスクの実行からオフロードとなり、アプリケーション・トラフィックの処理にすべての CPU サイクルを使用できます。ロード・バランサーが SSL オフロード・タスクを実行するには、SSL 証明書が必要です。既存の SSL 証明書を使用するか、新しい SSL 証明書を購入し、[Bluemix/Softlayer 証明書ストア](https://control.softlayer.com/security/sslcerts)を介して管理できます。 

**注:** ロード・バランサー・サービスは、SSL オフロードを有効にした TLS バージョン 1.2 をサポートしています。SSLv3 は、脆弱性があるためサポートしていません。SSL 暗号リストは、現時点ではカスタマイズできません。 
