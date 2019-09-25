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
* Dialogflow?

## 20:30 ~ 21:00	休憩
* と言う名の懇親会タイム

## 21:10 ~ 21:20	LT1 Raspberry Pi + Go で IoT した話 (仮) by yaegashi

## 21:20 ~ 21:30	LT2 Goを使ったセンサーデータ収集基盤のお話(仮 by takeshinoda

## 21:30 ~ 21:40	LT3 Build real world data collecting architecture with goroutine & channel by banana_umai

## 21:40 ~ 21:50	終了・撤収
