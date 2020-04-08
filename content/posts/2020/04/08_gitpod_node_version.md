---
title: "Gitpodのnodeバージョンを変更する"
date: "2020-04-08"
tags: ["node", "gitpod"]
---

https://github.com/zeit/next.js/tree/master/examples/with-firebase-hosting-and-typescript
これを動かしたくて、

```
$ yarn create next-app --example with-firebase-hosting-and-typescript with-firebase-hosting-and-typescript-app
```
したところ、`The engine "node" is incompatible with this module. Expected version "10". Got "12.16.1"`というエラーで正常終了しない。バージョン10系を要求されているのに、インストールされているのは12系。

```
$ nvm install 10
```
を実行することで、10系になる。
