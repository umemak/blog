---
title: "idとauto increment"
date: "2022-07-15"
tags: ["db"]

---

DB設計するときのIDカラムについて。

昔ながらのシステムだと、auto increment使って連番が定番だと思うのだけど、PocketBaseでCollectionにRecord追加したとき、idは`1ldTBeJNhX3jufu`みたいな文字列が割り振られていて、そういえばFirebaseもそうだったな、と。

最近は文字列をIDにするのがトレンドなのかな、と思いちょっと調べてみた。

- [idをautoincrementして何が悪いの？](https://zenn.dev/dowanna6/articles/3c84e3818891c3)
- [ID生成方法についてあれこれ](https://zenn.dev/j5ik2o/articles/a085ab3e3d0f197f6559)
- [MySQLでプライマリキーをUUIDにする前に知っておいて欲しいこと | Raccoon Tech Blog [株式会社ラクーンホールディングス 技術戦略部ブログ]](https://techblog.raccoon.ne.jp/archives/1627262796.html)

マイクロサービス化というかDBとAPIがネットワーク的に離れていたりして、レコードのinsertが終わるまでIDがわからない状態を嫌う場合は、リクエストを出す側でIDを生成してしまえば待つ必要がない、と。

auto incrementな連番の方が良い場合は、検索などのパフォーマンスを重視するとき。かな。
