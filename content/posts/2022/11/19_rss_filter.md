---
title: "RSSフィルタ"
date: "2022-11-19"
tags: ["RSS"]

---

[mmcdole/gofeed: Parse RSS, Atom and JSON feeds in Go](https://github.com/mmcdole/gofeed)を使ったら、RSSの読み込みが超簡単にできた。

が、不要なエントリを削除してまたRSSとして出力しようとしたときに、手段が用意されていなさそう。

なので、`encoding/xml`を使って作るのが良さそう。

- [Goのencoding/xmlの使い方について雑に紹介](https://zenn.dev/nnabeyang/scraps/a1429f7f1214e9)
- [Go言語 - XMLを読んで特定の要素を削って出力 - 覚えたら書く](https://blog.y-yuki.net/entry/2017/07/02/120000)

この辺りが参考になりそう。
