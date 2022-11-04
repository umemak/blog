---
title: "SWR使ってみた"
date: "2022-11-04"
tags: ["swr", "next.js"]

---

前から気になっていたけど使う機会がなかった[データ取得のための React Hooks ライブラリ – SWR](https://swr.vercel.app/ja)を使ってみた。

[SWRを使おうぜという話2022](https://zenn.dev/mast1ff/articles/5b48a87242f9f0)を参考にやったら参照は簡単に実装できた。

GitpodでフロントとAPIが別ポートだとCORS問題とかそもそもポートを公開しないと到達できないとかあったけど、APIサーバーのCORS設定してAPI側のポート公開にしたらいけた。

更新系もできるようなので、それもやってみたい。
