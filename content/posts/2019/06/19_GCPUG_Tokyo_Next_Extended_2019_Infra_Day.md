---
author: "umemak"
date: 2019-06-19
title: GCPUG Tokyo Next Extended 2019 Infra Day
tags: [ "GCP", "event" ]
---

* 2019/06/19(Wed)
* 19:00 〜 22:00

## Next Introduction

## Next 189 UPDATE Infra misc
* Anthos
  - 複数のコンポーネントの集合体
  - 去年はCSPという名前
  - GKEとオンプレをまとめて扱うみたいな
* OSSベンダとのパートナーシップ
  - 基本、Googleのクローズドソースだった
  - ElasticとかMongoDBとか
  - 今年中くらいにリリース？
* Google Cloud Storage
  - 新しいタイプ Ice Cold Archive
  - Nearline, coldline のさらに安いやつ
  - まだ保存料金しか発表されていない
* Cloud Firestore Collection group queries
  - 複数のSUb CollectionをまとめてQueryできるようになった
* Cloud Bigtable Multi Region Replica
  - 別リージョンのクラスタを相互に同期できるようになる
* Microsoft SQL Server on Cloud SQL
  - aws RDS的な
  - アルファバージョン
  - ActiveDirectoryのフルマネージドも出た
* Policy Intelligence
  - Policy(awsのrole?)の管理補助ツール
  - 使われていない権限（削除しても良くない？）を見つけてくれる
  - どの設定で403になるのか調査してくれる

## Service Networking
* traffic director
 - コンテナである必要はない
 - ユーザーに使いリージョンにトラフィックを流したりできる（Istioではできない）
   - まだアルファバージョン
* Cloud Service Mesh
  - Stackdriverと連携もできる
  - これもプライベートアルファバージョン
* Istio On GKE
  - managed istio
  - GKEのバージョンとIstioのバージョンは密結合
* keywords
 - instagramはモノリス
   - 世界最大のpythonプロダクト？
   - Envoy for iOS and android
 - mutual TLS

## パネルディスカッション
* Service Mesh Interface(SMI)
* PostgresOperator
* https://skywalking.apache.org/
* Oracle RAC をクラウドで使うのは無理
*  





