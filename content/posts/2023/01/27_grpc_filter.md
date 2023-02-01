---
title: "einride/aip-go使ってみる"
date: "2023-01-27"
tags: ["gRPC"]

---

[filtering package - go.einride.tech/aip/filtering - Go Packages](https://pkg.go.dev/go.einride.tech/aip/filtering)

を使おうとしてみたけれど、よくわからない。

[aip-go/parser_test.go at master · einride/aip-go](https://github.com/einride/aip-go/blob/master/filtering/parser_test.go)を見て、まずInitに文字列渡して、ParseでExprが作られるのはわかった。
そのExprをWarkで見て回るところができず。

とりあえず、入力パターンを制限してstrings.Splitとかでしのいでおく。
