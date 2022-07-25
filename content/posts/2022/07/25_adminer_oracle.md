---
title: "AdminerのOracl対応"
date: "2022-07-25"
tags: ["Docker", "Oracle"]

---

[Adminer - Database management in a single PHP file](https://www.adminer.org/)のDockerイメージ[Adminer - Official Image | Docker Hub](https://hub.docker.com/_/adminer/)は、Oracle接続に必要なモジュールが入っていない。

[PHP: インストール/設定 - Manual](https://www.php.net/manual/ja/oci8.setup.php)によると、[Instant Client for Linux x86-64 (64-bit)](https://www.oracle.com/database/technologies/instant-client/linux-x86-64-downloads.html)のBasicと、oci8が必要らしい。

DockerfileはOfficial Imageの[TimWolla/docker-adminer: Database management in a single PHP file](https://github.com/TimWolla/docker-adminer)を参考に。

ってalpineはInstant Client入れるの苦労しそう。。ということでFROMをbullseyeに変更。。したらaddgroupとかadduserのオプションがalpineと違っていてそのままでは通らない。

意外と面倒だな。。
