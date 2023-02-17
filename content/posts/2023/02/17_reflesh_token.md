---
title: "リフレッシュトークンについて調べた"
date: "2023-02-17"
tags: []

---

存在意義がわからなかったので、調べてみた。

[リフレッシュ・トークン - IBM Documentation](https://www.ibm.com/docs/ja/api-connect/2018.x?topic=tokens-refresh)

これが一番わかりやすいと思った。

- アクセストークンは頻繁にネットワーク上を流れるから、有効期限を短くする。
- リフレッシュトークンは、アクセストークンが切れた時しかネットワーク上を流れないので、有効期限が長くても良い。
- ワンタイムで破棄するとより安全。

存在理由は腑に落ちたけど、作り方とか持たせる情報がイマイチわからない。

[goLang-jwt-auth-example/myJwt.go at 92d8df8e0a424bd5d02ef3423c126533a98d36d8 · adam-hanna/goLang-jwt-auth-example](https://github.com/adam-hanna/goLang-jwt-auth-example/blob/92d8df8e0a424bd5d02ef3423c126533a98d36d8/server/middleware/myJwt/myJwt.go#L173)

普通にJWT作るときと同じで良さそうだけど、ワンタイムにするためには発行側のDBとかに識別するためのIDを持たせておくとかちょっと面倒そう。
