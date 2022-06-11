---
title: "OracleサーバーのDockerイメージ"
date: "2022-06-11"
tags: ["Docker", "oracle"]

---

[docker-images/OracleDatabase/SingleInstance at main · oracle/docker-images](https://github.com/oracle/docker-images/tree/main/OracleDatabase/SingleInstance)はクライアント側みたいにビルド済みイメージが用意されていないのかな、と思ったらOracle Container Registryにそれらしいものを見つけた。

[Home](https://container-registry.oracle.com/ords/f?p=113:10::::::) > Database > express

```sh
$ docker pull container-registry.oracle.com/database/express:latest
```

サイズやばい
```sh
$ docker images | grep ora
oraclelinux                                      8            3bbe8a2c4b82   9 days ago     226MB
oraclelinux                                      8-slim       1fcc1e6dda05   3 weeks ago    101MB
container-registry.oracle.com/database/express   latest       e986fd612413   2 months ago   11.2GB
```

```sh
$ docker run -d container-registry.oracle.com/database/express

$ docker ps
CONTAINER ID   IMAGE                                            COMMAND                  CREATED          STATUS                             PORTS     NAMES
b9c64bc970d7   container-registry.oracle.com/database/express   "/bin/sh -c 'exec $O…"   56 seconds ago   Up 55 seconds (health: starting)             wizardly_dijkstra

$ docker ps
CONTAINER ID   IMAGE                                            COMMAND                  CREATED              STATUS                        PORTS     NAMES
b9c64bc970d7   container-registry.oracle.com/database/express   "/bin/sh -c 'exec $O…"   About a minute ago   Up About a minute (healthy)             wizardly_dijkstra
```
Statusがhalthyになるまで1分くらいかかった。

```sh
$ docker exec -it b9c64bc970d7 sqlplus / as sysdba

SQL*Plus: Release 21.0.0.0.0 - Production on Sat Jun 11 03:52:08 2022
Version 21.3.0.0.0

Copyright (c) 1982, 2021, Oracle.  All rights reserved.


Connected to:
Oracle Database 21c Express Edition Release 21.0.0.0.0 - Production
Version 21.3.0.0.0

SQL> quit
Disconnected from Oracle Database 21c Express Edition Release 21.0.0.0.0 - Production
Version 21.3.0.0.0
```
OK。

別コンテナから接続してみる。docker-compose.yml用意して起動。
```yaml
version: '3'
services:
  db:
    image: container-registry.oracle.com/database/express
    ports:
      - 1521:1521
    environment:
      - ORACLE_PWD=OraclePwd

  cli:
    image: ghcr.io/oracle/oraclelinux8-instantclient:21
    tty: true
    command: bash
```

クライアント側から接続
```sh
[root@8406cc5e19f2 /]# sqlplus sys/OraclePwd@db:1521 as sysdba

SQL*Plus: Release 21.0.0.0.0 - Production on Sat Jun 11 05:28:50 2022
Version 21.5.0.0.0

Copyright (c) 1982, 2021, Oracle.  All rights reserved.


Connected to:
Oracle Database 21c Express Edition Release 21.0.0.0.0 - Production
Version 21.3.0.0.0

SQL> quit
Disconnected from Oracle Database 21c Express Edition Release 21.0.0.0.0 - Production
Version 21.3.0.0.0
```
OK。

