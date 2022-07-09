---
title: "Goアプリ"
date: "2022-07-09"
tags: ["go", "chi", "mysql"]

---

結局、フレームワークは[go-chi/chi: lightweight, idiomatic and composable router for building Go HTTP services](https://github.com/go-chi/chi/)を使うことにした。

理由は、認証で使いそうなパッケージ[go-pkgz/auth: Authenticator via oauth2, direct, email and telegram](https://github.com/go-pkgz/auth)のサンプルが使っていたから。

とりあえず、HTTPリクエストを受けてDB読み書きしてテンプレート加工して返すところまでできた。
