---
title: "OracleにGoで接続する3"
date: "2022-06-12"
tags: ["Docker", "oracle", "go"]

---

昨日は、[mattn/go-oci8: Oracle driver for Go using database/sql](https://github.com/mattn/go-oci8)と[sijms/go-ora: Pure go oracle client](https://github.com/sijms/go-ora)を使ったサンプルをコンテナ上で`go run`して動かしていた。

今日は`go build`でバイナリにして実行できるようにしてみる。

何もオプション付けずにビルドしたら、どちらも問題なし。

バイナリサイズを小さくしようと、`-ldflags="-s -w -extldflags \"-static\""`をつけたところ、go-oraは大丈夫。go-oci8はNGだった。
```sh
 > [go-oci8:local 9/9] RUN go build -ldflags="-s -w -extldflags "-static"" -o bin/go-oci8 go-oci8/main.go:
#0 0.595 go: downloading github.com/mattn/go-oci8 v0.1.1
#0 2.207 # command-line-arguments
#0 2.207 /usr/local/go/pkg/tool/linux_amd64/link: running gcc failed: exit status 1
#0 2.207 /usr/bin/ld: cannot find -lclntsh
#0 2.207 /usr/bin/ld: cannot find -lpthread
#0 2.207 /usr/bin/ld: cannot find -lc
#0 2.207 collect2: error: ld returned 1 exit status
#0 2.207 
```
`-extldflags \"-static\"`を削除したら通った。

マルチステージビルドにして、ビルドしたバイナリをalpineに載せてみる。

こちらもgo-oraは問題なかったが、go-oci8は実行時にエラー。
```sh
$ docker compose run go-oci8 bin/go-oci8
standard_init_linux.go:228: exec user process caused: no such file or directory
```

Oracleのライブラリなども実行環境に持っていく必要がありそう。

この時点で、コンテナイメージサイズはgo-oraが**13.6MB**に対して、改善の余地があるとはいえgo-oci8は**1.25GB**。

単純に接続してCRUDかける程度なら、go-oraで問題ないと思うけど、Oracleの機能を使い倒そうと思ったら、純正ライブラリを利用しているgo-oci8じゃないとダメな場面が出て来るかもしれない。

今回もDockerfileなどは[こちら](https://github.com/umemak/oracle_test)においてある。
