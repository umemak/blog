---
title: "airのオプション"
date: "2022-08-03"
tags: ["air"]

---

[cosmtrek/air: ☁️ Live reload for Go apps](https://github.com/cosmtrek/air)で、コマンドラインでオプション指定できるみたいだけど、思ったように動かないな・・という内容で書こうとして見直してたら、`beta feature`ってちゃんと書いてあるし。

エラーになったり、完全に動かないわけではなく、`build.cmd`とか指定が効いてたので気づかなかった。

モノレポで使うときに、共通の部分は`.air.toml`に書いておいて、異なるところだけコマンドラインで指定できるとうれしい。
