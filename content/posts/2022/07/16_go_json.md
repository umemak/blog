---
title: "GoのJSON"
date: "2022-07-16"
tags: ["Go"]

---

PocketBaseのユーザー作成をGoからHTTP叩いて実行しようとして、正常時とエラー時で戻ってくるJSONの形式が違っていた。

structを別々に用意して、Unmarshalでエラーになったらもう片方を使う？とか思ったけど、
[golang は ゆるふわに JSON を扱えまぁす! — KaoriYa](https://www.kaoriya.net/blog/2016/06/25/)によると、`interface{}`（Go1.18以降なら`any`か）を使えば、structを事前に用意する必要がないと。

- [koron/go-dproxy: dProxy - document proxy](https://github.com/koron/go-dproxy)
- [mattn/go-jsonpointer](https://github.com/mattn/go-jsonpointer)

が紹介されていて、指定の仕方がわかりやすそうな go-jsonpointer を使ってみることにした。

そもそも、PocketBaseがエラーでもHTTPステータスコード200を返してくるのを変えるようにすれば良いのか？？
