---
title: "TypeScriptで標準出力"
date: "2022-05-05"
tags: ["TypeScript", "mdmml"]

---

マークダウンから変換したSMFデータを標準出力に書き出したいのだけれど、バイナリをそのまま出力する方法がわからず。。

`console.log`だと型情報とかついた普通のテキストになってしまう。
```sh
$ node dist/main.js
Uint8Array(45) [
  77,  84, 104, 100,  0,   0,   0, 6, 0,   1,  0,
   1,   3, 192,  77, 84, 114, 107, 0, 0,   0, 23,
   0, 255,   3,   0,  0, 255,  81, 3, 7, 161, 32,
   0, 255,  88,   4,  4,   2,  24, 8, 0, 255, 47,
   0
]
```

`fs`パッケージを使おうとしたけれど、`Module not found: Error: Can't resolve 'fs'`などと言われてbuildできず。

こういう本質的でないところで詰まるのほんとやめてほしい。

追記：これでできた。
```js
console.log(Buffer.from(MDtoSMF("cdefg")).toString("binary"));
```
