---
title: "PocketbaseのMigration"
date: "2022-07-20"
tags: ["poketbase"]

---

昨日、Migratinが用意されているのを知って、試してみたけれど思ったように動かず。

マイグレーションにしか使わないパッケージもいくつかimportが必要だし、明示的に`migrate up`しないといけない。

であれば、普通にHTTP APIでCreate Collectionしても良いかなという気持ちになっている。

ただ、Admin権限じゃないとCreate Collectionは使えないので、そこが面倒という気持ちもある。
