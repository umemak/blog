---
title: "Serverless Days Tokyo 2019"
date: "2019-10-22"
tags: ["serverless", "event"]
---

サーバーレスのカンファレンス

https://tokyo.serverlessdays.io/


## 09:00 はじめに / 諸説明
* meetup 4年目
* 大企業での採用が進んできている

## 09:10 10x Serverless Product Development for a Startup with Microsoft Azure
### Yutaka Tachibana(EBILAB)
* 飲食店の生産性向上
* 来客人数の予測（過去実績、天気などから）
* 入店率も計算している
  - 店頭のディスプレイでA/Bテストも可能
* データソースが増えても追加実装は簡単
* PowerBI Embedded
  - レポートをノンコーディングで作成できる
  - エンジニアはレポート追加にノータッチ
* サーバーレスで実装したメリット
  - 開発運用コストが少ない
  - 将来的にスケールした場合の楽観的
  - 責務分割が自然にできる
  - 協業・分業しやすい

## 09:50 break

## 10:00 Keynote
### Keisuke Nishitani (AWS)
* EventDriven
  - 呼ぶ側と呼ばれる側が疎結合にできる
* aurora, ecs も2014年のre:inventで発表された
* モダンアプリケーション
  - 市場投入を加速
  - イノベーションの向上
  - 信頼性の向上
  - コスト削減
* All you need is code
  - 付加価値を産まない重労働からの開放
* 5年たった今も
  - We're still writing code
* もっとコードを減らすためには
  - どういう問題をどう解決するのか

## 10:40 10 min break
* スポンサーLT

## 10:50 Keynote: Infinite Scaling, Finite Failures: Serverless Resiliency Patterns and Lessons Learned
### Katy Shimizu (Microsoft)
* 失敗は絶対に起こります。アプリケーションがそれらを処理する必要があります
  - Data source
  - Customer code
  - Serverles/Fass layer
  - External deebdebct
  - IaaS/Pass
  - Datacenter/Infra
* 失敗例
  - レースコンディション
  - ネットワーク障害
  - レート制限
  - ハードウェア障害
* 依存関係を知る、依存関係が失敗する方法を知る
  - デザインパターン
* デザインパターン
  - 再試行
    - サービスに組み込まれている
  - サーキットブレーカー
    - 耐久性のあるエンティティを試す
* 新製品を使用すると、回復力が容易になります
  - Durable Functions 2.0
  - Premium hosting plan
* サーバーレスは改善され続けています

## 11:30 10 min break


## 11:40 グローバル展開のコネクティッドカーを支える大規模サーバーレスシステム事例
### Yuya Urayama (TOYOTA), Takanori Suzuki (Acroquest Technology) and Eiichiro Uchiumi (AWS)
* なぜサーバーレスを選んだのか
  - Connented Platform
    - 日本・中国・北米でサービス提供中
  - 無駄の削減のため
* 夜間と日中のアクセス数の差が大きい
  - 日中のアクセス数に合わせたリソース確保→無駄
* 長く乗られる（平均8．5年）
  - パッチあてなどの保守工数→無駄
* 広い地域での提供
  - 各国現地にリソース確保→無駄
* 設計指針
  - 一貫した方法でコンポーネントを分割
  - 緩やかに統合
  - プロセスをステートレスに構成
* アーキテクチャスタイル
  - Nティア−
    - コンポーネントを役割に応じて分割する
  - ウェブキューワーカー／イベントドリブン
    - ロジック層をウェブとワーカーに分割する
  - マイクロサービス
    - ライフサイクルを共有する最小単位でコンポーネント群を複製し、自律可動境界を設定
* 実装パターン
  - リアクティブスケーリング型
    - API GW + Lambda
    - 基本はこっち
  - プロアクティブスケーリング型
    - ALB + Fargate
    - ある程度余裕をもたせたい、スケールをコントロールしたいとき
  - P2P
    - SQS
  - ファンアウト
    - SNS
  - イベントストリーミング
    - Kinesis Streams
  - ワーカープロセス
    - Lambda
* 特徴
  - トラフィックの特性によってスケーリングパターンを選べる
* デプロイメントはカオス
* 課題
  - 開発量は少なくなったがテストしにくい
    - CI/CDパイプラインでのテスト実行環境の整備
    - Localstack、Karateを利用
    - イベントドリブンな部分のテスト、非同期の処理結果も確認している
  - 各機能はシンプルになったが全体が見にくい
    - X-Rayを利用
  - 自動スケールは便利だがコントロールすべき要素が出てきた
    - リトライ用Lambdaが数千並列した
      - アカウントに対する同時実行数の上限までスケールした結果、他のLambrdaの起動が妨げられる
    - コールドスタート問題
      - 時間がかかる処理が重なってAPI/GWがタイムアウト
      - ENIのIP枯渇
* 運用フェーズ
* 激務コンテナ・サボりコンテナ問題
  - アクセスログ数を気合でカウントした結果
    - 激務もサボりもなかった
  - どんなメトリクスをどの粒度でどう見るかを予め検討する
* 運用コストが下がった結果
  - 運用にかけていたコストを開発に回した
  - デプロイサイクルの高速化
* 今後の展望
- スケーリングを最適化
- プラットフォームの挙動をより的確に把握
- 問題が生じた際の回復を自動化

## 12:20 Lunch


## 13:20 All You Need Is JavaScript
### Jensen Hussey / Cloudflare
* Cloudflare worker
  - サーバーレス用JS実行環境
  - V8エンジン採用
    - WebAssemblyが使えるので、JS以外の言語でも開発可能
  - ユーザーの地理情報を利用してエッジで翻訳することができる

## 13:40 short break


## 13:45 Zero Scale Abstraction in Knative Serving
### Tsubasa Nagasawa (CyberAgent)
* Build, Serving, Events
  - Buildは卒業（てくとん）
* K8Sのyamlたくさんカカkなくてもデプロイできる
* tag（リビジョン）でデプロイを分けて、カナリアリリースのようなこともできる
* ゼロスケール
  - フローを紙芝居で説明。あとでちゃんと読み込みたい。
* Pros
  - オートスケールが柔軟
  - テストがちゃんとしている
    - google/mako
* Cons
  - Podに入れられるコンテナが1つ
  - Webhook自作で複数入れることも可能
  - 使えるVolumeに制限がある
  - Podの配置席ノードが指定できない
    - サーバーレスの思想にそぐわない
* Autoscale
  - コールドスタート1秒未満を目標にしている（現在4秒程度）
* 本番投入に向けて
  - 学習コスト
  - yaml地獄
  - ゼロスケール可能
  - KnativeとK8sのDual Stack
  - ポータビリティ

## 14:25 Long break


## 14:40 空調設備向けIoTシステムにおけるクラウドランニングコスト
### 野原 健太 / ダイキン工業株式会社
* 想定500万台、30万人（同時アクセス数9万人）
  - 性能とScalaリビリティをAWSに任せる
  - RDMSは使わない
  - 接続台数に応じてコスト最適化
  - 1台あたり数百項目（差分のみ送信）
* **サーバーレス開発はクラウドランニングコストとの戦い**
  - サーバーレスを適すつに使えば、機能面、非機能面ともに作り低システムは作れる
* コスト
  - DynamoDB書き込み時
  - 運転データ参照時のLambda処理時間
* DynamoDBデータ構造
  - 1台1アイテム→部分更新でもWCU対象消費
  - 運転項目1アイテムとして格納→改善したが、取り出し時に時間がかかりすぎる
  - PartitionKeyを建物IDに、SortKeyを機器IDと項目名の結合→取り出し時間の短縮達成

## 15:00 short break

## 15:05 ISPがサーバレスに手を出した
### 伊藤良哉 & 松田丈司 (NTTコミュニケーションズ)
* サーバーレス以外の選択肢
  - 物理サーバー、自社IaaSサービス、他社IaaSサービス
  - 納期3ヶ月→サーバーレス以外間に合わない
* 社倍基準と通信事業としての基準
  - 社内クラウドを利用しない理由
    - IPv6未対応だった
  - 信頼性の担保
    - マルチクラウドで
* IPv6使えない
  - CDNを間に挟む
* ローカルテスト
  - Serverless Frameworkとプラ部員で動かす
* 負荷試験ツール
  - Gatling
  - 無償版はシェルスクリプト頑張ればスケールできる
* CI導入のメリット
  - テスト実行の担保
  - 環境が汚れない
  - 証跡が取れる
* slsでIaC
  - プラグインが多い
  - AWSの対応範囲が広い（全部ではない）
  - AzureはFunctionのみ対応
  - Blue/Greenデプロイ

## 15:45 Long break


## 16:00 AWS Lake Formation で実現、マイクロサービスのサーバーレスな分散トレーシング
### 江藤武司 & 岩井良和 (Sony Corporation)
* 製品の特性ごとにAWSアカウント分けて構築
* DynamoDB streamやSNSでクロスアカウントだったりオンプレとやり取りしたり
* ユーザーからの問い合わせがすぐ来るときもあれば、何かあってから1ヶ月以上立ってから来ることもある
* →調査が大変
* そこで分散トレーシング
* Lake Formationを分散トレーシングにつかう
  - 複数アカウントのログを集約できる
  - サーバレスで実現できる
  - X-Ray, CWLogs, Datadogも併用
* トレースIDの重要性
  - X-Rayだけでは非同期イベントのトレースが困難
  - API GW
    - カスタムHTTP Headerを利用して伝搬
    - zone.jsを利用してIDを保持
  - SNS、SQS
    - message attributesを利用して伝搬
  - Step FUncitons
    - StateMachne実行時にトレースIDを注入
    - ResulePathを使用して、書くTaskにIDを注入
  - S3
    - オブジェクトメタデータを利用する
    - APIのhtad-objectを利用して取得
    - イベントオブジェクトからは取得できない
    - オブジェクト削除時は、工夫が必要

## 16:20 short break


## 16:25 Don’t think Serverless Security, think Application Security
### Ido Neeman (Nuweba)
* FUDの例とそれに対する回答的な
* 全編英語なので資料公開されたら読み返したい
* How Serverless Inprever\s Security
  - Serverkess platforms manage tge nahiruty id the secyrutyattack
  - Small and contained blast raduys
  - Finegrained acces cntrol
  - Ephemetality: No attackers' and data oresustence?
  - No infrastryctyre - more time to wrute better go
* How to protect your serverless Application
  - Attacler don't care if app run on sercerless, containers, VNs or Rasi
  - Hhow to maintain and improve secyrutt oisryre wgeb tridutuibak tiiks art nistkt ineffective
  - Abrtraction of the infrastrycrute can introduct some chalenges:
    - you still need to secure rhe app layer
    - limited visibility
    - where to install tools? lambda layers?
    - security logic performance overhead
    - How to enforce existic\bg secyrtt oikucues?
    - fast dev-to-oriduction cycle

## 17:05 short break


## 17:10 Azure でサーバーレス、 Infrastructure as Code どうしてますか？
### Kazumi Ohira
* IaC
  - コードにしておけば、あとから思い出せる
  - CI/CDと相性が良い
* ARM template
  - AzureのCFn？
  - Azure Resource Manager
  - GUIで作った構成をエクスポートできる
  - CUIでデプロイしなくてもGUIでデプロイできる
  - json で書く
* APIバージョン
  - Azure REST APIと連動している
* セキュアに扱う
  - Parameterの方secure系を使う
  - Key Vaultから受け取る
  - ManagerdIdentitiesや　VirtuanNetwork
* リソース名の付け方
  - リソースごとに異なる
  - グローバルで一位でなければいけないものがある
  - StorageAccountの制限が厳しい
* コードのモジュール化
  - Linked templateを使う
* Terraformでも可

## 17:30 short break

## 17:35 The hidden cost and technical debt of running huge Serverless service on production
### James Nguyen / MaaS Global


## 17:55 short break


## 18:00 Lightning Talks x 4


## 18:40 Closing Remarks


## 19:00 Community Social / 懇親会


