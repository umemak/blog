---
title: "ラズパイでDockerでMySQL"
date: "2022-12-10"
tags: ["raspberry-pi", "docker"]

---

GitHub Codespacesが使えるようになるのを待つ間、ラズパイで何とかならないか試してみた。

VS Codeからリモート接続して、Dockerインストールするところまでは順調だったけれど、docker compose upしたところでエラー。

MySQLのコンテナイメージが提供されていないようだ。
意外だった。

[mysql Tags | Docker Hub](https://registry.hub.docker.com/_/mysql/tags)には`linux/arm64/v8`があるけれど、ラズパイは`v7`らしい。

[hypriot/rpi-mysql: RPi-compatible Docker image with Mysql](https://github.com/hypriot/rpi-mysql)も検索で出てきたが古いバージョンでメンテナンスもされていない様子。

forkしてバージョン書き換えてビルドしなおしてみる。

まずはそのまま。
```
 __      ___   ___ _  _ ___ _  _  ___
 \ \    / /_\ | _ \ \| |_ _| \| |/ __|
  \ \/\/ / _ \|   / .` || || .` | (_ |
   \_/\_/_/ \_\_|_\_|\_|___|_|\_|\___|
======================================
resin base images have been deprecated
in favour of the new balenalib images,
read more about it in our docs:
https://www.balena.io/docs/reference/base-images/base-images/
```
使っているベースイメージが古いようだ。

[Balena base images - Balena Documentation](https://www.balena.io/docs/reference/base-images/base-images/)って知らなかったけど、各種用意されていた。
そして何を選んだらよいのかがわからない。

[balenalib/raspberrypi3-debian - Docker Image | Docker Hub](https://hub.docker.com/r/balenalib/raspberrypi3-debian)これかな？

```
W: Skipping acquire of configured file 'ui/binary-armhf/Packages' as repository 'http://archive.raspberrypi.org/debian bullseye InRelease' doesn't have the component 'ui' (component misspelt in sources.list?)
E: Version '5.5*' for 'mysql-server' was not found
```

先は長そう。。
