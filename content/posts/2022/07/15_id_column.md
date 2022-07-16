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

PocketBaseのIDは、UUIDとかではなくランダム文字列らしい。

- https://github.com/pocketbase/pocketbase/blob/3d07f0211dc74710affd9154f61728d77cfb6f4c/models/base.go#L65-L67
- https://github.com/pocketbase/pocketbase/blob/3d07f0211dc74710affd9154f61728d77cfb6f4c/tools/security/random.go#L11-L21

(could change in the future)とコメントに書かれているので、将来的には変わるかも。
