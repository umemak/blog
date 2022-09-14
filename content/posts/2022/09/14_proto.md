---
title: "proto"
date: "2022-09-14"
tags: ["go", "gRPC"]

---

昨日のエラーは、[grpc-ecosystem/grpc-gateway: gRPC to JSON proxy generator following the gRPC HTTP spec](https://github.com/grpc-ecosystem/grpc-gateway)にあるように`buf.yaml`に
```
deps:
  - buf.build/googleapis/googleapis
```
を追記して`buf mod update`を実行したら直ったような気がする。

気がする、というのは他にもprotoファイルをダウンロードしてきたりとかいろいろやっていて何が決定打だったのかよくわかってない。

結果オーライ。
