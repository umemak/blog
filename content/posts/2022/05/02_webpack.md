---
title: "webpackで構築"
date: "2022-05-02"
tags: ["JavaScript","webpack"]

---

昨日は、TypeScript環境構築に手間をかけたくないという想いでParcelを試してみたところ、エラーで途方に暮れていた。

今日は、古き良きwebpackを試した。

参考にしたページはこちら
- [最新版TypeScript+webpack 5の環境構築まとめ(React, Vue.js, Three.jsのサンプル付き) - ICS MEDIA](https://ics.media/entry/16329/#webpack-ts)

```sh
$ npm init -y
$ npm i -D webpack webpack-cli typescript ts-loader
$ code package.json
$ code tsconfig.json
$ code webpack.config.js
$ code src/main.ts
$ npm run build
> mdmml_js@1.0.0 build /home/umemak/workspace/mdmml_js
> webpack

asset main.js 1.2 KiB [emitted] (name: main)
./src/main.ts 14 bytes [built] [code generated]
webpack 5.72.0 compiled successfully in 1126 ms
```
できた。
楽をしようとしてかえって遠回りになった経験だった。
