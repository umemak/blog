---
title: "Prisma"
date: "2022-07-25"
tags: ["Prisma"]

---

[Prisma](https://www.prisma.io/)を使ってDB設計ってできるのかな、と思い調べてみた。

Prisma自体は、ORMということだけれど、スキーマファイルをもとにDBに対してマイグレーションで定義を反映できる。
モデル間の関連もスキーマファイルで表現できる。

でも、API側をOpenAPIやGraphQLで定義するとすると、似たようなものを管理しなくてはいけないのがちょっと。

GraphQLと組み合わせて使うこともできるようだけど、まだGraphQLへの苦手意識があるので試すまで至らない。
- [GraphQL with Database & Prisma | Next-Generation ORM for SQL Databases](https://www.prisma.io/graphql)

あと、[Prism | Open-Source HTTP Mock and Proxy Server | Stoplight](https://stoplight.io/open-source/prism)というOpenAPIから生成できるモックもあるので名前が紛らわしい。
