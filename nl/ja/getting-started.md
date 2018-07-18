---

copyright:
  years: 2017
lastupdated: "2018-04-13"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}


# 概説
IBM Cloud Load Balancer の使用を開始するには、主に次の 2 つの項目が必要です。

* IBM のアカウント: [IBMid](https://www.ibm.com/account/us-en/signup/register.html)
* IBM サーバー ([ベア・メタル](https://console.bluemix.net/docs/bare-metal/about.html#getting-started-with-bare-metal-servers)または[仮想サーバー・インスタンス (VSI)](https://console.bluemix.net/docs/vsi/vsi_index.html#getting-started-with-virtual-servers))
 
**IBMid** アカウントの取得について支援が必要な場合は、[IBM 営業担当員](https://www.ibm.com/cloud-computing/bluemix/contact-us)にお問い合わせください。

既存の IBM Cloud Infrastructure (SoftLayer) アカウントがある場合は、IBMid と[アカウントをリンク](https://console.bluemix.net/docs/account/softlayerlink.html#unifyingaccounts)することができます。 

## ロード・バランサーを注文する

IBM Cloud Load Balancer サービスを注文するには、[IBM Cloud カタログ](https://console.bluemix.net/catalog/infrastructure/load-balancer-group)から**「ネットワーク」>「ロード・バランサー」>「IBM Cloud Load Balancer」**を選択します。ログインするか新規アカウントを作成してから、以下の手順を実行してください。

1. データ・センターを選択し、サービス・プランを検討します。 **「次へ」**をクリックします。
2. ロード・バランサーをデプロイするサブネットを選択します。 ロード・バランサー・サービス・インスタンスは、このサブネット上にいずれかのネットワーク・インターフェースを持ちます。 アプリケーション・サーバーがこのサブネット上にあるか、またはこのサブネットから到達できることを確認してください。 必要な場合は、VLAN スパンニングを有効にします。 **「次へ」**をクリックします。
3. 名前、説明、フロントエンド・アプリケーションとバックエンド・アプリケーションのプロトコルとポート、およびロード・バランシングの方式などの基本のサービス・パラメーターを定義します。 初期サービス作成中は、最大 2 つのプロトコルを定義できます。 サービスの作成後は、最大 10 個のプロトコルを定義できます。 さらに、固有のフロントエンド・ポートを使用する必要があります。 **「次へ」**をクリックします。
4. 必要な場合は、ヘルス・チェック・パラメーターを調整してください。そうでない場合、デフォルト設定を使用します。 **「次へ」**をクリックします。
5. ロード・バランサーの後ろにある 1 つ以上のサーバー・インスタンスを関連付けます。 表示されるサーバー・インスタンスは、ご使用のデータ・センターからローカルとなるサーバー・インスタンスのみです。 **「次へ」**をクリックします。
6. サマリー・ページを確認し、**「作成」**をクリックします。 


サマリー・ページには、作成したばかりのロード・バランサー・サービス・インスタンスが表示されます。 **「状況」**フィールドに注目してください。 `「オフライン」`の状況は、ロード・バランサーがサービス中でないことを暗黙に示しています。 状況が`「オンライン」`に変わるまでは、新しい構成を作成したり、ロード・バランシング・サービスを提供したりすることはできません。 現在の状況を表示するには、画面を最新表示する必要がある場合があります。
 
このページにあるサービス名をクリックすると、そのサービスの概要ページが表示されます。 **「プロトコル」**、**「ヘルス・チェック」**、および**「サーバー・インスタンス」**の各タブにナビゲートして既存の構成を編集することができます。
