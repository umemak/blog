---
title: "OracleのDockerイメージ"
date: "2022-06-08"
tags: ["Docker", "oracle"]

---

[oracle/docker-images: Official source for Docker configurations, images, and examples of Dockerfiles for Oracle products and projects](https://github.com/oracle/docker-images) にまとめられている。

サーバー側：[docker-images/OracleDatabase at main · oracle/docker-images](https://github.com/oracle/docker-images/tree/main/OracleDatabase)

クライアント側：[docker-images/OracleInstantClient at main · oracle/docker-images](https://github.com/oracle/docker-images/tree/main/OracleInstantClient)

ベースイメージは[Oraclelinux - Official Image | Docker Hub](https://hub.docker.com/_/oraclelinux)が使われている（結構でかい）。

```
$ docker images | grep ora
oraclelinux              8            3bbe8a2c4b82   6 days ago     226MB
oraclelinux              8-slim       1fcc1e6dda05   3 weeks ago    101MB
```
