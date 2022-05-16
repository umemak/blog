---
title: "Kuzzleを使ってみる"
date: "2022-05-16"
tags: ["Kuzzle"]

---

[Flutter | Kuzzle Documentation](https://doc.kuzzle.io/sdk/dart/2/getting-started/flutter/)
から
[Run Kuzzle | Kuzzle Documentation](https://doc.kuzzle.io/core/2/guides/getting-started/run-kuzzle/)
でバックエンドをローカルで起動する。

```sh
$ sudo npm install -g kourou
$ kourou app:scaffold playground
$ cd playground && npm run dev:docker
```
http://localhost:7512/ でJSONで情報が取得できた。

http://next-console.kuzzle.io/ でAdmin Consoleが表示できるけど、ローカル環境なのに外部を一度経由するのかな。ちょっとこれは気になる。
