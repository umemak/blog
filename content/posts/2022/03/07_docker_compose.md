---
title: "docker-compose v1のEOL"
date: "2022-03-07"
tags: ["docker"]

---

Docker Desktopでは設定でcomposeのバージョン（1系と2系）を切り替えることができる。

ところで、いつまでV1が使えるのか気になったので調べてみた。

https://github.com/docker/compose では、デフォルトのブランチがv2となっている。masterブランチに切り替えてREADME.mdを見ると、
> New features and bug fixes will only be considered in the V2 codebase
とあるが、
> but as of right now there is no concrete timeline
ともあるので、機能追加やバグフィクスはv2ベースだけど、v1の廃止については具体的には決まっていないと。

使ってみて致命的な不具合がなければv2を使っておくのが良いのだろうな。

