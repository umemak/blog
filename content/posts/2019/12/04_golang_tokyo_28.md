---
title: "golang.tokyo #28"
date: "2019-12-04"
tags: ["event", "golang"]
thumbnail: "https://connpass-tokyo.s3.amazonaws.com/thumbs/86/d4/86d4cfcbc4f2eafd41a40f332ef2716e.png"
---

https://golangtokyo.connpass.com/event/156678/

LT大会（１６本！）です。

## 19:00 ~	開場・受付
{{<tweet 1202169265698131968>}}

## 19:30 ~ 19:40	オープニング・乾杯
* yappli

## 19:40 ~ 19:45	LT1: [仮]wire.goをプロダクトで使ってみた
### bieshanさん
* DIツール
  - 依存関係のコードを生成してくれる
* wire使い方イマイチ理解していないので助かる
* 型を見て生成しているので、同じ定義だとどちらを使っていいか判断できない
  - 型の名前を変えれば良い
  - 内部まで書き換えに行く？
    - 構造体でラップしてあげれば良い

## 19:45 ~ 19:50	LT2: 作業効率アップ！便利なTUIツール5選
### ゴリラさん
* https://speakerdeck.com/gorilla0513/zuo-ye-xiao-lu-atupu-osusumetuituru5xuan
* lazygit
* docui
* pst
* ff
* tson

## 19:50 ~ 19:55	LT3: Twitter を自由自在にフィルタリングする Twilter を作った
### kawasin73さん
* tweetbotおすすめ
* フィルタした結果をRTするBOT
* 鍵垢（BOT）でRTしてそれをフォローしておく運用
  - 鍵垢じゃないとRTするたびに相手に通知が飛ぶ

## 20:00 ~ 20:05	LT5: go toolを使ってインライン展開をのぞいてみる(仮)
### tutuzさん
* objdump（標準ツール）で逆アセンブリできる
* インライン展開しない場合の実行コスト
  - ５倍くらいになる場合もある
* 複雑なものは展開されない

## 20:05 ~ 20:10	LT6: Markdown内のコードだって美しくしたいんだ！！
### po3rinさん
* https://speakerdeck.com/po3rin/i-want-to-make-the-code-in-markdown-beautiful
* mdを構文解析して処理している
* 舌打ちはアイデアになる

## 20:10 ~ 20:15	LT7: gRPC周りで困ったこととその解決方法
### Go Sagawaさん
* https://docs.google.com/presentation/d/1bmTIrdgyi3E-bK3r7KHpsOFXDQOZoZVz6oXi7iSFPsw/edit#slide=id.g33148270ac_0_143
* protoの扱い
* 抽象化が難しい
* 構造化を考える
* clang-format でフォーマットできる
* 実装する前にレビューするの大事
* grpc-gatewayを使うと、ミドルウェアがかけるので良い

## 20:15 ~ 20:20	LT8: (仮)初めてGoで開発してみて思ったこと
### rkmathiさん
* 言語使用や書き方はわかった、実際のアプリケーションはどう書くのか
* Gopher道場

## 20:30 ~ 20:35	LT9: [仮]keepAliveのすゝめ
### Shogo_Tomiokaさん
* http.TansPortで設定できる
  - デフォルト有効
* tcnksm/go-httpstat
* res.Body.Close() しないと使い回せない
* パラメータはアプリケーションの特性を考えて調整する

## 20:16 ~ 20:26	休憩

## 19:55 ~ 20:00	LT4: Write Kubernetes Custom Controller in Go
### morito_ikedaさん


## 20:35 ~ 20:40	LT10: マイクロサービスで共用するprivateなエラー&ロギングパッケージを作った
### Shohei O.さん


## 20:40 ~ 20:45	LT11: gRPCのクライアントが絡むテスト
### dice_zuさん


## 20:45 ~ 20:50	LT12: Repositoryによる抽象化の理想と現実
### sonatardさん


## 20:50 ~ 20:55	LT13: インフラエンジニアもGolangが書きたい
### nwiizoさん


## 20:55 ~ 21:00	LT14: 年末なのでgoを使ったプロダクトを初めてリリース・運用した1年を振り返ってみる
### keitaro_1020さん


## 21:00 ~ 21:05	LT15: Transform Go error handling using AST inspector
### Hidetake Iwataさん


## 21:05 ~ 21:10	LT16: Go基礎力に効く標準ライブラリContext徹底理解。あなたはContextの挙動を説明できますか？
### shibu_jpさん


## 21:10 ~ 21:35	懇親会

## 21:35 ~ 21:45	結果発表

## 21:45 ~ 21:55	終了・撤収
