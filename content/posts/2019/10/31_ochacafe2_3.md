---
title: "OCHaCafe2 #3 Serverlessな世界をのぞいてみよう！"
date: "2019-10-31"
tags: ["event", "serverless", "oracle"]
---

https://ochacafe.connpass.com/event/147285/

ServerlessDaysで紹介されていたイベントです。

ちょうどサーバーレスの回だったので参加しました。


## 18：30　受付開始　
* お菓子もらいました

## 19：00　オープニング
* OCHA Cafe Premiumやるよ
  - Oracle Cloud で考える高可用性アーキテクチャ
* ビッグデータのイベントもやるよ

## 19：10　セッション開始
* Oracleのブランドカラー変わっていた

* サーバーレスをざっくりと理解する
  - Fn ProjectはIronWorkerをルーツとしている
  - なぜサーバーレスが注目されているのか
    - ビジネス価値の向上
      - 課題と対策
        - 生み出すプロダクトが市場に合うかわからない
          - →素早くリリース
        - 開発に時間をかけられない
          - →開発に時間をかけない
        - お金・人が少ない
          - →低コストなシステム
        - はじめから大規模なシステムはコストが高い
          - →容易にスケール可能
      - サーバーレスの特徴
        - フレキシブル
        - シンプル
          - 価値のあるものにリソースを週痛できる
        - 低コスト
          - システムのアイドル時間には課金されない
        - スケーラブル
          - 負荷に応じてスケールする
  - サーバーレスとは（CNCFの定義）
    - 誤解：サーバーあるじゃん
    - サーバー管理を必要としない、アプリケーションの構築モデル
    - 何も動作していないときは、サーバー部分の課金なし
  - どうやってサーバー管理をなくすのか
    - FaaS(Functions as a Service)
      - なにかの処理を行うコード（Function)をクラウドへアップロードすると、クラウド側で運用管理してくれる
      - 起動イベントによりFunctionが起動し、一定時間後に削除される
    - BaaS(Backend as a Service)
      - システムのバックエンドを構成する部品を、置き換えることのできるサービス
        - ユーザー管理、認証、プッシュ通知、めせ−ジング、分析、Pub/Subキューなど
      - ビジネスの価値に直結しない部分を、クラウド側に任せる
  - 制限事項と対策
    - コールドスタート問題(FaaS)
      - →Functionの定期実行
    - Functionの実行時間上限(FaaS)
      - →アプリケーションの設計をイベントドリブンに変更
      - バッチ処理のような時間のかかる処理はそもそも向かない
  - 主なユースケース
    - Webアプリのバックエンド
      - 静的ファイルのホスティング、認証サービス、API GatewayからのFunction、データベース
    - ビッグデータ・IoT（データ分析）
      - データのストリーム処理、データ加工Function、データベース
    - データ変換処理
      - データ格納、データ処理Function、データ変換サービス、データ格納
    - 定期実行
      - システムヘルスチェックFunction、メール送信サービス

* Oracleのサーバーレスサービスを知る
  - Oracle Functions の紹介
    - Oracle Cloud Infrastructure(OCI)で提供しているFaaS
    - OSS(DFn Project)ベース
      - 任意のインフラ上にFn Projectを展開することで、Oracle Functions互換の環境を構築可能
      - 互換環境の選択肢
        - 任意のDockerホスト
          - RasPiで実行してEdgeとしての利用も可
        - K8s
          - Helmを利用することでプロダクションレベルの構成を容易に構築
        - Oracle Functions
          - マネージドサービス
          - 使った分だけ課金
     - Container Native
       - Functionをコンテナイメージとして実装
       - 依存をパッケージ可能

* 10分休憩

* demo
  - Oracle Functions で Hello World
  - 開発者ツールのFunctionでアプリケーションを作成
    - 画面が表示されないのでスキップ
  - VSCodeのリモートでインスタンスにSSHして操作
  - 内容的には今日見ていたQiitaの記事と同じかな
  - デプロイコマンドでdocker buildからイメージのpushまでまるっとやってくれる

* FDK(Function Development Kits)
  - Functionを簡単に書くためのツール
  - FKDが提供されていない言語でも自前でインターフェースを実装すれば良い
  - Dockerfileも各言語用に自動生成してくれる


* Oracle Functions の起動方法
  - SDK, CLIから
  - oci-curlから
  - HTTPから（API Gateway(LimitedAbirable)経由）
  - Eventsサービス経由
  - 定期実行（今後に期待）

* CloudEvents
  - イベントデータの標準化を目指して定義されている仕様

* Fn Flow
  - Functionのオーケストレーションツール
  - ワークフロー定義もできる
  - フローの可視化も
  - Oracle Functionsでは今後提供予定

* demo2
  - ServerlessDaysでデモしてたやつだ！
  - 猫の名前は「なまず」ちゃん
  - API GWはPhoenixリージョンで限定公開中（今日ハマりかけたやつだ）
  - Object Storageの事前承認済みリクエスト
    - S3のと同じ感じ？
  - https://github.com/Sugi275/serless_front

* まとめ
  - サーバーレスの特徴
    - シンプル、フレキシブル、低コスト、スケーラブル
  - Oracleもサーバーレス出してきている
  - コミュニティとともに盛り上げていきたい

## 20：30　セッション終了/懇親会　


## 21：45　撤収
