---
title: "Serverless Meetup Tokyo #14"
date: "2019-09-19"
tags: ["event", "serverless"]
---

Serverless Meetup Tokyo #14
https://serverless.connpass.com/event/143446/

## 19:10-19:15	Opening Talk	堀家 隆宏 (Serverless Operations LLC. CEO)
* Serverless Daysやるよ

## 19:15-19:20	会場案内、告知	株式会社Speee
* Good Coffee -> Good COde

## 19:20-19:40	機械学習MVPにServerless Frameworkがオススメな理由	池田 雄太郎（株式会社 KaizenPlatform）
* 短期的・長期的ダイナミクス
* 短期的：一時的に大量なリソースが必要
* 長期的：やってみないとわからないやつ
* ー＞リソースのスケールが必要
  - ー＞そこでserverless
* Serverlessの悩み
  - ベンダー、性能、セキュリティ、設定・デプロイ
* 使うBaaSが多くなりがち
  - 管理が大変
* DevOps環境の構築が大変
* そこでServerless Framework
  - リソース情報を一括管理できる
  - yaml の custom で定義
  - CFnも書く必要がある？

## 19:40-20:05	今Serverlessが面白いわけ（v19.09）	川崎 庸市（Microsoft Corporation）
* Serverless != サーバーがない
* Serverless = サーバーを管理する必要がない
* Serverlessの定義
  - スケーリング
  - 管理不要
  - 本質的な作業に集中
* 人類の問題解決
* FaaSはインフラ進化の賜物
  - コンテナ
  - 実行単位が分離されている→セキュリティ有利
  - CGI-Bin？
  - データストアの進化
    - 水平スケール大事
    - NoSQLがマッチしている
  - 進化の方向性
    - 自動化、抽象化、標準化
* 標準化が課題
  - ベンダーロックインの懸念
  - CNCF Serverless WGで進められている
  - Cloud Events
    - イベントスキーマ標準化のための共通仕様
  - 複雑性の抽象化
    - Terraform, plumi
* マルチクラウド化対応
  - K8sベースのServerless環境
  - K8sがインフラを抽象化
  - Knative, KEDA
  - クラスタレス
    - バッチ処理とか
  - Virtual Kubelet
    - クラウドのリソースをK8sから管理

## 20:05-20:15	Social	／
休憩

## 20:15-20:35	AWSで開発するサーバレスAPIバックエンド	三宅 暁（フリーランス）
* AppSync,DynamoDB,Cognito でGraphQLなAPIを作る
* GraphQL
  - スキーマファースト
* Amplify->AWSにロックイン
* Serverless FWにAppsyncのプラグインがある
* VTL＝Apache Velocity Template Language？
* ノンコーディング

## 20:35-20:40	今日飲み物持ち込んでるエフセキュアのサーバーレス向けセキュリティ	河野 真一郎（エフセキュア株式会社）
* AWS,GCP,Azure向けがまだない。

## 20:40-	After Meetup + Knative LT 杉田 寿憲（メルペイ）	21:30までに完全撤収


