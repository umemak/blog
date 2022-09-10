---
title: "gRPCを触ってみる"
date: "2022-09-10"
tags: ["go", "gRPC"]

---

gRPCを触ってみたくなったので、[gRPCがフロントエンド通信の第一の選択肢になる時代がやってきたかも？ | フューチャー技術ブログ](https://future-architect.github.io/articles/20220819a/)をやってみる。

frontendでnpm installするところでgitエラーになってしまう。
```sh
$ npm install --save-dev bufbuild/protoc-gen-connect-web bufbuild/protoc-gen-es
npm ERR! code 128
npm ERR! An unknown git error occurred
npm ERR! command git --no-replace-objects ls-remote ssh://git@github.com/bufbuild/protoc-gen-connect-web.git
npm ERR! git@github.com: Permission denied (publickey).
npm ERR! fatal: Could not read from remote repository.
npm ERR! 
npm ERR! Please make sure you have the correct access rights
npm ERR! and the repository exists.
```

とりあえず置いておいて先に進めるが、結局buf generateするところで出力先がないのでエラーになってしまった。

frontendとAPIサーバー一つにまとまられると、PocketBase見たいで良いなーと思ったんだけど、残念。

その後、
```sh
$ npm install --save-dev bufbuild/protoc-gen-connect-web bufbuild/protoc-gen-es
```
これを
```sh
$ npm install --save-dev @bufbuild/protoc-gen-connect-web @bufbuild/protoc-gen-es
```
こうしたらエラー解消できた。

あと
```sh
$ npm install @bufbuild/connect-web
```
も必要っぽい。

