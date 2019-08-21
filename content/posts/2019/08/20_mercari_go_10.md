---
author: "umemak"
date: 2019-08-20
title: mercari.go #10
---

# mercari.go #10
https://mercari.connpass.com/event/141122/

## 19:40 ~	morikuni	GopherCon 2019
* GopherConとは
  - 2014年デンバーで始まった。いろんなところでやっている。
  - 今年はサンディエゴで開催
    - 1800人を超える参加者
* Mercariの関わり
  - Silver Sponsor
  - BOLD Scholarship
    - 学生向け
  - 11+2名参加
* １日目はワークショップ
* ２日目３日目は発表がメイン
* ４日目はコミュニティデイ
  - LTとか
* One MOre Thing
  - Generics(Contracts)
  - Interfaceとの違い
    - 直和型

## 19:50 ~	mark.hahn	Workshop: Go-Beginner Training
* 英語の発表だけど聞き取りやすかった
* Goは1日で習得できる（シンプル）

## 20:00 ~	micnnicim	How Uber Goes
* 1500サービス、200M行がGoで書かれている
* MONOREPOへの移行
* [uber-go/fx](https://github.com/uber-go/fx)
  - アプリケーションフレームワーク
* glue
  - 非公開ライブラリ
  - クリーンアーキテクチャ
* [Bazel](https://bazel.build/)
  - OSSのビルドツール
  - monorepoに効く？

## 20:15 ~	upamune	How I Write HTTP Web Services After Eight Years
* Mat Ryer
  - https://gopherize.me/
  - https://medium.com/statuscode/how-i-write-go-http-services-after-seven-years-37c208122831
* Maintainability
  - 最初から考えて作る
* Glaceability
  - 視認性
  - 理解しやすさ
* Code shuld be boring
  - 
* Self Similar code
  - コード内に似たコードがあると親しみやすくなる

## 20:25 ~	taqboz	TinyGo
* Small is going big
* LLVMを使ったGoコンパイラ
* WebAssembly対応
* Goroutineのサポートが不完全
* 使えない標準パッケージが多い（net系全滅）
* IoTデバイス、マイクロコントローラーでの活用
* Drone飛ばすデモ

## 20:40 ~	hunter	PKI for Gophers
* 暗号化の話
* Hardware Keys
  - YubiKey

## 20:50 ~	yuki.ito	Workshop: Observability in Go & Socket to me: Where do Sockets live in Go? 
* 資料
  * https://speakerdeck.com/110y/my-favorite-talks-at-gophercon-2019
  * https://github.com/freeformz/go-observability-workshop/ 
  * https://github.com/110y/sockoptgo/
* Observability
  - Log
    - logrus 構造化出力できる
  - Metric
    - expvar
    - Prometheus
  - Trace
    - Jaeger
* Socket Option

## Go Quiz
* 型厳密なのな。。
