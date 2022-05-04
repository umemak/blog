---
title: "TextEncoderのエラー"
date: "2022-05-04"
tags: ["TypeScript"]

---

replaceAllを使いたくて、tsconfig.jsonに以下設定を追加した。
```
    "lib": [
      "ES2021.String"
    ]
```

replaceAllが使えるようになったが、TextEncoderを使っているところでエラーになるようになってしまった。
```
error TS2304: Cannot find name 'TextEncoder'.
```
定義がないのか？と思って[@types/text-encoding - npm](https://www.npmjs.com/package/@types/text-encoding)にあるとおり追加してみた。
```
npm install --save @types/text-encoding
```
別のエラーが出るようになった。
```
error TS2304: Cannot find name 'TextEncoder'.
```
未解決。
