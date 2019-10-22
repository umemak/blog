---
title: "Serverless Days TOkyo 2019"
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


## 13:40 short break


## 13:45 Zero Scale Abstraction in Knative Serving
### Tsubasa Nagasawa (CyberAgent)


## 14:25 Long break


## 14:40 空調設備向けIoTシステムにおけるクラウドランニングコスト
### 野原 健太 / ダイキン工業株式会社


## 15:00 short break


## 15:05 ISPがサーバレスに手を出した
### 伊藤良哉 & 松田丈司 (NTTコミュニケーションズ)


## 15:45 Long break


## 16:00 AWS Lake Formation で実現、マイクロサービスのサーバーレスな分散トレーシング
### 江藤武司 & 岩井良和 (Sony Corporation)


## 16:20 short break


## 16:25 Don’t think Serverless Security, think Application Security
### Ido Neeman (Nuweba)


## 17:05 short break


## 17:10 Azure でサーバーレス、 Infrastructure as Code どうしてますか？
### Kazumi Ohira


## 17:30 short break


## 17:35 The hidden cost and technical debt of running huge Serverless service on production
### James Nguyen / MaaS Global


## 17:55 short break


## 18:00 Lightning Talks x 4


## 18:40 Closing Remarks


## 19:00 Community Social / 懇親会


