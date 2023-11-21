---
title: "DockerでNGINXを動かすとClientIPが取れない"
date: "2023-11-21"
tags: ["docker", "nginx"]

---

SvelteKitアプリでアクセス元IPアドレスを見て処理を分けたかった。

ローカル環境では`Handle`で`event.getClientAddress()`したら取れていた。

SvelteKitはログが寂しいので、手前にNGINXを置いてアクセスログを詳細にとれるようにしてみた。

ローカルにNGINXインストールするのはちょっとあれだったので、docker composeで組んだ。

そしたらgetClientAddressで取得されるのは、dockerのゲートウェイアドレスになってしまった。

言われてみればそうかもしれないけど、何とかならないものか。

