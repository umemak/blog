---
title: "OracleにGoで接続する"
date: "2022-06-11"
tags: ["Docker", "oracle", "go"]

---

[前の記事](../11_oracle_docker)でsqlplusで接続できたので、Goのプログラムから接続してみる。

instantclientベースでGoをインストールするDockerfile作成
```dockerfile
FROM ghcr.io/oracle/oraclelinux8-instantclient:21

RUN yum install -y wget tar

RUN wget https://go.dev/dl/go1.18.3.linux-amd64.tar.gz

RUN rm -rf /usr/local/go && tar -C /usr/local -xzf go1.18.3.linux-amd64.tar.gz

ENV PATH="${PATH}:/usr/local/go/bin"

CMD [ "go", "version" ]

```

docker-composeもそれを使うように修正
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
    build: .
    image: oraclegocli
    tty: true
    command: bash
```

[sijms/go-oraのサンプル](https://raw.githubusercontent.com/sijms/go-ora/master/examples/hello_sql/main.go)ファイルを拝借。
importの所はv2に修正。

```sh
sh-4.4# vi main.go
sh-4.4# go mod tidy
go: finding module for package github.com/sijms/go-ora/v2
go: downloading github.com/sijms/go-ora/v2 v2.4.24
go: found github.com/sijms/go-ora/v2 in github.com/sijms/go-ora/v2 v2.4.24
sh-4.4# go run main.go  oracle://system:OraclePwd@db:1521/XE

Successfully connected.

```
接続はできているみたいだけど、SQLの実行結果が表示されない。。

ros.Scan(&s)のerrを見たら、カラム数があってない的なエラーだったので、PrerareしてるSQLを`*`から`BANNER`に変更。

```sh
sh-4.4# go run main.go  oracle://system:OraclePwd@db:1521/XE

Successfully connected.

Oracle Database 21c Express Edition Release 21.0.0.0.0 - Production
```
できた。
