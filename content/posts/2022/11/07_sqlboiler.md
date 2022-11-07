---
title: "SQLBoiler"
date: "2022-11-07"
tags: ["go"]

---

[volatiletech/sqlboiler: Generate a Go ORM tailored to your database schema.](https://github.com/volatiletech/sqlboiler)を少し触ってみた。

普段は[kyleconroy/sqlc: Generate type-safe code from SQL](https://github.com/kyleconroy/sqlc)をよく使っているのだけれど、あらかじめSQLを書かなくて良いのは楽。

だけど結局DB操作するときには対象のレコードを指定するのに組み立てないといけないので、一長一短。

手段を一つしかもっていないと、それがダメになったときに詰んでしまうが、複数選択肢があれば柔軟に対応できるので、色々知っておくのは大事だと思う。
