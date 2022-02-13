---
title: "goldmarkを読む"
date: "2022-02-13"

---

難解だと思って避けていたASTを直接見れば、goqueryを使わなくてもよいのでは？と思ってgoldmarkのソースを眺めてみた。

rendererの[html.go](https://github.com/yuin/goldmark/blob/master/renderer/html/html.go)が参考になると思うんだけど、なかなか長大な感じ。
[RegisterFuncs](https://github.com/yuin/goldmark/blob/master/renderer/html/html.go#L162)で各要素ごとの処理を登録していけばよいのかな。

うーん。変換結果としてASTを取る方法がわからぬ。HTMLになってしまう。
もしかして、extensionとして書かないといけない？
となるとちょっと大変そうだなぁ。。
