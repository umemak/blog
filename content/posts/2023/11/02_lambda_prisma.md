---
title: "LambdaとPrisma"
date: "2023-11-02"
tags: ["Lambda", "Prisma"]

---

昨日、SSTでデプロイしてエラーになったので、[yarbsemaj/sveltekit-adapter-lambda: An adapter to build a SvelteKit app into a lambda ready for deployment with lambda proxy via the Serverless Framework.](https://github.com/yarbsemaj/sveltekit-adapter-lambda)を試してみた。

結果としては、やはりPrismaのエラーで落ちていた。

ひとまずLambda諦めて動くものを作るのを優先しよう。
