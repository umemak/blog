---
title: "http-serverメモ"
date: "2022-05-02"
tags: ["npm"]

---

ローカルでチョット確認するためのhttpサーバー立てるのに便利な[http-party/http-server: a simple zero-configuration command-line http server](https://github.com/http-party/http-server)。

最近、起動はするもののリクエストを送ると終了してしまう現象が起きていて、ググったらissueがあった。
- [Server Crashing with "Cannot set headers after they are sent to the client" · Issue #634 · http-party/http-server](https://github.com/http-party/http-server/issues/634)

バージョン13.0.2だと大丈夫らしい。

```sh
$ npx http-server@13.0.2
```
大丈夫だった。

