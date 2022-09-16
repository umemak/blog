---
title: "OpenAPIで生成したサーバーのテスト"
date: "2022-09-16"
tags: ["go", "OpenAPI"]

---

よくわからない。

ググるとhttptest使う例が良く出てくるけど、型が合わなくて組み立てられない。

仕方ないので、APIサーバー起動してhttp.NewRequestWithContextで叩いて結果を見るという、E2Eっぽいテストに落ち着きそう。
