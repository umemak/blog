---
title: "Prism使ってみた"
date: "2022-12-08"
tags: ["OpenAPI"]

---

APIサーバーのモックを手っ取り早くほしかったので[stoplightio/prism: Turn any OpenAPI2/3 and Postman Collection file into an API server with mocking, transformations and validations.](https://github.com/stoplightio/prism)を試してみた。

POSTのレスポンスがexample指定してるはずなのに、空で返ってきてよくわからない。

モック対象がそんなに多くなかったから、とりあえずgoで組んだ。

これだとサーバー側の仕様変更に追従できないから、時間あるときに解決したい。
