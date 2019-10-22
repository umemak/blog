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


