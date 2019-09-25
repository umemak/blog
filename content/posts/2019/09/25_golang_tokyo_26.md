---
title: "golang.tokyo #26"
date: "2019-09-25"
tags: ["golang","event"]
---

https://golangtokyo.connpass.com/event/147175/

* 今回はスマートホームとGoの話です

## 19:30 ~ 20:00	Go in Nature（仮） by songmu]
* Nature Remoの裏側
* gocredits オススメ
  - 依存ライブラリのLICENSEを同梱してくれる
* ecsched気になる
* Websocketでクラウドに接続しっぱなしにしている
* 外部のデバイスからはクラウドに司令を出す
* 常時接続の管理が大変
* ECS上でうごかしている
* Nginxとポート数の問題
  - 接続数が少ないところにつなぎに行く
  - ALBに直接つなぎに行けるようにしたい
* deploy時に接続を切るので、その後一斉に再接続が来る
* Migration
  - goose から schemalex に乗り換えたい
* Dependabot 導入
  - Go対応はちょっと微妙

## 20:00 ~ 20:30	Nature Remo用のGo API Clientを作った話（仮） by tenntenn
* 完全に対応したGoクライアントが存在していなかったので作った
* swagger見ながら作った
* Dialogflowも使いたい

## 20:30 ~ 21:00	休憩
* と言う名の懇親タイム

## 21:10 ~ 21:20	LT1 Raspberry Pi + Go で IoT した話 (仮) by yaegashi
* エッジデバイスでの活用
* クロスコンパイルが簡単
* シングルバイナリ
* 並列処理のサポート
* GPIOの制御
  - pigpioが便利
  - 遅延、CPU負荷が弱点
  - periph.ioもオススメ

## 21:20 ~ 21:30	LT2 Goを使ったセンサーデータ収集基盤のお話(仮 by takeshinoda
* IoTでGoは便利
  - クロスコンパイル、非同期データ通信制御、デプロイの容易さ
  - 非同期処理と同期処理の混在もOK
* nodeとGo、Goのほうが安心感がある

## 21:30 ~ 21:40	LT3 Build real world data collecting architecture with goroutine & channel by banana_umai
* pipeline pattern
  - channelで並列にデータ受け渡しをしていくパターン
  - データの順序性、即時性を保ちたい
* debouncing, buffering
  - ネットワークの不安定さに対応できる
