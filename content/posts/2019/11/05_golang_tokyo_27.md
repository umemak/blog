---
title: "golang.tokyo #27"
date: "2019-11-05"
tags: ["golang", "event"]
---

https://techplay.jp/event/753881

先日のGo Conferenceには参加できなかったので、当選できてよかった。
{{< figure src="../IMG_20191105_193605_1573015343606.jpg" title="" class="center" width="640" >}}

## 19:00 ~	開場・受付
{{< figure src="../IMG_20191105_193759_1572967448087.jpg" title="乾杯！" class="center" width="640" >}}

## 19:30 ~ 19:35	オープニング
* DevQuizの解説。思ってた動作と違かった。。
* 当日発表になった登壇者とスケジュール。予定より本数が少なくなっていました。
  {{< figure src="../IMG_20191105_194058_1573015274227.jpg" title="" class="center" width="640" >}}


## 19:35 ~ 19:55	Session 1
### Creating shell magager with golang / Yusuke Komatsu
* https://speakerdeck.com/usk81/create-shell-manager-with-golang
* shway
  - https://github.com/getshway/shway
* dotfileの管理方法のベストプラクティスを模索
* home brew
* 開発環境のシェアができる？
* 子プロセスで読んだコマンドの結果が親プロセスに反映されない
  - 標準出力に吐いて親で読み込む
* ログを出してしまうと、親に読まれてしまう
  - STDERRに出す
* go-git
  - オススメのgitライブラリ
* 未完成

## 19:55 ~ 20:15	Session 2
### Multi Cloud Serverless Architecture / 渋川さん
* https://docs.google.com/presentation/d/1x4Ed-sYP-7oJntGQ0hiUozbx-ys7yJfYI-_S62RtP60/edit
* サーバーレスの話
* Go Cloudで実現できる？
* AWSとGCP（Go対応）で実験
  - ローカルでも動かせる
* GCPとAWSの違い
  - CGP: ソースをアップ、AWS: バイナリをアップ
  - エントリポイントの形式も違う
    - コードジェネレータを作ってカバー
* chi router
  - https://github.com/go-chi/chi
* docstore
  - https://gocloud.dev/howto/docstore/
  - DynamoDB, Firestore, CosmosDB のアクセスを抽象化するライブラリ
  - ローカルで mongodocstore というインメモリ環境もあり
* まとめ
  - マルチクラウドサーバーレスアプリケーションの実現は可能
  - Go Cloud良い

## 20:20 ~ 20:35	休憩


## 20:35 ~ 20:55	Session 3
### uber-go/guide の解説 / かまたさん
* https://docs.google.com/presentation/d/10H6tvkVG2Qb9DNeSITAiKP-5BJKHqwnWFRCxEQYbpYQ/edit#slide=id.p
* Uber社内で使われているスタイルガイド
  - https://github.com/uber-go/guide
* ガイドライン / パフォーマンス / スタイル / パターン
* Be Consistent
  - 可読性、保守性のためにコードの一貫性を保ちましょう
* linter
  - go vet, goimports, golangci-lint
  - ulinter 作成中
* Handle Tpe Assertion Failures
  - 型アサーションの結果をハンドリングしているかチェック
* linterの作り方
  - ASTを作ってパターンを見ていく
* Start Enums as One
  - enumのゼロ(iota)は、初期化(goのデフォルト初期値)しただけなのか明示的に設定したのか区別しにくいため
* Converting number to string
  - fmt.Printfよりstrconvパッケージを使ったほうがパフォーマンス有利なので

## 20:55 ~ 21:00	LT1
### SaaS関連系における静的解析の活用 / Yohei Miyamoto
* https://go-talks.appspot.com/github.com/yoheimiyamoto/talks/golang-tokyo/27/talk.slide#1
* SaaS関連系の条件をカスタマイズできるようにしてみた話

## 21:00 ~ 21:50	終了・撤収
