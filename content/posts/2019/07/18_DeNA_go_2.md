---
author: "umemak"
date: 2019-07-18
title: DeNA.go #2
---

# DeNA.go #2
* 2019/07/18 19:30-
* https://dena.connpass.com/event/133957/

## @kiyotaka.nakashima / 新ゲームサーバ基盤TakashoでのGo言語活用事例の紹介 / ゲーム・エンターテインメント事業本部
* Sakasho
  - 共通ゲームサーバー（複数タイトルで相乗り）
  - プレイヤーデータの管理
  - 課金系
* Sakasyoの課題
  - 相乗りによる制約
  - 変更の影響大
* Takasho
  - Webサバーフレームワーク
  - ステートレスなAPI
  - 1サーバー1クライアント
  - GCP(GAE)前提(Terraformで構築)
  - 共通機能も提供
  - クライアント側はC#
  - サーバ側はGo
    - 少ない学習コストで高いパフォーマンスと安定性
* RPCサーバ
  - net/httpベース
  - gRPCの独自実装（GAEでgRPCがサポートされていなかった）
  - protoスキーマからコード生成
  - DBテーブルまわりもjsonで定義して生成

## @toku_bass /次世代タクシー配車サービス「MOV」におけるテスト事例紹介 / オートモーティブ事業本部
* GAE / CircleCI / chatbot E2E
* 方針
  - テスト対象以外の暗黙のデータに依存しない
  - テスト全体に関わるfixtureを使わない
    - マスターデータはOK
  - 並列でテストを実行
    - user_idなどの固定値を書かないようにする
    - github.com/bxcodec/faker
    - primary key をランダム生成してかぶる対策
* testerator
  - GAEのテストサーバーを立ち上げっぱなしにしてくれる
  - 起動には3秒くらいかかる
* pstest
  - Cloud PubSubの公式ライブラリのテスト方法
  - どうやってテストしたらよいかわからなければ公式を見に行く
    - 公式もテストできていないことも・・

## @kurikei / DeSCヘルスケアにおけるGo活用事例の紹介 / DeSCヘルスケアサービス企画開発部
* GCP(GAE/Cloud Firestore/Cloud Functions/BigQuery) / CircleCI / OpenAPI 3
* レイヤードアーキテクチャ（+DIP）
  - レイヤーで分離する→各レイヤーで関数を定義する→コード量が増える→テストも増える
  - gomockを使う
* 暗号化の手法
  - DBの保存／取得時に透過的に処理する
  - エンベロープ暗号
    - カラム暗号化の際に使う
    - 鍵を暗号化する鍵(KEK)とデータを暗号化する鍵(DEK)の２種類を使う
    - KEKをKMSで管理して、DEKはデータと一緒に保存
    
