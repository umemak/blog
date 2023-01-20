---
title: "gRPC Connect"
date: "2023-01-20"
tags: ["go", "gRPC"]

---

[bufbuild/connect-go: Simple, reliable, interoperable. A better gRPC.](https://github.com/bufbuild/connect-go)

テスト用にgRPCのサーバーが欲しかったので、使ってみた。

READMEに書いてあるサンプルのように作ったら、grpcurlでリフレクションのエラーになったので、[次世代gRPC?『connect-go』やってみた](https://zenn.dev/rai_wtnb/articles/e07ad831ea8e34)を参考にリフレクションを入れたら動いた。

ついでにクライアントもConnectで書いてみた。

サーバーの指定をプロトコル込み（http://～/）で指定しないといけないのと、RequestとResponceにMsgを挟まないといけないので少しハマったけど、おおむね問題なさそう。
