---
title: "sqlc"
date: "2022-07-28"
tags: ["Go", "DB"]

---

別の調べものをしていて見つけた[sqlc.dev | Compile SQL to type-safe Go](https://sqlc.dev/)を試してみた。

`schema.sql`は、今までMySQLの起動時に読み込ませていたSQLファイルがそのまま使えた。

`query.sql`もgoのmodelパッケージ内に書いていたSQLをコピペで作れた。

結構良いかも。
