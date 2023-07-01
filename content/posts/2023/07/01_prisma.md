---
title: "Prisma"
date: "2023-07-01"
tags: ["Prisma"]

---

[TypeScript ORM「Prisma」のはじめかた - くらげになりたい。](https://www.memory-lovers.blog/entry/2021/10/13/113000)を見て、DBマイグレーション管理としてのPrismaを試してみた。

既存のDBスキーマを`prisma pull`で持って来られるというのを試したら、boolがtinyintになってしまうなどあったが、そこそこいい感じにできた。
