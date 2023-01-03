---
title: "Fly.io"
date: "2023-01-03"
tags: ["Fly.io"]

---

IBM Cloudが使えないので、[Deploy app servers close to your users · Fly](https://fly.io/)を試してみた。

Fly.ioあまり聞いたことなかったけど、Heroku的な立ち位置らしい。

[Fly.io for self hosting CouchDB · Discussion #85 · vrtmrz/obsidian-livesync](https://github.com/vrtmrz/obsidian-livesync/discussions/85#discussion-4186670)の通りにやっていたたら、あっさり動いた。

一か所、`6. Create data volume`のところのコマンドが`fly`だったのを`flyctl`にする必要があった。

で、Self-hosted LiveSyncプラグインが使えるようになったけれど、モバイルの同期がやっぱり時間かかる。ファイル数は1200弱だけど、1ファイル1秒くらいかかってる印象。
