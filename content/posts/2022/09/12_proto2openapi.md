---
title: "protoをマスターにする"
date: "2022-09-12"
tags: ["go", "gRPC"]

---

protoをAPIスキーマのマスターにしようとした場合、既存のOpenAPIで用意していたUIとかどうしよう、ということになるけれど、OpenAPI->gRPCとは違って逆の変換はたくさんツールがあることは調査済み。

全体の作りとしては[grpc-gatewayでgRPCとREST両対応のサーバを作る | フューチャー技術ブログ](https://future-architect.github.io/articles/20220624a/)こんな感じにするのが良さそう。

ということでまずはマネするところからやっていきたい。
