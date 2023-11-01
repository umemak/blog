---
title: "SST入門"
date: "2023-11-01"
tags: ["Serverless", "SST"]

---

SvelteKitをAWSのLambdaで動かす方法を探していて、[ゼロコンフィグデプロイ • Docs • SvelteKit](https://kit.svelte.jp/docs/adapter-auto)で[Use SvelteKit with SST | SST](https://docs.sst.dev/start/svelte)が紹介されていた。

SSTってSega Sound Teamしか知らないけど、Serverless Stackの略らしい（Tはどこから？）。

で、ドキュメントに沿って動かしてみたら、いい感じにデプロイできた。

が、[Prisma](https://www.prisma.io/)を使ったツールをデプロイしたら

> "PrismaClientInitializationError: Prisma Client could not find its `schema.prisma`. This is likely caused by a bundling step, which leads to `schema.prisma` not being copied near the resulting bundle. We would appreciate if you could take the time to share some information with us.",

といったエラーになってしまった。[Prisma not working with sst monorepo · Issue #18570 · prisma/prisma](https://github.com/prisma/prisma/issues/18570)と同じ現象かな？

Prismaを使わない構成にしたほうが良いのか、SSTを使わない（＝Lambdaもあきらめ）構成にするか。
