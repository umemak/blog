---
title: "OracleにGoで接続する2"
date: "2022-06-11"
tags: ["Docker", "oracle", "go"]

---

[mattn/go-oci8: Oracle driver for Go using database/sql](https://github.com/mattn/go-oci8)でやってみる。

```sh
sh-4.4# go run go-oci8/main.go 
# pkg-config --cflags  -- oci8
pkg-config: exec: "pkg-config": executable file not found in $PATH
sh-4.4# yum install -y pkgconfig
sh-4.4# go run go-oci8/main.go 
# pkg-config --cflags  -- oci8
Package oci8 was not found in the pkg-config search path.
Perhaps you should add the directory containing `oci8.pc'
to the PKG_CONFIG_PATH environment variable
Package 'oci8', required by 'virtual:world', not found
pkg-config: exit status 1
```
とりあえずmain.goと同じところにoci8.pcを作成。中身は[Examples](https://github.com/mattn/go-oci8#linux)。
```sh
sh-4.4# export PKG_CONFIG_PATH=.
sh-4.4# go run go-oci8/main.go 
# github.com/mattn/go-oci8
cgo: C compiler "gcc" not found: exec: "gcc": executable file not found in $PATH
sh-4.4# yum install -y gcc
sh-4.4# go run go-oci8/main.go 
# github.com/mattn/go-oci8
In file included from vendor/github.com/mattn/go-oci8/c_helpers.go:3:
./oci8.go.h:1:10: fatal error: oci.h: No such file or directory
 #include <oci.h>
          ^~~~~~~
compilation terminated.
sh-4.4# find / | grep oci.h
/usr/include/oracle/21/client64/oci.h
```
oci8.pcのincludedirを/usr/include/oracle/21/client64に変更。
```sh
sh-4.4# go run go-oci8/main.go 
# github.com/mattn/go-oci8
In file included from vendor/github.com/mattn/go-oci8/c_helpers.go:3:
./oci8.go.h:1:10: fatal error: oci.h: No such file or directory
 #include <oci.h>
          ^~~~~~~
compilation terminated.
```
あれ？

oci8.pcを/usr/share/pkgconfig/にコピーして、環境変数PKG_CONFIG_PATHを/usr/share/pkgconfig/にする。
```sh
sh-4.4# go run go-oci8/main.go 
# command-line-arguments
go-oci8/main.go:18:10: undefined: oci8.TestDisableDatabase
go-oci8/main.go:27:14: undefined: oci8.TestUsername
go-oci8/main.go:28:15: undefined: oci8.TestPassword
go-oci8/main.go:29:22: undefined: oci8.TestUsername
go-oci8/main.go:29:48: undefined: oci8.TestPassword
go-oci8/main.go:31:22: undefined: oci8.TestUsername
go-oci8/main.go:34:21: undefined: oci8.TestHostValid
```
exampleのコードそのままだとダメっぽい。
```go
openString := "system/OraclePwd@db:1521/XE"
```
とTest系の参照せずにべた書きする
```sh
sh-4.4# go run go-oci8/main.go 
1
```
できた！

https://github.com/umemak/oracle_test にまとめた。
