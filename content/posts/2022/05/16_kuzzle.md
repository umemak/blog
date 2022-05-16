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

[What is Kuzzle | Kuzzle Documentation](https://docs.kuzzle.io/core/2/guides/introduction/what-is-kuzzle/#admin-console)

> As it is a single-page application (SPA), no data related to your Kuzzle application will pass through our servers, so you can use the online version available at http://next-console.kuzzle.io.

GitHubにローカルでAdmin Console動かす方法も書いてあった。

https://github.com/kuzzleio/kuzzle-admin-console#local-build
