saml-sample-js: ADFS/SAML認証サンプル（ブラウザ/JavaScript）
========================================================
ブラウザでADFS/SAML認証を行うためのサンプルです。

BaaS サーバ 事前準備
----------------------
先に BaaS サーバ上に SAML を設定したテナントを作成しておく必要があります。
手順は以下の通りです。

1. IdP メタデータを事前に入手しファイルに保存しておく。
2. BaaSコンソールでテナントを新規作成する。認証種別に 通常認証+SAML認証 を指定し、上記 IdPメタデータファイルを添付すること。
3. テナント編集画面に入り、SPメタデータをエクスポートする。
4. IdP に SPメタデータをインポートする。
5. テナント編集画面のSAML認証設定にある"許可するリダイレクトURI(オプション)"に
   コンテンツサーバ上のlanding.htmlおよびlanding_manual_login.htmlを登録する。  
    (例)  
    * http://[contentserver]/landing.html
    * http://[contentserver]/landing_manual_login.html

コンテンツサーバ 事前準備
---------------------------
js/config.sample.js を js/config.js にコピーし、
BaaSのテナントID、アプリID、アプリキー、APIベースURLなどを設定してください。

### 設定対象
* tenant
* appId
* appKey
* baseUri

SDKをデバッグモードで動作させたい場合は以下の設定をtrueとしてください。

###  設定対象
* debugMode  
  trueの場合、デバッグモード動作となりデバッグログが出力されます。

利用手順
--------
コンテンツサーバ上のindex.html（本サンプル） をブラウザで開き、以下のメニューを選択してください。

* Start authentication  
SAML認証が成功すると自動的にログインを行います。

* Start authentication(Manual Login)  
SAML認証に成功するとloginメニューが表示されます。  
loginメニューを選択するとログインを行います。

ログインが成功すると、画面上にユーザ情報が表示されます。

