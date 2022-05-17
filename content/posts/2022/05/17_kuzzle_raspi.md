---
title: "Kuzzle Admin Consoleをラズパイ4に入れてみる"
date: "2022-05-17"
tags: ["Kuzzle", "raspberry-pi"]

---

https://github.com/kuzzleio/kuzzle-admin-console#local-build をやってみる

```sh
$ git clone https://github.com/kuzzleio/kuzzle-admin-console
$ cd kuzzle-admin-console
$ npm install
npm ERR! command sh -c node-gyp rebuild
npm ERR! gyp info it worked if it ends with ok
npm ERR! gyp info using node-gyp@3.8.0
npm ERR! gyp info using node@17.3.0 | linux | arm
npm ERR! gyp ERR! configure error 
npm ERR! gyp ERR! stack Error: Command failed: /usr/bin/python -c import sys; print "%s.%s.%s" % sys.version_info[:3];
npm ERR! gyp ERR! stack   File "<string>", line 1
npm ERR! gyp ERR! stack     import sys; print "%s.%s.%s" % sys.version_info[:3];
npm ERR! gyp ERR! stack                       ^
npm ERR! gyp ERR! stack SyntaxError: invalid syntax
```
ダメか。。
