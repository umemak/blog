---
title: "docker composeで特定コンテナの再起動"
date: "2022-09-01"
tags: ["docker"]

---

`docker compose up -d`で複数コンテナを動かしているときに、その中の特定のコンテナのイメージを更新して再起動したい。
できればその他のコンテナは再起動したくない。

そんなの`docker compose stop hogehoge`して`docker compose start hogehoge`したらいいと思ってた。

ログ的には再起動されるけれども、コンテナイメージは古いままだった。

結局、`docker compose up -d hogehoge`したら期待してた動作になった。
