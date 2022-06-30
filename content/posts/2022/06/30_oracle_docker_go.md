---
title: "OracleにGoで接続するイメージの軽量化"
date: "2022-06-30"
tags: ["Docker", "oracle", "go"]

---

go-oci8を使ったイメージの、oraclelinux8をベースイメージにしたやつが`1.25GB`にもなったので、もっと小さくならないか試してみた。

golang:1-bullseyeをベースにした場合、rpmが使えないのでOracleInstantClient関連のzipを展開する方法でやって、`1.32GB`。増えてる。

golang:1-alpineをベースに、これもzipファイルから展開する方法でやったけれど、go buildが通らず。glibcの何かが原因だと思う。
go build手前までで`781MB`。思ったより小さくならない。

```sh
$ docker images | grep oci8
go-oci8-alpine                                   local        fa45827f44d6   About a minute ago   781MB
go-oci8-bullseye                                 local        3a40111a0898   14 minutes ago       1.32GB
go-oci8                                          local        a8fa2c967223   2 weeks ago          1.25GB
```
