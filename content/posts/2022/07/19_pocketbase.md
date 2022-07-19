---
title: "PocketbaseのCollections"
date: "2022-07-19"
tags: ["poketbase"]

---

コンテナで起動時にコレクションを作成したい時のやり方が見つからない。

MySQLとかだと、`/docker-entrypoint-initdb.d`にSQLを置いておけば実行してくれる、そういうやつ。

→[DB migrations - Docs - PocketBase](https://pocketbase.io/docs/db-migrations/)

Pocketbaseの起動時に初期化するのではなく、利用するアプリ側でマイグレーションを実行する方式らしい。

https://github.com/pocketbase/pocketbase/blob/73fb12c2bca57be504712ed169ce5a0dc95e7b2c/migrations/1640988000_init.go#L38-L47

こんな感じでCREATEを書いていけば良いっぽいけど、、書式がなんか知ってるSQLと違う。。
