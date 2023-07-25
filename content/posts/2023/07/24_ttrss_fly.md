---
title: "Tiny Tiny RSSをfly.ioにデプロイ（失敗）"
date: "2023-07-25"
tags: []

---

[serl/ttrss-fly](https://github.com/serl/ttrss-fly)を試してみた。

`flyctl deploy`のところでエラーになってしまう。

ログを見ると、DBへの接続でエラーになっているように見える。

> psql: error: invalid connection option "アプリ名?sslmode"

DB接続文字列は、`flyctl postgres attach --app $PREFIX-ttrss $PREFIX-db`で設定されているので問題ないと思うのだけど。

コマンドラインから変更してみようと思ったけど、変更するにはアプリのコンテナが起動する必要があるらしく、コンテナ起動時にエラーが出ているので変更できない。ように見える。

ちょっとよくわからないのでfly.ioで動かすのはあきらめて、OCI試してみようかな。
