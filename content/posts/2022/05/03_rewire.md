---
title: "rewireでjest"
date: "2022-05-03"
tags: ["JavaScript","rewire","jest"]

---

テストのために関数exportしないといけないの、チョット気持ち悪いので、解決策を探ってみる。

[jhnns/rewire: Easy monkey-patching for node.js unit tests](https://github.com/jhnns/rewire)が一般的らしい。

```sh
$ npm install -D rewire @types/rewire
```

テストコードのimportを修正
```ts
import rewire from 'rewire';

const __local__ = rewire('./mdmml.ts');
const atoi = __local__.__get__('atoi')
```

テスト実行
```sh
$ npm test

> mdmml_js@1.0.0 test
> jest

 FAIL  src/mdmml.test.ts
  ● Test suite failed to run

    /home/umemak/workspace/mdmml_js/src/mdmml.ts:8
        Tracks: Track[] = [];
        

    SyntaxError: Unexpected identifier

      at Object.load (node_modules/rewire/lib/moduleEnv.js:57:18)
      at internalRewire (node_modules/rewire/lib/rewire.js:49:15)
      at rewire (node_modules/rewire/lib/index.js:11:12)

Test Suites: 1 failed, 1 total
Tests:       0 total
Snapshots:   0 total
Time:        1.01 s
Ran all test suites.
```

関係ないところでエラーになるようになってしまった。。

面倒なのでとりあえずexportする方向で。
