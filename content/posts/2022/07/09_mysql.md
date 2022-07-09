---
title: "adminer"
date: "2022-07-09"
tags: ["mysql"]

---

MySQLコンテナ作ろうと思って、[Mysql - Official Image | Docker Hub](https://hub.docker.com/_/mysql)のcompose書き方見てたら、adminerというイメージを使っていて、同様に起動してみたらなかなか良い。

元のプログラムは[dockette/adminer: Tiniest boxed dockerized Adminer (MySQL, PostgreSQL, SQLite, Mongo, Oracle) Dockerfiles](https://github.com/dockette/adminer)かな。

テーブル定義作るときに、カラム名を別のテーブル名+idにしたら、自動で外部キー定義として認識してくれてすごい。
