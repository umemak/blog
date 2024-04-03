---
title: "Windowsでbunを試す"
date: "2024-04-03"
tags: ["bun"]

---

[Bun — A fast all-in-one JavaScript runtime](https://bun.sh/)

v1.1でWindowsにも対応したということなので、Surface go 2で試してみた。

```
$ bun create next-app
√ What is your project named? ... bun-next-app
√ Would you like to use TypeScript? ... No / Yes
√ Would you like to use ESLint? ... No / Yes
√ Would you like to use Tailwind CSS? ... No / Yes
√ Would you like to use `src/` directory? ... No / Yes
√ Would you like to use App Router? (recommended) ... No / Yes
√ Would you like to customize the default import alias (@/*)? ... No / Yes
√ What import alias would you like configured? ... @/*
```

```
$ cd bun-next-app/
$ bun --bun run dev
$ next dev
   ▲ Next.js 14.1.4
   - Local:        http://localhost:3000

 ✓ Ready in 9.1s
 ○ Compiling / ...
```
で終了して、終了できない枠だけのターミナルが起動した。

npmだと普通に起動したので、bunに原因がありそう。
```
$ npm run dev

> bun-next-app@0.1.0 dev
> next dev

   ▲ Next.js 14.1.4
   - Local:        http://localhost:3000

 ✓ Ready in 9.1s
 ○ Compiling / ...
 ✓ Compiled / in 14.1s (511 modules)
 ✓ Compiled in 1708ms (241 modules)
 ○ Compiling /favicon.ico ...
 ✓ Compiled /favicon.ico in 13.6s (523 modules)
```
