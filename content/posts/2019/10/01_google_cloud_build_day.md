---
title: "Google Cloud Build Day"
date: "2019-10-01"
tags: ["GCP", "CI/CD", "event"]
---

https://gcpug-tokyo.connpass.com/event/143453/

* GCPの[Cloud Build](https://cloud.google.com/cloud-build/?hl=ja)サービスに関する話。
* AWSだと、CodePipelineとCodeBuildとCodeDeployに相当するもの。

## 19:30 ~ 20:00 マルチアーキテクチャイメージの作成（仮） @ymotongpoo
* イベントベースでビルドのトリガー（GitHubのpushとか）
* テストの実行とアーティファクトのビルド
* 雑に言うとDocker on Docker
* ビルド実行時間にる対する課金
* Artifact management
  - プライベートコンテナレジストリに自動push＆脆弱性スキャン
* 70以上のビルダーイメージ
* Cloud Console UIで実行状況・結果の確認ができる
* セキュア情報はKMSと連携して暗号化可能
* Dockerが入っていればローカルで試すことができる
* STEPの並行実行ができる
  - 依存関係も定義できる（waitFor）

## 20:00 ~ 20:25 Cloud Build out of steps @apstndb
* CI/CDにおけるコンテナ間の通信
* K8s IN Docker(KIND)
  - DOckerの中で本物のK8sクラスタを構築するツール
  - 現在アルファ版
  - CircleCI, TravisCI, GitHub Actionで動いた報告あり
* STEP内でdocker buildが使える→docer runも使える→何でもできる
* 他のCI/CDサービスとは異なるアプローチ
* dockerize
  - 他のコンテナの起動を待つ用途で使っている
  - https://github.com/jwilder/dockerize
* Cloud BuildでKINDするには
  - STEPから外れる必要がある
  - Docker Networkが使えないのでhostネットワークを使う＝STEPと直接通信できない
* デモは時間切れ。。

## 20:25 ~ 20:35 休憩

## 20:35 ~ 20:50 Cloud Buildを気軽なコンテナ実行環境として利用する @chidakiyo
* 注意点
  - `gcloud builds submit`した際に指定したディレクトリは以下のファイルが送られる。
  - 巨大なファイルがあると大変。
  - `.gcloudignore`で除外指定可能。
  - 無料枠は請求先アカウント単位なので複数プロジェクトでやるとすぐ尽きる
* 事例
  - Dataflowを使っていた処理のCloud build化
  - gcloudコマンドさえ入っていればローカルに諸々インストールする必要がない

## 20:50 ~ 21:10 LT
### yukinagae
* Berglas（ばーぐらす）
  - Cloud KMSとCloud Storageで暗号化できる
* デモは時間切れ。。

### SouMatsuda
* Cloud Build x Terraform
* 通常、ローカルで実行する init, plan, apply をCloud Buildで実施する
* インフラの設定変更が頻繁に起きる場合は工数削減に効く
* それなりに学習コストはかかる

### kumagai
* Cloud Build で docker-compose と ansible
* 用途
  - 自動テスト用ベースイメージとして
  - 開発者にGCEのテンプレートとともに渡す
  - 社内デモ環境としてGKEで起動

## 感想
* Cloud Build使ってみたくなった。
* ちょうどblogのCI作ろうとしていたから、これでやってみようかな。
