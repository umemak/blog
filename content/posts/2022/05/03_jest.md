---
title: "Jestの導入"
date: "2022-05-03"
tags: ["JavaScript","Jest"]

---

ブラウザからの動作確認はいったん置いておいて、コマンドライン実行で動くものを目指す。

どうせなら自動テストも動かしながらやっていきたい。

JavaScriptのテストフレームワークは、[Jest · 🃏 Delightful JavaScript Testing](https://jestjs.io/ja/)が主流らしいので、それに乗っかる。

[Typescriptでの単体テストの書き方(Jest) | スターフィールド株式会社](https://sterfield.co.jp/blog/development/%E3%83%97%E3%83%AD%E3%82%B0%E3%83%A9%E3%83%A0/typescript%E3%81%A7%E3%81%AE%E5%8D%98%E4%BD%93%E3%83%86%E3%82%B9%E3%83%88%E3%81%AE%E6%9B%B8%E3%81%8D%E6%96%B9jest/)を見ながらインストール。

```sh
$ npm install --save-dev jest typescript ts-jest @types/jest
$ npx ts-jest config:init
$ code jest.config.js
$ code package.json
$ npm run test
ts-jest[versions] (WARN) Version 28.0.3 of jest installed has not been tested with ts-jest. If you're experiencing issues, consider using a supported version (>=27.0.0 <28.0.0-0). Please do not report issues in ts-jest if you are using unsupported versions.
ts-jest[config] (WARN) message TS151001: If you have issues related to imports, you should consider setting `esModuleInterop` to `true` in your TypeScript configuration file (usually `tsconfig.json`). See https://blogs.msdn.microsoft.com/typescript/2018/01/31/announcing-typescript-2-7/#easier-ecmascript-module-interoperability for more information.
```

jestとts-jestのバージョンが不一致らしい。
```sh
$ npm install -D jest@27
```
あとtsconfigにesModuleInteropを設定が必要らしい。

```sh
$ npm run test

> mdmml_js@1.0.0 test
> jest

 PASS  src/mdmml.test.ts
  ✓ number (1 ms)
  ✓ not number (1 ms)

Test Suites: 1 passed, 1 total
Tests:       2 passed, 2 total
Snapshots:   0 total
Time:        1.382 s, estimated 2 s
Ran all test suites.
```
できた。

けど、テスト対象の関数exportしないとダメなの？
